---
layout: default
title: Importer
parent: Release Info
nav_order: 2
---

# Release Info (Importer)
{: .no_toc }

Release Informationen für die Importer API zum Import von Geodaten und Statistiken in das KomMonitor-System.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine detaillierte Übersicht der wichtigsten Neuerungen, Fehlerbehebungen und technischen Optimierungen der KomMonitor Importer API ab Version 1.0.0.

---

## Version 4.2.x
### 4.2.1 (05.05.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
##### Zertifikats-Management:
{: .no_toc }
Die Einbindung von Sicherheitszertifikaten im Startprozess wurde korrigiert, um eine reibungslose Kommunikation in verschlüsselten Umgebungen zu gewährleisten.

##### Sicherheits-Token:
{: .no_toc }
Die Handhabung von Security-Token für interne Anfragen wurde optimiert, sodass die Autorisierung mittels Bearer-Token nun zuverlässig erfolgt.

#### Änderungen
{: .no_toc }
##### Proxy-Verbesserungen:
{: .no_toc }
Die Unterstützung für Netzwerk-Proxys wurde erweitert und verbessert, einschließlich der Unterstützung für Authentifizierung und Tinyproxy.

### 4.2.0 (06.11.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Automatische Daten-Aggregation:
{: .no_toc }
Statistische Daten können nun während des Imports automatisch für übergeordnete Raumeinheiten berechnet werden (z.B. Summe oder Anzahl), was die manuelle Vorverarbeitung reduziert.

#### Änderungen
{: .no_toc }
##### API-Refactoring:
{: .no_toc }
Die internen Programmschnittstellen wurden grundlegend überarbeitet, um die Wartbarkeit und Performance des Systems zu steigern.

---

## Version 4.1.x
### 4.1.1 (02.09.2025)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### Systemwartung:
{: .no_toc }
Wichtige Abhängigkeiten wurden aktualisiert und allgemeine Wartungsarbeiten durchgeführt, um die langfristige Stabilität zu sichern.

### 4.1.0 (28.05.2025)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### Schnittstellen-Synchronisation:
{: .no_toc }
Die internen Schnittstellen wurden mit den aktuellen System-Spezifikationen abgeglichen, um eine optimale Kompatibilität innerhalb des KomMonitor-Ökosystems zu garantieren.

---

## Version 4.0.x
### 4.0.0 (11.12.2024)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Systemstabilität:
{: .no_toc }
Die verwendete Laufzeitumgebung wurde auf eine feste Version fixiert, um eine gleichbleibende Zuverlässigkeit über verschiedene Installationen hinweg sicherzustellen.

#### Fehlerbehebungen
{: .no_toc }
##### Regionale Referenzwerte:
{: .no_toc }
Ein Fehler im Datenmodell für regionale Vergleichswerte wurde behoben, wodurch diese nun wieder korrekt verarbeitet werden können.

---

## Version 3.2.x
### 3.2.5 (18.12.2024)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
##### Kompilierung:
{: .no_toc }
Interne Fehler im Erstellungsprozess der Software wurden behoben.

### 3.2.4 (03.04.2024)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Objekt-Identifikation:
{: .no_toc }
Unterstützung für die Identifizierung von Merkmalen über eine explizite ID-Eigenschaft wurde hinzugefügt, was die Eindeutigkeit beim Datenimport erhöht.

### 3.2.3 (30.01.2024)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### OpenAPI-Spezifikation:
{: .no_toc }
Die Schnittstellenbeschreibung wurde an den neuesten Standard angepasst, um die Interoperabilität zu verbessern.

### 3.2.2 (28.11.2023)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Kodierungs-Optionen:
{: .no_toc }
Neue Einstellungen für die Zeichenkodierung ermöglichen den problemlosen Import von Dateien aus unterschiedlichen Quellen und Systemen.

##### CORS-Unterstützung:
{: .no_toc }
Die Unterstützung für Cross-Origin Resource Sharing wurde ergänzt, um den sicheren Zugriff durch moderne Web-Browser zu optimieren.

### 3.2.1 (20.11.2023)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
##### Proxy-Konfiguration:
{: .no_toc }
Ein Fehler in den Einstellungen für den Netzwerk-Proxy wurde korrigiert.

### 3.2.0 (15.11.2023)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Räumliches Zuschneiden:
{: .no_toc }
Importierte Daten können nun automatisch auf eine definierte Referenz-Geometrie zugeschnitten werden.

##### OGC API Features:
{: .no_toc }
Ein neuer Konverter zur Unterstützung des modernen OGC API Features Standards wurde implementiert.

---

## Version 3.1.x
### 3.1.1 (07.11.2023)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Automatische Kodierungserkennung:
{: .no_toc }
Die Erkennung der Text-Kodierung für Shapefiles und GeoJSON-Dateien wurde verbessert, um die korrekte Darstellung von Sonderzeichen sicherzustellen.

### 3.1.0 (19.09.2023)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### GeoPackage-Layer:
{: .no_toc }
Beim Import von GeoPackage-Dateien ist es nun möglich, gezielt einzelne Daten-Layer für den Import auszuwählen.

---

## Version 3.0.x
### 3.0.0 (18.08.2023)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### Technologische Modernisierung:
{: .no_toc }
Vollständige Migration auf Spring Boot 3 und Java 17 für verbesserte Sicherheit und eine modernere Systembasis.

---

## Version 2.0.x
### 2.0.7 (02.08.2023)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### Image-Optimierung:
{: .no_toc }
Das Java-Laufzeit-Image wurde optimiert, um den Ressourcenverbrauch zu senken und die Startzeit zu verkürzen.

### 2.0.4 (29.03.2023)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Geocoding-Proxy:
{: .no_toc }
Unterstützung für Netzwerk-Proxys bei Geokodierungs-Anfragen wurde hinzugefügt.

### 2.0.1 (07.11.2022)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Adress-Details:
{: .no_toc }
Zusätzliche Adressinformationen bei der Geokodierung verbessern die Genauigkeit der räumlichen Zuordnung.

### 2.0.0 (24.07.2022)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Tabellen-Geokodierung:
{: .no_toc }
Einführung von Werkzeugen zur Umwandlung tabellarischer Adressdaten in Punkt-Geometrien (sowohl Einzel- als auch Batch-Verarbeitung).

##### Excel-Unterstützung:
{: .no_toc }
Daten können nun direkt aus Excel-Dateien importiert werden.

---

## Version 1.2.x
### 1.2.1 (17.12.2021)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
##### Sicherheits-Update:
{: .no_toc }
Kritische Sicherheitsaktualisierung der Log4j-Bibliothek zur Schließung bekannter Sicherheitslücken.

### 1.2.0 (07.09.2021)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Partielle Updates:
{: .no_toc }
Unterstützung für die teilweise Aktualisierung bestehender Ressourcen, ohne den gesamten Datensatz überschreiben zu müssen.

---

## Version 1.0.x
### 1.0.0 (12.05.2021)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Initial-Release:
{: .no_toc }
Erste Veröffentlichung der Kern-Importer-Logik mit Unterstützung für WFS-Schnittstellen und automatischer Transformation in das WGS 84 Koordinatensystem.
