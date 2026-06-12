---
layout: default
title: Client Config API
parent: Release Info
nav_order: 8
---

# Release Info (Client Config API)
{: .no_toc }

Release Informationen für die KomMonitor Client Config API.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen, Fehlerbehebungen und technischen Optimierungen der Client Config API ab Version 1.0.0.

---

## Version 2.x.x

### 2.3.0-SNAPSHOT (Mai 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Dashboards Konfiguration: 
{: .no_toc }
Es wurden neue Endpunkte für die Konfiguration von Dashboards hinzugefügt. Hierzu wurde auch die OpenAPI-Spezifikation entsprechend aktualisiert. Dashboard-Konfigurationen werden als separate JSON-Dateien, die per ID identifiziert werde, abgespeichert.

#### Änderungen
{: .no_toc }

##### Dashboard-Erstellung: 
{: .no_toc }
Das Antwortverhalten bei der Erstellung von Dashboards wurde angepasst.

##### Infrastruktur: 
{: .no_toc }
Die Docker-Compose Konfiguration für Keycloak wurde aktualisiert.

---

### 2.2.1 (Mai 2026)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### Verwaltung von Filtern: 
{: .no_toc }
Für Endpunkte zur Verwaltung von globalen Filtern kann festgelegt werden, welche Rollenberechtigungen hierzu notwendig sind. Standardmäßig können nun User mit einer `*.unit-resources-creator` oder `.client-resources-creator` Rolle Filterkonfigurationen verwalten.

##### Abhängigkeiten: 
{: .no_toc }
Die `keycloak-helper` Abhängigkeit wurde aktualisiert.

---

### 2.2.0 & 2.2.0-beta.1 (September - November 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Startseite: 
{: .no_toc }
Die Funktionalität zum Speichern und Abrufen der Startseite wurde implementiert.

#### Änderungen
{: .no_toc }

##### Abhängigkeiten: 
{: .no_toc }
Verschiedene Abhängigkeiten und die Dokumentation (README) wurden aktualisiert.

---

### 2.1.0 (Oktober 2024)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Filterkonfiguration: 
{: .no_toc }
Ein neuer Endpunkt für die Konfiguration von Web-App Filtern wurde hinzugefügt.

#### Änderungen
{: .no_toc }

##### Technik: 
{: .no_toc }
Migration auf die neueste Version der `oas-tools` Bibliothek.

##### Entwicklung: 
{: .no_toc }
Ein Docker-Setup für Entwicklungszwecke wurde hinzugefügt.

---

### 2.0.0 - 2.0.4 (Juli 2022 - Juli 2023)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Sicherheit: 
{: .no_toc }
Implementierung des Keycloak-Schutzes für POST-Anfragen auf geschützte Ressourcen. Diese können nun nur noch von KomMonitor-Administratoren aufgerufen werden.

##### Technik-Upgrade: 
{: .no_toc }
Upgrade auf OpenAPI v3 Router und Nutzung von YAML-Ressourcen.

#### Änderungen
{: .no_toc }

##### Docker & Umgebung: 
{: .no_toc }
Das `gettext` Paket wurde zum Docker-Image hinzugefügt, um `envsubst` Befehle zu unterstützen.

##### Konfiguration: 
{: .no_toc }
Standardeinstellungen in der App-Konfiguration wurden angepasst und `.env` Kommentare korrigiert.

---

## Version 1.x.x

### 1.3.0 (September 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Info-Modal: 
{: .no_toc }
Eigenschaften für das erweiterte Info-Modal wurden hinzugefügt.

#### Änderungen
{: .no_toc }

##### Einstellungen: 
{: .no_toc }
Die Einstellung `useNoDataToggle` wurde standardmäßig auf `false` gesetzt.

---

### 1.2.0 (Juni 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Benachrichtigungen: 
{: .no_toc }
In der Konfigurationsdatei wird nun die Bearbeitung von Benachrichtigungen für Raumeinheiten unterstützt.

---

### 1.0.0 - 1.1.1 (Mai 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initialer Release: 
{: .no_toc }
Bereitstellung eines Express-Servers zur zentralen Verwaltung von Client-Konfigurationen inklusive Standarddateien für verschiedene Konfigurationstypen.

#### Änderungen
{: .no_toc }

##### Release-Prozess: 
{: .no_toc }
Wechsel des Release-Tools zu `release-it` für automatisierte Changelog-Aktualisierungen.
