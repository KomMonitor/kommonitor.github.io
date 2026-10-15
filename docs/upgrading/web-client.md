---
layout: default
title: Web Client
parent: Upgrading
nav_order: 1
---

# Upgrading Guide – Web Client
{: .no_toc }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Migration zum Web Client 5.x.x
Die nachfolgenden Migrationsschritte sind für verschiedene KomMonitor Komponenten notwendig, um einen Wechsel auf
KomMonitor Web Client Version 5 zu vollziehen.


## Processes API

Mit Version 5 von KomMonitor findet ein Wechsel der Prozessierungsumgebung von KomMonitor statt, die 
Verantwortlich für die Ausführung von Indikatoren-Skripten ist. Statt der bisherigen Komponenten “KomMonitor 
Processing Engine” und “KomMonitor Processing Scheduler” bilden nun die “KomMonitor Processes API” auf Basis des 
Python-basierten _pygeoapi_ Frameworks sowie die Open-Source Workflow Engine _Prefect_ die Basis für die neue 
Prozessierungsumgebung.

{: .important }
Eine Übernahme bereits bestehender Indikatoren-Skripte in die neue Prozessierungsumgebung ist nicht möglich. 
Werden KomMonitor Processing Engine und KomMonitor Processing Scheduler weiterhin betrieben, bleiben bestehende
Skripte zunächst noch lauffähig und werden regelmäßig ausgeführt. Ein Zugriff auf die Skripte via Admin UI
ist nicht mehr möglich. Da bei zukünftigen Updates die Funktionsfähigkeit der alten Skripte nicht zugesichert
werden kann, wird dringend empfohlen nach vollzogenem Wechsel auf Web Client Version 5 alle Skripte über die
Admin UI mit verbesserten Konfifurationsmöglichkeiten neu anzulegen.

**1) Docker Einrichtung**

Ein Template zum Betrieb der neuen Komponenten als Docker Container wird unter 
[https://github.com/KomMonitor/docker/tree/master/prod/processing](https://github.com/KomMonitor/docker/tree/master/prod/processing) bereitgestellt.
Das Docker Compose Setup sowie die `.env`\-Datei sind auf die jeweilige Betriebsumgebung anzupassen.

Weitere notwendige Konfigurationsdateien sind gemäß der in den Templates vorgegebenen Ordnerstruktur anzulegen,
müssen jedoch nicht angepasst werden:

* [https://github.com/KomMonitor/docker/blob/master/config/processes-api/default-config.yml](https://github.com/KomMonitor/docker/blob/master/config/processes-api/default-config.yml)
* [https://github.com/KomMonitor/docker/blob/master/config/processes-api.env](https://github.com/KomMonitor/docker/blob/master/config/processes-api.env)

Die nicht mehr benötigten Dienste `kommonitor-processing-engine` und `kommonitor-processing-scheduler` können aus
dem Docker Compose Setup für KomMonitor entfernt werden: [https://github.com/KomMonitor/docker/blob/master/prod/kommonitor/docker-compose.yml](https://github.com/KomMonitor/docker/blob/master/prod/kommonitor/docker-compose.yml) 

**2) Proxy Einrichtung**

Um die neue Processes API über das Internet oder Intranet erreichbar zu machen, sind Proxy Einstellungen zu
ergänzen. Für den internen KomMonitor Proxy liegen folgende Templates bereit:

* [https://github.com/KomMonitor/docker/blob/master/prod/nginx/docker-compose.yml](https://github.com/KomMonitor/docker/blob/master/prod/nginx/docker-compose.yml)
* [https://github.com/KomMonitor/docker/blob/master/prod/nginx/templates/default.conf.template](https://github.com/KomMonitor/docker/blob/master/prod/nginx/templates/default.conf.template)

Soll die Prefect UI ebenfalls über das Internet/Intranet erreichbar sein, sind folgende Templates zu verwenden:

* [https://github.com/KomMonitor/docker/blob/master/prod/nginx/docker-compose.oauth2-proxy.yml](https://github.com/KomMonitor/docker/blob/master/prod/nginx/docker-compose.oauth2-proxy.yml)
* [https://github.com/KomMonitor/docker/blob/master/prod/nginx/templates/oauth2-proxy.conf.template](https://github.com/KomMonitor/docker/blob/master/prod/nginx/templates/oauth2-proxy.conf.template)

In diesem Setup sichert ein OAuth2-Proxy die Prefect UI über Keycloak ab.

## Web Client Konfiguration
Für den Web Client ist in der Admin UI unter _Einstellungen_ -> _Allgemeine Einstellungen_ der Parameter
`window.__env.targetUrlToProcessesApi` zu ergänzen. Für diesen Parameter ist die URL, unter die Processes API im
Internet/Intranet erreichbar sein wird zu setzen.

Alternativ kann dieser Parameter direkt in die Konfigurationsdatei _./kommonitor/storage/config_server/webClientAppConfig.js_
gesetzt werden.Anschließend ist der "kommonitor-client-config" Container neu zu starten.


## Keycloak Konfiguration

Bestehende Keycloak Instanzen müssen über die Admin Console im Browser zur Nutzung durch die neuen
Prozessierungskomponenten angepasst werden.

**1) Processes API Client erstellen**

1. Öffnen des “_Clients_” Bereich
2. Neuen Client über den “_Create Client_” Button erstellen
3. Konfiguration des Clients wie folgt (nicht benannte Felder können freigelassen oder mit den vorausgefüllten 
Standard-Werten belassen werden):
    * General Settings
        * _Client type_: `OpenID Connect`
        * _Client ID_: `kommonitor-processes-api`
        * _Name_: `KomMonitor Processes API`
    * Capability Config
        * _Client authentication_: `On`
        * _Direct access grants_: `enabled`
        * Service account roles: `enabled`
    * Login settings
        
        Login Setting sind abhängig von der Umgebung, in der KomMonitor betrieben wird und der URL unter der
        KomMonitor erreichbar ist. Angenommen die Processes API soll unter
        `https://demo.kommonitor.de/processes-api` erreichbar sein, sind folgende Werte einzutragen:
        
        * _Valid redirect URIs_: `https://demo.kommonitor.de/processes-api/*`
        * _Web origins_: `https://demo.kommonitor.de`
4. Mit Klick auf “Save” kann der Client angelegt werden
5. Über den Tab “Credentials” das “Client Secret” kopieren und sicher abspeichern

**2) Token Exchange Permissions anlegen**

1. Öffnen des “_Clients_” Bereich
2. Auswahl des “kommonitor-data-management” Clients
3. Öffnen des “Permissions” Tab
4. Aktivieren von “Permissions enabled”
5. Aufruf der “token-exchange” Permission aus der “Permission list”
6. Klick in Feld “Policies”, um neue Policy über “Create client policy” zu erstellen
7. Auswahl “Client” als Policy Type
8. Konfiguration der Policy
    * _Name:_ `data-management-token-exchange`
    * _Clients:_ `kommonitor-processes-api`
    * _Logic:_ `Positive`
9. Erneut Aufruf der “token-exchange” Permission für den “kommonitor-data-management” Client
10. Auswahl der `data-management-token-exchange` Policy nach Klick ins Feld “Policies”
11. Klick auf “Save”

**3) Impersonate Permission anlegen**

1. Öffnen des “Users” Bereich
2. Öffnen des “Permissions” Tab
3. Aktivieren von “Permissions enabled”
4. Aufruf der “impersonate” Permission aus der “Permission list”
5. Klick in Feld “Policies”, um neue Policy über “Create client policy” zu erstellen
6. Auswahl “Client” als Policy Type
7. Konfiguration der Policy
    * _Name:_ `kommonitor-processor-impersonator`
    * _Clients:_ `kommonitor-processes-api`
    * _Logic:_ `Positive`
8. Erneut Aufruf der “impersonate” Permission im Bereich “Users”
9. Auswahl der `kommonitor-processor-impersonator` Policy nach Klick ins Feld “Policies”
10. Klick auf “Save”