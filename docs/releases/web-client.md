---
layout: default
title: Web-Client
parent: Release Info
nav_order: 1
---

# Release Info (Web-Client)
{: .no_toc }

Release Informationen für den KomMonitor Web Client
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen und Verbesserungen des KomMonitor Web-Clients ab Version 3.0.0. Diese Zusammenfassung konzentriert sich auf Funktionen, die für Anwender*innen direkt relevant sind.

---

## Version 5.1.x
### 5.1.2
{: .no_toc }
*   **Geokodierung:** Die Adresssuche (Geokodierung) kann nun flexibler für verschiedene Länder konfiguriert werden.

### 5.1.1 (15. Mai 2026)
{: .no_toc }
*   **Radar-Diagramme:** Optimierte Aktualisierung der Diagramme beim Abwählen von Objekten in der Karte.
*   Offizielles Wartungs-Release.

### 5.1.0 (6. Mai 2026)
{: .no_toc }
*   **Berichtswesen:** Erhebliche Verbesserungen beim Export von Berichten. Karten-Snapshots (Leaflet) und Diagramme werden nun zuverlässiger und mit korrekter Ausrichtung im Hintergrund generiert.
*   **Logo-Darstellung:** Fehler bei der Logo-Anzeige in generierten Berichten behoben.

---

## Version 5.0.x
### 5.0.0 (23. März 2026)
{: .no_toc }
*   **Performance-Schub:** Deutlich schnellere Generierung von Berichtsseiten durch asynchrone Hintergrundverarbeitung.
*   **Prozess-Anbindung:** Integration der neuen Endpunkte für die Terminierung (`/schedule`) und Verwaltung von Jobs (`/jobs`) der Processes-API.
*   **Skript-Management:** Erweiterung um dynamische Skript-Prototypen bei der Auswahl von Skript-Typen.

---

## Version 4.4.x
### 4.4.0 & 4.4.1 (Mai 2026)
{: .no_toc }
*   **Berichts-Optimierung:** Performance-Verbesserungen durch Hintergrund-Generierung von Geodaten-Features.
*   **Zeitreihen:** Fehlerbehebung bei der Erstellung von Datentabellen für Indikatoren-Zeitreihen.
*   **Radar-Diagramme:** Verbesserte Interaktion beim Abwählen von Features.

---

## Version 4.3.x
### 4.3.6 (20. April 2026)
{: .no_toc }
*   **Raumfilter:** Verschiedene Fehlerbehebungen und Detailverbesserungen bei der räumlichen Filterung.

### 4.3.5 (24. März 2026)
{: .no_toc }
*   **Benutzerfreundlichkeit:** Korrektur eines Fehlers beim Mouse-over-Effekt in der Karte und bei der Auswahl von Verantwortlichen (Owner).

### 4.3.4 (3. März 2026)
{: .no_toc }
*   **Karten-Interaktion:** Verfeinerte Legenden-Informationen für räumlich gefilterte Einheiten und Korrektur von doppelten Mouse-over-Events.

### 4.3.3 (30. Januar 2026)
{: .no_toc }
*   **Berichtswesen & Diagramme:** Neue Layout-Optionen für den Druck und dynamische Stile für Radar-Diagramme.
*   **Navigation:** Anzeige des gewählten Datums in der Legende der Balkendiagramme (X-Achse).

### 4.3.0 - 4.3.2 (Januar 2026)
{: .no_toc }
*   **Raumebenen:** Neue Option zur Auswahl verschiedener Aggregationsebenen für Raumeinheiten, inklusive Integration in den Import/Export.
*   **Automatisierung:** Automatische Aktualisierung von Metadaten nach erfolgreichen On-Demand-Berechnungsprozessen.

---

## Version 4.2.x
### 4.2.0 & 4.2.1 (Juli - September 2025)
{: .no_toc }
*   **Kartenprojektion:** Integration von D3 für verbesserte Kartenprojektionen (Mercator) in ECharts und stabilere Überlagerung mit Leaflet-Karten.
*   **Benachrichtigungen:** Neue Statusmeldungen für Nutzer*innen während der Vorbereitung von Berichtsseiten.

---

## Version 4.1.x
### 4.1.0 & 4.1.1 (Mai 2025)
{: .no_toc }
*   **Filter-Modul:** Einführung eines neuen Modals zum Hinzufügen und Bearbeiten von Filtern, inklusive tabellarischer Auswahlmöglichkeiten.
*   **Barrierefreiheit:** Verbesserte Konfigurationsmöglichkeiten für die Zugänglichkeit von Widgets.

---

## Version 4.0.x
### 4.0.0 (Beta-Phase)
{: .no_toc }
*   **Berechtigungskonzept:** Umstellung auf rollenbasierte Berechtigungen im Benutzermenü und Synchronisation mit Keycloak-Gruppen für Organisationseinheiten.
*   **Oberfläche:** Neues Gitter-Layout (Grid) für Übersichts-Tabellen.
*   **Datenverarbeitung:** Korrektur der Handhabung von Null-Werten in Berechnungs-Skripten (Summe/Anteil).

---

## Version 3.4.x
### 3.4.0 - 3.4.3 (Juli 2025 - März 2026)
{: .no_toc }
*   **Zahlenformatierung:** Verbesserte Darstellung formatierter Zahlen in Filter-Komponenten.
*   **Klassifizierung:** Optimierte Unterscheidung zwischen Rohwerten und eindeutigen Werten für die Klasseneinteilung in der Legende.

---

## Version 3.3.x
### 3.3.0 (5. Mai 2025)
{: .no_toc }
*   **Design & Theming:** Einführung von Farbthemen (Color-Theming) für alle Komponenten und Unterstützung benutzerdefinierter Farbschemata.
*   **Begrifflichkeiten:** Anpassung der Terminologie (z.B. "Raumeinheit" statt "Feature"), um die Verständlichkeit für Planer*innen zu erhöhen.

---

## Version 3.2.x
### 3.2.0 & 3.2.1 (Januar - Februar 2025)
{: .no_toc }
*   **Favoriten:** Möglichkeit, Georessourcen als Favoriten zu markieren.
*   **Skript-Verwaltung:** Neue Hinweise und Sicherheitsabfragen bei Batch-Updates und der Skript-Verwaltung.

---

## Version 3.1.x
### 3.1.0 - 3.1.8 (August 2024 - Januar 2025)
{: .no_toc }
*   **Diagramm-Referenzen:** Neue Referenzwerte für Ranking-Diagramme zur Korrektur von Fehlern in Zeitreihen-Berichten.
*   **Farben:** Reaktivierung divergierender Farppaletten und Unterstützung für benutzerdefinierte ColorBrewer-Paletten.
*   **Statistik:** Neue Konfigurationsoptionen für die Anzeige von Mittelwerten in Legenden und Diagrammen.

---

## Version 3.0.x
### 3.0.0 - 3.0.5 (Juni - Juli 2024)
{: .no_toc }
*   **Erreichbarkeitsanalysen:** Integration von Erreichbarkeits-Isochronen direkt in die Hauptkarte und neue Erläuterungen (Tooltips) for Statistiken.
*   **Metadaten-Tab:** Umstrukturierung der Legende: Metadaten und verknüpfte Ressourcen befinden sich nun in einem eigenen, übersichtlichen Reiter.
*   **Karten-Interaktion:** Anzeige von POI-Texten direkt in der Karte und Legende.
*   **Regionale Referenzwerte:** Neue Benutzeroberfläche für den Vergleich mit regionalen Durchschnittswerten in Zeitreihen.
*   **Technik-Update:** Modernisierung der Basis-Technologien (AngularJS & Webpack) für eine zukunftssichere Anwendung.
