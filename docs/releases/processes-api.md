---
layout: default
title: Processes API
parent: Release Info
nav_order: 4
---

# Release Info (Processes API)
{: .no_toc }

Release Informationen für die KomMonitor Processes API.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen, Fehlerbehebungen und technischen Optimierungen der Processes API ab Version 1.0.0.

---

## Version 1.1.x

### 1.1.0 - 1.1.1 (Mai 2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Indikatoren-Berechnung: 
{: .no_toc }
Korrektur eines Fehlers, der bei einer Reihe identischer Eingabe-Indikatoren von Skripnte auftrat.

##### Leitindikatoren-Skript: 
{: .no_toc }
Fehlerbehebungen im Leitindikator-Skript bei der Berücksichtigung von Gültigkeitszeiträumen von Raumeinheiten-Features.

#### Änderungen
{: .no_toc }

##### Technik: 
{: .no_toc }
Aktualisierung der Version und interne Code-Verbesserungen.

---

## Version 1.0.x

### 1.0.1 (März 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Export-Funktionen: 
{: .no_toc }
Implementierung neuer Export-Skripte (Einzel-Export, Raumeinheiten-Export, Multi-Export) und Unterstützung für Datei-Downloads.

##### Filter & Abfragen: 
{: .no_toc }
Hinzufügen eines Zeitspannen-Filters für Georessourcen.

##### Öffentliche Exporte: 
{: .no_toc }
Erweiterte Unterstützung für öffentliche Export-Anfragen.

##### System-Optimierung: 
{: .no_toc }
Automatisierte Job-Bereinigung (Job Cleaning) und dynamische Ermittlung der API-URL für Antworten.

#### Fehlerbehebungen
{: .no_toc }

##### Legenden: 
{: .no_toc }
Korrekturen an dynamischen Legenden für verschiedene Skripte (z.B. Prozentanteil).

##### Daten-Handling: 
{: .no_toc }
Behandlung von leeren Zeitreihen und ungültigen Referenzdaten korrigiert.

#### Änderungen
{: .no_toc }

##### Authentifizierung: 
{: .no_toc }
Verfeinerung der Berechtigungsprüfung bei der Prozess-Ausführung und beim Download von Ergebnissen.


### 1.0.0 (Januar 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initialer Release: 
{: .no_toc }
Bereitstellung der OGC-konformen Schnittstelle zur Prozess-Orchestrierung.

##### Indikatoren-Skripte: 
{: .no_toc }
Die Processes API bietet eine Vielzahl an standardisierten Skripten zur Berechnung von Indikatoren und Statistiken. Im Folgenden sind die verfügbaren Skripte mit ihrem vollen Titel aufgeführt:

- Anzahl Punktobjekte pro Gebietskörperschaft (`km_georesource_count_pointsWithinPolygon.py`)
- Summierte Linienlänge pro Gebietskörperschaft (`km_georesource_length_lineSegmentsWithinPolygon.py`)
- Statistiken anhand Eigenschaft der punktbasierten Georessource (`km_georesource_miscStatistics.py`)
- Prozentualer Anteil für eine Teilmenge gewählter Punktobjekte pro Gebietskörperschaft (`km_georesource_share_byPropertyValue.py`)
- Leitindikator - verkettete Berechnung (`km_headline_indicator.py`)
- Absolute Veränderung bezogen auf Zeitspanne (`km_indicator_absChange_nTemporalItems.py`)
- Absolute Veränderung bezogen auf festen Referenz-Zeitpunkt (`km_indicator_absChange_refDate.py`)
- Grad der Kontinuität bezogen auf Zeitspanne (`km_indicator_continuity_nTemporalItems.py`)
- Division zweier Indikatoren (`km_indicator_divide.py`)
- Multiplikation beliebig vieler Indikatoren (`km_indicator_multiply.py`)
- Multiplikation eines Indikators mit einem festen Wert (`km_indicator_multiply_value.py`)
- Prozentualer Anteil mehrerer Basisindikatoren von einem Referenzindikator (`km_indicator_percentage.py`)
- Promille Wert mehrerer Basisindikatoren von einem Referenzindikator (`km_indicator_promille.py`)
- Relative Veränderung bezogen auf Zeitspanne (`km_indicator_relChange_nTemporalItems.py`)
- Relative Veränderung bezogen auf einen Referenzzeitpunkt (`km_indicator_relChange_refDate.py`)
- Anteil mehrerer Basisindikatoren von einem Referenzindikator (`km_indicator_share.py`)
- Subtraktion mehrerer Basisindikatoren von einem Referenzindikator (`km_indicator_subtract.py`)
- Summe aus mehreren Indikatoren (`km_indicator_sum.py`)
- Trendberechnung bezogen auf Zeitspanne (`km_indicator_trend_nTemporalItems.py`)

##### Prozess-Scheduling: 
{: .no_toc }
Implementierung von Endpunkten zur Planung, Abfrage und zum Löschen von Prozess-Schedules.

##### Prefect-Integration: 
{: .no_toc }
Integration von Prefect zur Workflow-Steuerung und Ergebnis-Speicherung.

##### Konfiguration: 
{: .no_toc }
Alle externen Komponenten sind nun konfigurierbar (z.B. Keycloak, Daten-Management API).

##### Infrastruktur: 
{: .no_toc }
Bereitstellung eines Docker-Compose-Setups inklusive pygeoapi-Konfiguration und GitHub Actions für den Docker-Build.
