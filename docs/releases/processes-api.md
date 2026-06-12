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

## Version 1.x.x

### 1.1.0 - 1.1.1 (Mai 2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Indikatoren-Berechnung: 
{: .no_toc }
Korrektur eines Fehlers, der bei einer Reihe identischer berechneter Indikatoren auftrat.

##### Headline-Indikatoren: 
{: .no_toc }
Fehlerbehebungen im HeadlineIndicator-Skript.

#### Änderungen
{: .no_toc }

##### Technik: 
{: .no_toc }
Aktualisierung der Version und interne Code-Verbesserungen.

---

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

---

### 1.0.0 (Januar 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Initialer Release: 
{: .no_toc }
Bereitstellung der OGC-konformen Schnittstelle zur Prozess-Orchestrierung.

##### Prozess-Scheduling: 
{: .no_toc }
Implementierung von Endpunkten zur Planung, Abfrage und zum Löschen von Prozess-Schedules.

##### Prefect-Integration: 
{: .no_toc }
Integration von Prefect zur Workflow-Steuerung und Ergebnis-Speicherung.

##### Berechnungs-Skripte: 
{: .no_toc }
Re-Implementierung von Skripten zur Indikatoren-Berechnung in Python.

**Indikatoren-Skripte**


##### Infrastruktur: 
{: .no_toc }
Bereitstellung eines Docker-Compose-Setups inklusive pygeoapi-Konfiguration und GitHub Actions für den Docker-Build.

#### Änderungen
{: .no_toc }

##### Konfiguration: 
{: .no_toc }
Alle externen Komponenten sind nun konfigurierbar (z.B. Keycloak, Daten-Management API).
