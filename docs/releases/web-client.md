---
layout: default
title: Web-Client
parent: Release Info
nav_order: 1
---

# Release Info (Web-Client)
{: .no_toc }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine detaillierte Übersicht der wichtigsten Neuerungen, Verbesserungen und architektonischen Änderungen des KomMonitor Web-Clients.

---

## Version 5.1.x

### 5.1.3 (5. Juni 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Filter-Konfiguration:
Die administrativen Filter-Einstellungen können nun gezielt für Admnistratoren von Ressourcen freigeschaltet werden.

#### Fehlerbehebungen
{: .no_toc }
##### Globale Filter:
Probleme beim Abruf von Indikatoren und Geodaten bei aktiven globalen Filtern wurden behoben. Es wird nun sichergestellt, dass Datensätze wirksam gefiltert werden.

### 5.1.2 (27. Mai 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Adresssuche:
Die Adresssuche lässt sich nun auch für Adressen außerhalb Deutschlands und in weiteren Sprachen konfigurieren.

### 5.1.1 (15. Mai 2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
##### Radardiagramme:
Probleme mit der Funktion "Raumeinheits-Selektion aufheben" und der damit verbundenen Entfernung von Raumeinheiten aus dem Radardiagramm wurden behoben.

#### Änderungen
{: .no_toc }
##### Wartungs-Release:
Offizielles Wartungs-Release zur Stabilisierung der 5.1.x-Linie.

### 5.1.0 (6. Mai 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Reporting Tool:
Umfangreiche Verbesserungen des Reporting Tools, inklusive beschleunigter Vorschau, verbesserter Benutzerführung, ergänzter Hinweistexte sowie einer optimierten Fortschrittsanzeige und Hintergrund-Aufbereitung von Kartenbildern.

---

## Version 5.0.x

### 5.0.0 (23. März 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Indikatoren-Fortschreibung:
Einführung einer neuen Methodik für die automatisierte Fortführung und Berechnung von Indikatoren.
##### Skriptverwaltung:
Anpassungen in der Skriptverwaltung zur Unterstützung von On-Demand Berechnungen und dynamischen Skript-Prototypen.
##### Reporting-Performance:
Implementierung eines asynchronen Lade-Konzepts ("Preview-First"), bei dem Berichtsseiten sofort eine Vorschau anzeigen, während Geodaten im Hintergrund geladen werden.

---

## Version 4.4.x

### 4.4.3 (5. Juni 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Filter-Konfiguration:
Übernahme der Filter-Sichtbarkeitskonfiguration aus dem 5.x-Zweig für Nutzer der 4.4er Wartungslinie.

#### Fehlerbehebungen
{: .no_toc }
##### Metadaten-Fix:
Behebung redundanter Metadaten-Abrufe zur Vermeidung von Fehlern bei globalen Filtern.

### 4.4.2 (29. Mai 2026)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### Sichtbarkeit:
Der Bereich Filter-Einstellungen ist nun auch für Administratoren von Ressourcen verfügbar. Technisches Release zur Synchronisation interner Metadaten und Versions-Templates.

### 4.4.0 & 4.4.1 (Mai 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Feature-Backports:
Integration der Performance-Optimierungen für das Berichtswesen (asynchrone Generierung von Geodaten-Features) in die stabile 4.4.x-Linie.

#### Fehlerbehebungen
{: .no_toc }
##### Radar-Diagramme:
Konsistente Interaktions-Fixes für komplexe Diagramm-Typen beim Abwählen von Objekten.

---

## Version 4.3.x

### 4.3.6 (20. April 2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
##### Raumfilter-Logik:
Verfeinerung der räumlichen Selektionsalgorithmen und Behebung von Kantenfällen bei der Filterung komplexer Geometrien.

### 4.3.0 - 4.3.5 (Januar - März 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Raumebenen-Aggregation:
Neue Benutzeroberfläche zur Auswahl verschiedener Aggregationsstufen für Raumeinheiten inklusive vollständiger Integration in Import- und Export-Workflows.
##### Visualisierungs-Details:
Dynamische Datums-Beschriftungen auf der X-Achse von Balkendiagrammen und neue Layout-Optionen für den Druck-Modus.

#### Änderungen
{: .no_toc }
##### Automatisierung:
Automatischer Metadaten-Refresh nach On-Demand-Berechnungen zur Sicherstellung aktueller Anzeigen.

---

## Version 4.2.x

### 4.2.0 & 4.2.1 (Juli - September 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Kartenprojektionen:
Integration verbesserter Projektions-Logik in Diagramme zur exakten Überlagerung statistischer Daten auf Karten.

#### Änderungen
{: .no_toc }
##### UX-Feedback:
Einführung neuer Statusmeldungen und Fortschrittsbalken während der Vorbereitung umfangreicher Berichtsdaten.

---

## Version 4.1.x

### 4.1.0 & 4.1.1 (Mai 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Modulares Filter-System:
Komplettes Redesign des Filter-Dialogs mit einem übersichtlichen Modal und tabellarischer Mehrfachauswahl für Indikatoren und Ressourcen.
##### Barrierefreiheit:
Erweiterte Unterstützung für assistierende Technologien und Tastaturnavigation für komplexe UI-Widgets.

---

## Version 4.0.x

### 4.0.0 (Beta-Phase)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Berechtigungskonzept:
Umstellung des Benutzermenüs auf ein granulares Berechtigungskonzept mit Synchronisation von Benutzergruppen.
##### Tabellen-Ansicht:
Einführung eines performanten Gitter-Layouts für Ressourcen-Tabellen für flüssiges Scrollen bei großen Datenmengen.

#### Fehlerbehebungen
{: .no_toc }
##### Datenintegrität:
Verbesserte Handhabung von leeren Werten und fehlenden Datenpunkten in Berechnungs-Skripten.

---

## Version 3.4.x

### 3.4.0 - 3.4.3 (Juli 2025 - März 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Zahlenformatierung:
Verbesserte Darstellung formatierter Zahlen in Filter-Komponenten.

#### Änderungen
{: .no_toc }
##### Klassifizierung:
Optimierte Unterscheidung zwischen Rohwerten und eindeutigen Werten für die Klasseneinteilung in der Legende.

---

## Version 3.3.x

### 3.3.0 (5. Mai 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Design & Theming:
Einführung von Farbthemen für alle Komponenten und Unterstützung benutzerdefinierter Farbschemata.

#### Änderungen
{: .no_toc }
##### Begrifflichkeiten:
Anpassung der Terminologie (z.B. "Raumeinheit" statt "Feature"), um die Verständlichkeit für Planer*innen zu erhöhen.

---

## Version 3.2.x

### 3.2.0 & 3.2.1 (Januar - Februar 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Favoriten:
Möglichkeit, Georessourcen als Favoriten zu markieren.

#### Änderungen
{: .no_toc }
##### Skript-Verwaltung:
Neue Hinweise und Sicherheitsabfragen bei Massenaktualisierungen und in der Skript-Verwaltung.

---

## Version 3.1.x

### 3.1.0 - 3.1.8 (August 2024 - Januar 2025)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }
##### Diagramm-Referenzen:
Neue Referenzwerte für Ranking-Diagramme zur Korrektur von Fehlern in Zeitreihen-Berichten.

#### Änderungen
{: .no_toc }
##### Farben:
Reaktivierung verschiedener Farppaletten und Unterstützung für zusätzliche Farbschemata.
##### Statistik:
Neue Konfigurationsoptionen für die Anzeige von Mittelwerten in Legenden und Diagrammen.

---

## Version 3.0.x

### 3.0.0 - 3.0.5 (Juni - Juli 2024)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Erreichbarkeitsanalysen:
Integration von Erreichbarkeits-Zonen direkt in die Hauptkarte und neue Kurzinformationen für Statistiken.
##### Metadaten-Tab:
Umstrukturierung der Legende: Metadaten und verknüpfte Ressourcen befinden sich nun in einem eigenen Reiter.
##### Regionale Referenzwerte:
Neue Benutzeroberfläche für den Vergleich mit regionalen Durchschnittswerten in Zeitreihen.

#### Änderungen
{: .no_toc }
##### Karten-Interaktion:
Anzeige von Informationstexten direkt in der Karte und Legende.
##### Technik-Update:
Modernisierung der Basis-Technologien für eine zukunftssichere Anwendung.

---

## Version 2.2.x

### 2.2.0 - 2.2.2 (Januar 2024)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Standard-Schnittstellen:
Unterstützung für moderne Geodaten-Standards (OGC API Features) für Ressourcen und Raumeinheiten.

#### Fehlerbehebungen
{: .no_toc }
##### Stabilität:
Allgemeine Fehlerbehebungen und Stabilitätsverbesserungen in der Kartenansicht.

---

## Version 2.1.x

### 2.1.0 - 2.1.17 (August 2023 - Dezember 2023)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Rollenmanagement:
Umstellung der Berechtigungsverwaltung auf ein effizientes Daten-Gitter (RBAC Grid) mit Auswahlfeldern.
##### Navigation:
Neue Klick-Interaktionen für direktes Springen in der Ressourcen-Verwaltung über eine Fortschrittsanzeige.
##### Geokodierung:
Verbesserte Adresssuche und Geokodierung für eine präzisere Platzierung von Ressourcen.

#### Fehlerbehebungen
{: .no_toc }
##### Skripting-Logik:
Verfeinerung der Handhabung von fehlenden Werten und Optimierung mathematischer Grundlagen für Diagramme.

---

## Version 2.0.x

### 2.0.0 - 2.0.1 (Juli 2022)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Erreichbarkeits-Analysen (Beta):
Erster Entwurf für Erreichbarkeits-Zonen und Analysen interessanter Orte (POI) inklusive Puffer-Zonen.
##### Barrierefreiheit:
Erste Beta-Phase für verbesserte Zugänglichkeit der Benutzeroberfläche.
##### Berechtigungskonzept:
Einführung des initialen rollenbasierten Zugriffskontrollmodells (RBAC).

#### Änderungen
{: .no_toc }
##### Authentifizierung:
Integration von Keycloak zur zentralen Benutzerverwaltung und automatischer Abruf der Sicherheitskonfiguration.
##### Performance:
Optimierung der Ladegeschwindigkeit durch Auslagerung großer Software-Bibliotheken.

---

## Version 1.7.x

### 1.7.0 (Februar 2022)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### ZIP-Export:
Funktion zum Herunterladen von Indikatordaten als Archiv inklusive Metadaten.

---

## Version 1.6.x

### 1.6.0 (Dezember 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Skriptverwaltung:
Erweiterungen in der administrativen Verwaltung von Berechnungs-Skripten.

#### Änderungen
{: .no_toc }
##### Metadaten-Caching:
Implementierung einer Zwischenspeicherung für Metadaten zur Beschleunigung der Anzeige.

---

## Version 1.5.x

### 1.5.0 (November 2021)
{: .no_toc }

#### Änderungen
{: .no_toc }
##### Job-Monitoring:
Verbesserte Übersicht laufender Hintergrundprozesse mit Statusanzeigen.

---

## Version 1.4.x

### 1.4.0 (September 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Suche & Filter:
Einführung einer globalen Suchfunktion für alle Datentabellen.

---

## Version 1.0.x - 1.3.x

### 1.0.0 - 1.3.0 (Mai 2021 - August 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Geführte Tour:
Einführung einer interaktiven Einführung für neue Nutzer*innen.

#### Änderungen
{: .no_toc }
##### Tabellen-Migration:
Umstellung der zentralen Übersichts-Tabellen auf ag-grid für verbesserte Performance.

---

## Version 0.5.x

### Initial-Phase (Juni 2019)
{: .no_toc }

#### Neue Features
{: .no_toc }
##### Mapping-Grundlagen:
Erster Prototyp der Karten-Engine (Leaflet Integration) mit Fokus auf dynamischem Styling von Geodaten.
