---
layout: default
title: Processes API
parent: Release Info
nav_order: 4
---

# Release Info (Processes API)
{: .no_toc }

Release Informationen für die OGC-konforme Schnittstelle zur Prozess-Orchestrierung.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen, Fehlerbehebungen und technischen Optimierungen der Processes API ab Version 1.0.0.

---

## Version 1.1.x
### 1.1.1 (28.05.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
*   **Leitindikatoren-Skript:** Probleme mit Gültigkeitszeiträumen wurden behoben.

### 1.1.0 (12.05.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
*   **Berechnungslogik:** Ein Fehler bei der Verarbeitung einer identischen Anzahl von Berechnungsindikatoren wurde behoben.
*   **HeadlineIndicator:** Diverse Fehler im HeadlineIndicator-Skript wurden korrigiert.
*   **Methoden-Import:** Probleme beim Importieren von Methoden wurden behoben.

#### Änderungen
{: .no_toc }
*   **Entwicklung:** Verschiedene Feature-Branches wurden in den Hauptzweig zusammengeführt.

---

## Version 1.0.x
### 1.0.1 (23.03.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
*   **Dateidownload:** Die Funktionalität zum Herunterladen von Dateien wurde implementiert.
*   **Export-System:** Neue Export-Skripte und eine entsprechende Basisklasse wurden hinzugefügt.
*   **Zeitfilter:** Ein Zeitspannen-Filter für Georessourcen wurde integriert.
*   **Öffentliche Exporte:** Die Unterstützung für öffentliche Export-Anfragen über den Controller wurde ergänzt.
*   **API-Konfiguration:** Die Processes API URL kann nun dynamisch für Antworten abgerufen werden.

#### Fehlerbehebungen
{: .no_toc }
*   **Legenden:** Die dynamische Legende für Prozentskripte wurde korrigiert.
*   **Code-Qualität:** Diverse Tippfehler und fehlerhafte Methodensignaturen wurden behoben.
*   **Zeitreihen:** Probleme mit leeren Zeitreihen und ungültigen Referenzdaten wurden korrigiert.
*   **Statistik:** Ein Fehler bei der Berechnung der Standardabweichung wurde behoben.
*   **Parameter:** Der Eingabeparameter `comp_filter` wurde korrigiert.
*   **Geoverarbeitung:** Fehler in der `PointsWithinPolygon` Funktion wurden behoben.
*   **Datenintegrität:** Fehler bei nicht existenten Referenzdaten wurden abgefangen.

#### Änderungen
{: .no_toc }
*   **Prozessmanagement:** Die erste offizielle Prozessregistrierung und -ausführung wurde ermöglicht.
*   **Export-Erweiterung:** Verschiedene Export-Prozesse (Single, SU, Multiple) wurden implementiert.
*   **Visualisierung:** Das Symbol für Indikatoren in der Legende wurde angepasst.
*   **Infrastruktur:** Das Gunicorn Startup-Kommando wurde für eine bessere Stabilität optimiert.
*   **Abhängigkeiten:** Die Prefect-Version wurde festgeschrieben, um Inkompatibilitäten zu vermeiden.
*   **Fehlermanagement:** Fehlgeschlagene Prozesse werden nun explizit als "Work in Progress" markiert.
*   **Wartung:** Ein automatisches Deployment zur Bereinigung alter Jobs wurde eingeführt.
*   **Sicherheit:** Die Authentifizierungsprüfungen für die Prozessausführung wurden verfeinert.

### 1.0.0 (21.01.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
*   **Entwicklungs-Setup:** Ein vollständiges Docker-Setup für die lokale Entwicklung wurde bereitgestellt.
*   **Daten-Hilfsfunktionen:** Neue Funktionen zur Konvertierung von Zeitreihen in DataFrames und zurück wurden implementiert.
*   **Job-Management:** Klassen für Job-Zusammenfassungen und Ergebnisse wurden eingeführt.
*   **Testing:** Unit Tests für die dataio-Utility-Funktionen wurden hinzugefügt.
*   **Analyse-Skripte:** Prozessbeschreibungen für PercentageShare, Georessourcen-Statistiken und Indikatorsummen wurden integriert.
*   **Schnittstellen:** Ein iPython-Modul sowie Endpunkte für Schedules und Flow-Definitionen wurden erstellt.
*   **Automatisierung:** Ein Modul zum Triggern von Schedules und ein Docker Compose Setup für Prefect wurden hinzugefügt.
*   **Skript-Bibliothek:** Das HeadlineIndicator-Skript und die ZSCORE-Berechnungsmethode wurden implementiert.

#### Fehlerbehebungen
{: .no_toc }
*   **Konfiguration:** Fehler bei der Handhabung von Umgebungsvariablen wurden behoben.
*   **Typisierung:** Der Ergebnistyp des Indikator-Controllers wurde korrigiert.
*   **Validierung:** Pydantic-Validierungsfehler wurden behoben.
*   **Geodaten:** Fehler beim Vergleich von Feature-IDs zwischen Strings und Integern wurden korrigiert.
*   **Datenhandling:** Die Verarbeitung von Indikatorwerten mit dem Wert 0 wurde stabilisiert.

#### Änderungen
{: .no_toc }
*   **Architektur:** Die Initialisierung wurde überarbeitet und externe Komponenten sind nun vollständig konfigurierbar.
*   **Hilfsklassen:** Der KmHelper wurde in Python neu implementiert.
*   **API-Standardisierung:** Die OpenAPI-Modelle wurden an die aktuelle Spezifikation angepasst.
*   **CORS:** Konfigurierbare CORS-Regeln für die Flask-App wurden eingeführt.
*   **Logging:** Das Logging innerhalb der Docker-Umgebung wurde verbessert.
*   **Stabilität:** Die Ausnahmebehandlung und die Speicherung der Ergebnisse wurden optimiert.
