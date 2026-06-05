---
layout: default
title: Importer
parent: Release Info
nav_order: 2
---

# Release Info (Importer)
{: .no_toc }

Release Informationen für den KomMonitor Importer
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen und Verbesserungen des KomMonitor Importers ab Version 1.0.0. Diese Zusammenfassung konzentriert sich auf Funktionen, die für Anwender*innen und Administrator*innen relevant sind.

---

## Version 4.2.x
### 4.2.1 (5. Mai 2026)
{: .no_toc }
*   **Proxy-Unterstützung:** Einführung einer globalen, optionalen Proxy-Unterstützung mit Authentifizierung. Dies umfasst Anpassungen am REST-Template und HttpHelper für eine konsistente Nutzung im gesamten System. Getestet mit Tinyproxy.
*   **Sicherheit & Zertifikate:** Ein benutzerdefiniertes `entrypoint.sh` Skript behebt Probleme bei der Einbindung zusätzlicher Zertifikate im Docker-Container.
*   **Authentifizierung:** Fix für interne Anfragen an das Data-Management, um Bearer-Token bei getunnelten Anfragen korrekt zu erhalten. Robustere Handhabung fehlender Proxy-Parameter zur Vermeidung von NullPointer-Exceptions.

### 4.2.0 (6. November 2025)
{: .no_toc }
*   **Räumliche Aggregation:** Umfangreiche Erweiterung für den Import auf höhere Raumeinheiten. Unterstützt werden nun Aggregationsfunktionen wie `count` (Anzahl) und weitere mathematische Operationen.
*   **API-Erweiterung:** Einführung neuer Aggregationsparameter in den API-Modellen und Controller-Klassen. Erfolgreich aggregierte Features werden nun detailliert in der API-Antwort und im Monitoring aufgeführt.
*   **Logging:** Der Standard-Log-Level wurde auf `DEBUG` gesetzt, um die Diagnose bei komplexen Importvorgängen zu erleichtern.
*   **Infrastruktur:** Aktualisierung des Basis-Docker-Images und Anpassung des Docker-Test-Setups.

---

## Version 4.1.x
### 4.1.1 (2. September 2025)
{: .no_toc }
*   **Bibliotheken & Geo-Verarbeitung:** Update der GeoTools-Bibliothek inklusive notwendiger Anpassungen bei Paket-Imports. Allgemeine Aktualisierung von Kern-Abhängigkeiten.
*   **Automatisierung:** Regenerierung aller API- und Modellklassen sowie der Client-Klassen zur Sicherstellung der Konsistenz mit dem Gesamtsystem.
*   **Docker:** Optimierung des Docker-Setups für stabilere Deployments.

### 4.1.0 (28. Mai 2025)
{: .no_toc }
*   **API-Synchronität:** Vollständige Regenerierung der Modell- und API-Klassen zur Abstimmung mit den neuesten System-Spezifikationen.

---

## Version 4.0.x
### 4.0.0 (11. Dezember 2024)
{: .no_toc }
*   **Modell-Update:** Umfangreiche Aktualisierung und Synchronisation mit den neuesten API-Modellen und Client-Klassen.
*   **Regionale Referenzwerte:** Fehlerbehebung im API-Modell für den Typ regionaler Referenzwerte (`regionalReferenceValueType`).
*   **Bereinigung:** Entfernung veralteter (deprecated) Eigenschaften in Test-Entitäten für Indikatoren.
*   **Infrastruktur:** Fixierung der Version des Eclipse Temurin Basis-Images für reproduzierbare Builds.

---

## Version 3.2.x
### 3.2.4 & 3.2.5
{: .no_toc }
*   **Features:** Unterstützung für ID-Eigenschaften direkt in Feature-Objekten.
*   **API-Anbindung:** Aktualisierung der unterstützten Versionen der Data Management API.

### 3.2.2 & 3.2.3
{: .no_toc }
*   **Sicherheit:** Unterstützung für die Konfiguration von Cross-Origin Resource Sharing (CORS).
*   **Kodierung:** Einführung von Encoding-Parametern für verschiedene Konverter zur Vermeidung von Darstellungsfehlern.

### 3.2.0 & 3.2.1
{: .no_toc }
*   **OGC-API Features:** Neuer Konverter und Retriever für den OGC-API Features Standard. Unterstützt nun auch benutzerdefinierte Filter und spezifische Proxy-Einstellungen.
*   **Geometrie-Verarbeitung:** Implementierung einer exakten Geometrie-Zuschneidung (Cropping) auf eine Referenzgeometrie sowie verbessertes Handling von CRS-Parametern (Koordinatensysteme).
*   **Performance:** Refactoring des HTTP-Helpers zur Nutzung von Caching-Mechanismen für schnellere Datenabrufe.
*   **Robustheit:** Verbessertes Logging bei leeren Features oder Fehlern beim Parsen von Bounding-Boxen.

---

## Version 3.1.x
### 3.1.1 (November 2023)
{: .no_toc }
*   **Shapefiles:** Automatische Erkennung der Zeichenkodierung (Charset Detection) für Shapefiles.
*   **Retrieval:** Proxy-Unterstützung für HTTP-basierte Datenabrufe.

### 3.1.0 (September 2023)
{: .no_toc }
*   **GeoPackage:** Neuer Konverter zur Unterstützung von GeoPackage-Dateien.

---

## Version 3.0.x
### 3.0.0 (August 2023)
{: .no_toc }
*   **Technik-Update:** Migration des gesamten Projekts auf Spring Boot 3 und Java 17.
*   **Dokumentation:** Umstellung auf Springdoc-OpenAPI für die API-Dokumentation mit Swagger 3 Annotationen.
*   **Sicherheit:** Implementierung von OAuth2-Unterstützung via Spring Security.
*   **Test-Infrastruktur:** Erweiterung des Docker-Compose Setups um die Data-Management-API für automatisierte Integrationstests.

---

## Version 2.0.x
### 2.0.6 & 2.0.7
{: .no_toc }
*   **Wartung:** Migration auf JDK 17 und Einführung automatisierter Sicherheits-Scans (CVE).

### 2.0.3 - 2.0.5
{: .no_toc }
*   **Datenformate:** Optimiertes Parsen von Excel- und CSV-Dateien (z. B. Umgang mit leeren Headern).
*   **Einstieg:** Bereitstellung eines Docker-Compose Setups für einen schnellen Start.

### 2.0.0 - 2.0.2
{: .no_toc }
*   **Geokodierung:** Einführung der Adress-zu-Punkt Geokodierung für CSV- und Excel-Dateien sowie Unterstützung für Batch-Abfragen.
*   **Shapefiles:** Neuer Konverter für Shapefiles in ZIP-Ordnern.

---

## Version 1.2.x
### 1.2.1 & 1.2.2
{: .no_toc }
*   **Sicherheit:** Patches zur Behebung der Log4j-Sicherheitslücken.

### 1.2.0 (September 2021)
{: .no_toc }
*   **Aktualisierungen:** Unterstützung für Teil-Aktualisierungen (Partial Updates) von Raumeinheiten und Georessourcen.

---

## Version 1.0.0 (Mai 2021)
{: .no_toc }
*   **Initial-Release:** Bereitstellung der Kernfunktionalitäten, einschließlich WFS- und HTTP-Retrievern sowie Konvertern für GeoJSON und WFS.
