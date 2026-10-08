---
layout: default
title: Data Management
parent: Release Info
nav_order: 3
date: 2026-06-17
description: Release-Informationen für die KomMonitor Data Management API
---

# Release Info (Data Management)
{: .no_toc }

Release Informationen für die zentrale Datenverwaltung des KomMonitor-Systems.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine detaillierte Übersicht der wichtigsten Neuerungen, Fehlerbehebungen und technischen Optimierungen der KomMonitor Data Management API ab Version 1.0.0.

---

## Version 5.2.x

### 5.2.6 (17.06.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Proxy-Konfiguration:
{: .no_toc }
Erweiterung des Proxy-Supports um einen globalen Proxy-Selector, der Proxy-Routing tief in der Java-Netzwerkschicht erzwingt. Zudem wurde ein Fehler bei der Proxy-Einbindung im REST-Client für die Keycloak-Admin-Kommunikation behoben.

### 5.2.5 (15.06.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Proxy-Konfiguration:
{: .no_toc }
Behebung eines Fehlers bei der Proxy-Einbindung im REST-Client für die Keycloak-Kommunikation bei der Verwaltung von Benutzergruppen.

### 5.2.4 (08.06.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Proxy-Konfiguration:
{: .no_toc }
Verfeinerung der Proxy-Implementierung: Hinzufügen einer Proxy-Konfigurations-Bean für den RestEasy-Client, der für Keycloak-Admin-CLI-Anfragen benötigt wird.

### 5.2.3 (01.06.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Web Service Favoriten Management:
{: .no_toc }
Einführung eines Managementsystems zur Verwaltung von Web Service Favoriten für verbesserte Benutzerfreundlichkeit.

### 5.2.2 (21.05.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Qualitative Klassifizierung:
{: .no_toc }
Erweiterte Unterstützung für die qualitative Klassifizierung von Datenbeständen.

#### Änderungen
{: .no_toc }

##### Refactoring Default Classification:
{: .no_toc }
Umfassendes Refactoring der Standard-Klassifizierungslogik zur Steigerung der Wartbarkeit.

### 5.2.0 (20.04.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Docker-Compose:
{: .no_toc }
Bereitstellung optimierter Docker-Compose Konfigurationen für eine vereinfachte Deployment-Orchestrierung.

##### OpenAPI UI:
{: .no_toc }
Integration der interaktiven OpenAPI Benutzeroberfläche zur direkten API-Dokumentation und Erprobung.

---

## Version 5.1.x

### 5.1.5 (21.01.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Themen-Sortierung (Display Order):
{: .no_toc }
Implementierung einer flexiblen Sortierlogik zur Definition der Anzeige-Reihenfolge von Themenbereichen.

##### Web Service Filterung:
{: .no_toc }
Einführung erweiterter Filterkriterien für Web Service Endpunkte.

##### GeoPackage Export:
{: .no_toc }
Unterstützung des GeoPackage-Formats für den Export von Geodaten.

### 5.1.0 (20.08.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### RBAC Updates:
{: .no_toc }
Aktualisierungen und Erweiterungen am rollenbasierten Zugriffskontrollsystem (RBAC) für feinere Berechtigungsstrukturen.

##### GZIP Compression:
{: .no_toc }
Aktivierung der GZIP-Komprimierung zur Reduzierung der Payload-Größen und Optimierung der Antwortzeiten.

##### Öffentliche Themen Endpoints:
{: .no_toc }
Bereitstellung dedizierter Endpunkte für den unbeschränkten Zugriff auf öffentliche Themenressourcen.

---

## Version 5.0.x

### 5.0.0 (10.03.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Major Update:
{: .no_toc }
Grundlegende Überarbeitung der Systemarchitektur und Einführung zentraler Kernfunktionen.

---

## Version 4.1.x

### 4.1.0
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Maintenance:
{: .no_toc }
Durchführung allgemeiner Wartungsarbeiten und kleinerer Code-Optimierungen.

---

## Version 4.0.x

### 4.0.0
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Security:
{: .no_toc }
Implementierung kritischer Sicherheitsaktualisierungen und Härtung der API-Infrastruktur.

---

## Version 3.4.x

### 3.4.0
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Display Order:
{: .no_toc }
Einführung der Anzeige-Reihenfolge zur besseren Strukturierung von Ressourcenlisten.

---

## Version 3.3.x

### 3.3.0
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Maintenance:
{: .no_toc }
Kontinuierliche Wartung und Pflege der Codebasis.

---

## Version 3.2.x

### 3.2.0
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Maintenance:
{: .no_toc }
Stabilitätsverbesserungen und interne Refactorings.

---

## Version 3.1.x

### 3.1.0
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Maintenance:
{: .no_toc }
Reguläre Wartung zur Sicherstellung der Betriebsstabilität.

---

## Version 3.0.x

### 3.0.0
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Spring Boot 3:
{: .no_toc }
Vollständige Migration auf Spring Boot Version 3 inklusive Aktualisierung abhängiger Frameworks.

---

## Version 2.1.x

### 2.1.0
{: .no_toc }

#### Neue Features
{: .no_toc }

##### RBAC Grid:
{: .no_toc }
Erweiterung des Berechtigungsmanagements um eine tabellarische Gitteransicht zur effizienten Rollenzuweisung.

##### Encryption:
{: .no_toc }
Implementierung von Verschlüsselungsmethoden zur Erhöhung der Datensicherheit auf Transport- und Speicherebene.

---

## Version 2.0.x

### 2.0.0
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Organizations:
{: .no_toc }
Einführung der Mandantenfähigkeit durch Unterstützung von Organisationseinheiten.

##### Keycloak:
{: .no_toc }
Integration von Keycloak als zentraler Provider für Identitätsmanagement und Authentifizierung.

---

## Version 1.2.x

### 1.2.0
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initial:
{: .no_toc }
Fortführung der initialen Bereitstellungsphase mit erweiterten Basisfunktionen.

---

## Version 1.1.x

### 1.1.0
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initial:
{: .no_toc }
Ergänzungen der initialen Systemkomponenten der Data Management API.

---

## Version 1.0.x

### 1.0.0
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initial:
{: .no_toc }
Initiale Veröffentlichung der KomMonitor Data Management API zur zentralen Datenverwaltung.
