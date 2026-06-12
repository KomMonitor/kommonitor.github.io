---
layout: default
title: Spatial Data Processor
parent: Release Info
nav_order: 5
---

# Release Info (Spatial Data Processor)
{: .no_toc }

Release Informationen für den KomMonitor Spatial Data Processor.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen, Fehlerbehebungen und technischen Optimierungen des Spatial Data Processors ab Version 1.0.0.

---

## Version 1.1.x

### 1.1.0 (März 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Geometrie-Validierung: 
{: .no_toc }
Implementierung einer Prüfung auf topologische Gültigkeit von Geometrien. Ungültige Geometrien werden nun automatisch mittels eines `buffer(0)`-Verfahrens repariert.

#### Änderungen
{: .no_toc }

##### Infrastruktur: 
{: .no_toc }
Aktualisierung der Versionen für Cache-Actions und Trivy-Security-Scans.

---
## Version 1.0.x

### 1.0.1 - 1.0.4 (Juni - September 2024)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Datenabruf: 
{: .no_toc }
Optimierung des Abrufs von Raumeinheiten und Indikatoren-Zeitreihen durch vereinfachte Geometrien (`simplification=medium`), um Topologieprobleme bei Verschneidungen zu umgehen.

##### Geometrie-Handling: 
{: .no_toc }
Einführung eines konfigurierbaren Parameters zur Geometrie-Vereinfachung (`simplifyGeometries`).

#### Fehlerbehebungen
{: .no_toc }

##### Datenzugriff: 
{: .no_toc }
Korrektur beim Abruf öffentlicher Raumeinheiten und Indikatoren-Zeitreihen (Accept-Header und URLs).

##### Berechnungslogik: 
{: .no_toc }
Behebung von Fehlern bei fehlenden Indikatorenwerten für einzelne Raumeinheiten-Features sowie Korrekturen beim Casting von Geometrie-Typen.

#### Änderungen
{: .no_toc }

##### Sicherheit: 
{: .no_toc }
Anpassungen an der CORS-Konfiguration und Aktualisierung des Docker-Basis-Images (Eclipse Temurin).

### 1.0.0 (Juni 2024)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initialer Release: 
{: .no_toc }
Bereitstellung des spezialisierten Dienstes für komplexe räumliche Analysen.

##### Job-Queue System: 
{: .no_toc }
Implementierung eines Systems zur Verwaltung und Abarbeitung von Rechenaufträgen in einer Warteschlange, inklusive automatischer Bereinigung.

##### Isochronen-Analyse (Pruning): 
{: .no_toc }
Spezialisierter Algorithmus zur "Bereinigung" von Isochronen und zur Berechnung der Indikatoren-Abdeckung pro Isochrone.

##### Räumliche Verschneidung: 
{: .no_toc }
Implementierung verschiedener Verschneidungsmethoden:
- Berechnung von Überschneidungsanteilen (Intersection Proportion).
- Wohnflächengewichtete Verschneidung (Residential Area Weighted Intersection).
- Filterung und Subselektion von sich überschneidenden Features.

##### Schnittstellen & Integration: 
{: .no_toc }
- Basis-Client zur Kommunikation mit der KomMonitor Daten-Management API.
- Integration von Keycloak zur Authentifizierung und Unterstützung öffentlicher Anfragen.
- Bereitstellung einer Swagger-UI zur interaktiven API-Dokumentation.

##### Infrastruktur: 
{: .no_toc }
Bereitstellung eines Docker-Setups und GitHub Actions für CI/CD und Docker-Builds.
