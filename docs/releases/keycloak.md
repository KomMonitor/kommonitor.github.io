---
layout: default
title: Keycloak
parent: Release Info
nav_order: 9
date: 2026-08-31
description: Release-Informationen für die KomMonitor Keycloak-Erweiterungen
---

# Release Info (Keycloak)
{: .no_toc }

Release Informationen für die KomMonitor Keycloak-Erweiterungen.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen, Fehlerbehebungen und technischen Optimierungen der KomMonitor Keycloak-Erweiterungen ab Version 25.0.6. Die Versionsnummern orientieren sich an der jeweils eingesetzten Keycloak-Basisversion (z. B. 26.x entspricht Keycloak 26).

---

## Version 26.7.x
{: .important }
Bei einem Update auf eine Keycloak Version 26.7.x sind folgene Upgrading Hinweise zu beachten:
[Migration zu Keycloak 26.7.x](../upgrading/keycloak.md#migration-zu-keycloak-267x)

### 26.7.2 (31.08.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Keycloak-Version:
{: .no_toc }
Aktualisierung der eingesetzten Keycloak-Version auf den aktuellen Hotfix-Stand.

---

### 26.7.0 (16.07.2026)
{: .no_toc }


#### Neue Features
{: .no_toc }

##### Sicherheitsdokumentation:
{: .no_toc }
Eine SECURITY.md-Datei mit Hinweisen zur Meldung von Sicherheitslücken wurde zum Repository hinzugefügt.

##### Automatische Abhängigkeitsaktualisierungen:
{: .no_toc }
Dependabot wurde konfiguriert, um Abhängigkeiten automatisch auf dem neuesten Stand zu halten.

#### Änderungen
{: .no_toc }

##### Keycloak-Version:
{: .no_toc }
Aktualisierung der eingesetzten Keycloak-Version auf die aktuelle Minor-Version 26.7.

---

## Version 26.6.x

### 26.6.4 (16.07.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Build-Prozess:
{: .no_toc }
Der Build-Workflow wurde angepasst, um SNAPSHOT-Builds zu unterstützen. Zudem wurde die eingesetzte Keycloak-Hotfix-Version aktualisiert.

---

### 26.6.3 (13.07.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Sicherheit & CI-Pipeline:
{: .no_toc }
Das Docker-Image wurde gehärtet und die CI-Pipeline um automatisierte Sicherheits-Scans sowie Image-Signierung erweitert. Die Pipeline bricht künftig ab, wenn kritische Schwachstellen (CRITICAL) erkannt werden, sodass keine verwundbaren Images ausgeliefert werden. Nicht mehr benötigte Dummy-Zertifikate wurden entfernt und die eingesetzte Keycloak-Version aktualisiert.

---

## Version 26.5.x

### 26.5.5 - 26.5.7 (17.04.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Keycloak-Aktualisierung:
{: .no_toc }
Aktualisierung der eingesetzten Keycloak-Version auf aktuelle Minor- und Hotfix-Releases.

---

## Version 26.4.x

### 26.4.7 (13.01.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Keycloak-Aktualisierung:
{: .no_toc }
Aktualisierung der eingesetzten Keycloak-Minor-Version.

---

## Version 26.3.x

### 26.3.1 - 26.3.4 (18.09.2025)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Keycloak-Aktualisierung:
{: .no_toc }
Aktualisierung der eingesetzten Keycloak-Version auf aktuelle Minor- und Hotfix-Releases.

---

## Version 26.2.x

### 26.2.0 - 26.2.5 (11.07.2025)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Keycloak-Aktualisierung:
{: .no_toc }
Aktualisierung der eingesetzten Keycloak-Version auf aktuelle Minor- und Hotfix-Releases.

---

## Version 26.1.x

### 26.1.0 - 26.1.3 (27.05.2025)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Keycloak-Aktualisierung:
{: .no_toc }
Aktualisierung der eingesetzten Keycloak-Version auf aktuelle Minor- und Hotfix-Releases. Die verwendete Cache-Action in der CI-Pipeline wurde ebenfalls aktualisiert.

---

## Version 26.0.x

### 26.0.8 (14.01.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Hostname-Konfiguration:
{: .no_toc }
Unterstützung für das `hostname:v1`-Feature von Keycloak wurde hinzugefügt, das eine flexiblere Konfiguration von Keycloak-Hostnamen ermöglicht.

##### Realm-abhängige Rollenrichtlinien:
{: .no_toc }
Es wurde Unterstützung für realm-abhängige Rollenrichtlinien-Auswertung implementiert. Damit können rollenbasierte Zugriffsregeln für mehrere Realms separat konfiguriert und ausgewertet werden.

##### Token Exchange:
{: .no_toc }
Das Token-Exchange-Feature wurde aktiviert. Damit können Dienste und Clients Token gegeneinander austauschen, was eine sichere Service-zu-Service-Kommunikation vereinfacht.

#### Fehlerbehebungen
{: .no_toc }

##### Build & Integration:
{: .no_toc }
Fehler bei der Integration von Extension-Artefakten sowie bei der Einbindung benutzerdefinierter Provider im Docker-Build wurden behoben.

#### Änderungen
{: .no_toc }

##### Infrastruktur:
{: .no_toc }
Die Keycloak-Image-Version wurde auf eine feste Version gepinnt. Ein nicht mehr unterstütztes Keycloak-Feature wurde entfernt und die Keycloak-Version aktualisiert.

---

## Version 25.0.x

### 25.0.6 (26.11.2024)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initialer Release:
{: .no_toc }
Erstveröffentlichung der KomMonitor Keycloak-Erweiterungen als Docker-Image mit KomMonitor-spezifischen Anpassungen. Die initiale Version enthält ein Dockerfile sowie GitHub-Workflows für den automatisierten Build und die Bereitstellung des Images.

---
