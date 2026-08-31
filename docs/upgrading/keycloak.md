---
layout: default
title: Keycloak
parent: Upgrading
nav_order: 2
---

# Upgrading Guide – Keycloak
{: .no_toc }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Migration zu Keycloak 26.7.x
Ab Version 26.7.0 von Keycloak erfolgt beim Aufruf des OAuth2 Token Introspection Endpunkts eine
Validierung des Token Audiences Claims ([https://www.keycloak.org/docs/26.7.0/upgrading/#token-introspection-now-validates-audience-claim](https://www.keycloak.org/docs/26.7.0/upgrading/#token-introspection-now-validates-audience-claim)).

Diese Änderung des Verhaltens führt zu Problemen bei der Kommunikation des Web Clients mit der Client 
Config API und der Processes API. Beide Komponenten rufen den Token Introspection Endpunkt mit dem 
Token, der für den Web Client ausgestellt wurde, auf, wodurch ein *INTROSPECT_TOKEN_ERROR* auftritt. 

Nach einem Update auf eine Keycloak Version > 26.7.0 müssen daher folgende Anpassungen an der Keycloak Konfiguration über die Keycloak Administration Console vorgenommen werden:

**1) Audience Client Scope erstellen**
1. Öffnen des *"Client scopes"* Bereichs
2. Neuen Client Scope über den *"Create client scope"* Button erstellen
3. Konfiguration des Client Scopes wie folgt:
    * *Name*: `audience-scope`
    * *Type*: `Default`
    * Für alle anderen Felder können die voreingestellten Werte übernommen werden

**2) Client Config Mapper hinzufügen**
1. Wechsel zum Tab *"Mappers"* des soeben erstellten *"audience-scope"*
2. Neuen Mapper über *"Configure a new mapper"* erstellen
3. Auswahl von *"Audience"*
4. Mapper Konfiguration:
    * *Name*: `client-config-audience-mapper`
    * *Included Client Audience*: `kommonitor-client-config`
    * Für alle anderen Felder können die voreingestellten Werte übernommen werden

**3) Processes API Mapper hinzufügen**
1. Weiterhin im Tab *"Mappers"* des soeben erstellten *"audience-scope"*
2. Neuen Mapper über *"Add mapper" -> "By configuration"* erstellen
3. Auswahl von *"Audience"*
4. Mapper Konfiguration:
    * *Name*: `processes-api-audience-mapper`
    * *Included Client Audience*: `kommonitor-processes-api`
    * Für alle anderen Felder können die voreingestellten Werte übernommen werden

**4) Audience Client Scope für Web Client hinterlegen**
1. Öffnen des Clients *"Web Client" über "Clients" -> "kommonitor-web-client"*
2. Öffnen des Tabs *"Client scopes"*
3. Neuen Scope über *"Add client scope"* hinzufügen
4. Auswahl des soeben erstellen *"audience-scope"*
5. Hinzufügen über *"Add" -> "Default"*

Ob die Konfigurationsänderungen erfolgreich waren, kann geprüft werden, indem in der KomMonitor Admin
UI unter *"Einstellungen" -> "Allgemeine Einstellungen"* der Button *"App-Konfiguration speichern"*
angeklickt wird. Sollte diese Aktion fehlschlagen, muss die Konfiguration in Keycloak noch einmal
überprüft werden.