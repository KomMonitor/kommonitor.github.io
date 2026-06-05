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

Hier finden Sie eine detaillierte Übersicht der wichtigsten Neuerungen, Verbesserungen und architektonischen Änderungen des KomMonitor Web-Clients ab Version 3.0.0. Diese Zusammenfassung bietet sowohl für Anwender*innen als auch für Administrator*innen wertvolle Informationen zur Weiterentwicklung der Plattform.

---

## Version 5.1.x (Aktueller Zweig)
### 5.1.3 (5. Juni 2026)
{: .no_toc }
*   **Filter-Konfiguration:** Neue administrative Steuerung, um Filter-Einstellungen gezielt für Administratoren von Ressourcen verfügbar zu machen. Dies verbessert die Transparenz bei der Datenverwaltung.
*   **Fehlerbehebung Metadaten:** Optimierung des Abruf-Logiks für Metadaten; redundante Anfragen wurden eliminiert, was die Stabilität globaler Filter-Einstellungen signifikant erhöht.

### 5.1.2
{: .no_toc }
*   **Geokodierung & Internationalisierung:** Die Adresssuche wurde flexibilisiert. Über neue Konfigurationsparameter können nun länderspezifische Geokodierungs-Einstellungen vorgenommen werden, was den Einsatz über Deutschland hinaus erleichtert.

### 5.1.1 (15. Mai 2026)
{: .no_toc }
*   **Interaktive Diagramme:** Die Aktualisierungslogik für Radar-Diagramme wurde optimiert, um eine flüssige Darstellung beim dynamischen Abwählen von Kartenobjekten zu gewährleisten.
*   Offizielles Wartungs-Release zur Stabilisierung der 5.1.x-Linie.

### 5.1.0 (6. Mai 2026)
{: .no_toc }
*   **Globales Hintergrund-Reporting:** Einführung einer neuen Architektur für den Berichts-Export. Karten-Snapshots (Leaflet) und Diagramme (ECharts) werden nun in einem unsichtbaren Hintergrund-Container (`reporting-background-page`) gerendert. Dies stellt sicher, dass Exporte auch dann die korrekten Dimensionen und Ausrichtungen haben, wenn die entsprechenden UI-Elemente im Browser gerade nicht sichtbar sind.
*   **Logo-Handling:** Korrektur der Pfad-Auflösung für Logos in generierten PDF-Berichten.

---

## Version 5.0.x
### 5.0.0 (23. März 2026)
{: .no_toc }
*   **Processes-API Integration:** Volle Unterstützung der neuen `/schedule` und `/jobs` Endpunkte. Dies ermöglicht die detaillierte Planung und Überwachung von Hintergrund-Prozessen (z.B. Indikatoren-Berechnungen) direkt aus der Weboberfläche.
*   **Reporting-Performance:** Implementierung eines asynchronen Lade-Konzepts. Berichtsseiten zeigen nun sofort eine Vorschau an, während die vollständigen Geodaten-Features im Hintergrund nachgeladen werden ("Preview-First").
*   **Skript-Management:** Erweiterung der Oberfläche um dynamische Prototypen für Berechnungs-Skripte, was die Entwicklung neuer Indikatoren vereinfacht.

---

## Version 4.4.x
### 4.4.3 (5. Juni 2026)
{: .no_toc }
*   **Filter-Konfiguration:** Übernahme der Filter-Sichtbarkeitskonfiguration aus dem 5.x-Zweig für Nutzer der 4.4er Wartungslinie.
*   **Metadaten-Fix:** Behebung redundanter Metadaten-Abrufe zur Vermeidung von Fehlern bei globalen Filtern.

### 4.4.2 (29. Mai 2026)
{: .no_toc }
*   **Sichtbarkeit:** Der Bereich Filter-Einstellungen ist nun auch für Administratoren von Ressourcen verfügbar. Technisches Release zur Synchronisation interner Metadaten und Versions-Templates (`version-info.template.html`).

### 4.4.0 & 4.4.1 (Mai 2026)
{: .no_toc }
*   **Feature-Backports:** Integration der Performance-Optimierungen für das Berichtswesen (asynchrone Generierung von Geodaten-Features) in die stabile 4.4.x-Linie.
*   **Radar-Diagramme:** Konsistente Interaktions-Fixes für komplexe Diagramm-Typen.

---

## Version 4.3.x
### 4.3.6 (20. April 2026)
{: .no_toc }
*   **Raumfilter-Logik:** Verfeinerung der räumlichen Selektionsalgorithmen und Behebung von Kantenfällen bei der Filterung komplexer Geometrien.

### 4.3.0 - 4.3.5 (Januar - März 2026)
{: .no_toc }
*   **Raumebenen-Aggregation:** Neue Benutzeroberfläche zur Auswahl verschiedener Aggregationsstufen für Raumeinheiten. Inklusive vollständiger Integration in die Import- und Export-Workflows für eine flexible Datenanalyse auf unterschiedlichen Maßstabsebene.
*   **Visualisierungs-Details:** Dynamische Datums-Beschriftungen auf der X-Achse von Balkendiagrammen und neue Layout-Optionen für den Druck-Modus.
*   **Automatisierung:** Automatischer Metadaten-Refresh nach On-Demand-Berechnungen.

---

## Version 4.2.x
### 4.2.0 & 4.2.1 (Juli - September 2025)
{: .no_toc }
*   **Kartenprojektionen (D3 & ECharts):** Integration von D3-Projektions-Logik in die ECharts-Diagramme. Dies löst langjährige Probleme bei der exakten Überlagerung von statistischen Diagrammen auf Mercator-basierten Leaflet-Karten.
*   **UX-Feedback:** Einführung neuer Statusmeldungen und Fortschrittsbalken während der Vorbereitung umfangreicher Berichtsdaten.

---

## Version 4.1.x
### 4.1.0 & 4.1.1 (Mai 2025)
{: .no_toc }
*   **Modulares Filter-System:** Komplettes Redesign des Filter-Dialogs. Einführung eines übersichtlichen Modals mit tabellarischer Mehrfachauswahl für Indikatoren und Ressourcen.
*   **Barrierefreiheit:** Erweiterte ARIA-Unterstützung und Tastaturnavigation für komplexe UI-Widgets.

---

## Version 4.0.x
### 4.0.0 (Beta-Phase)
{: .no_toc }
*   **Role-Based Access Control (RBAC):** Umstellung des Benutzermenüs auf ein granulares Berechtigungskonzept. Synchronisation von Keycloak-Gruppen mit Organisationseinheiten ermöglicht eine automatische Zuweisung von Datenzugriffsrechten.
*   **Modernisierte Tabellen-Ansicht:** Einführung eines performanten Gitter-Layouts (Grid) für Ressourcen-Tabellen, das auch bei hunderten Einträgen flüssiges Scrollen ermöglicht.
*   **Datenintegrität:** Verbesserte Handhabung von Null-Werten und fehlenden Datenpunkten in Berechnungs-Skripten.

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

---

## Version 2.x
### 2.1.0 - 2.2.0 (August 2023 - Januar 2024)
{: .no_toc }
*   **OGC API - Features:** Einführung der Unterstützung für den OGC API - Features Standard sowohl für Georessourcen als auch für Raumeinheiten. Dies umfasst dedizierte Retriever- und Konverter-Logiken.
*   **Rollenmanagement:** Umstellung der Berechtigungsverwaltung von einer dualen Listenansicht auf ein effizienteres Daten-Gitter (Grid) mit Checkboxen, was die Administration großer Organisationseinheiten erleichtert.
*   **Skripting-Logik:** Verfeinerung der Handhabung von `NoData`-Werten in Berechnungs-Skripten und Optimierung der mathematischen Grundlagen für Regressions- und Radar-Diagramme.
*   **Navigations-Verbesserungen:** Neue Klick-Interaktionen in Fortschrittsbalken ermöglichen das direkte Springen zwischen verschiedenen Seiten der Ressourcen-Verwaltung.

### 2.0.0 - 2.0.1 (Juli 2022)
{: .no_toc }
*   **Erreichbarkeits-Analysen (Beta):** Erster Entwurf für die Anzeige von Isochronen und POI-Analysen, inklusive Unterstützung für Puffer-basierte Erreichbarkeitszonen.
*   **Authentifizierung:** Umstellung auf den automatischen Abruf der Keycloak-Konfiguration über den `client-config` Service.
*   **Performance:** Auslagerung großer Bibliotheken wie `jspdf` auf externe CDNs zur Reduzierung der Paketgröße und Verbesserung der Ladezeiten.

---

## Version 1.x
### 1.4.0 - 1.7.0 (September 2021 - Februar 2022)
{: .no_toc }
*   **ZIP-Export:** Neue Funktion zum Herunterladen von Indikatordaten als ZIP-Archiv, das sowohl die Rohdaten als auch die zugehörigen Metadaten enthält.
*   **Metadaten-Caching:** Implementierung eines clientseitigen Caches für Ressourcen-Metadaten und Zeitstempel, um redundante API-Aufrufe zu minimieren und die gefühlte Geschwindigkeit zu erhöhen.
*   **Suche & Filter:** Einführung einer globalen Suchfunktion für Namensspalten in allen Datentabellen.

### 1.0.0 - 1.3.0 (Mai 2021 - August 2021)
{: .no_toc }
*   **Geführte Tour (Guided Tour):** Einführung einer interaktiven Einführung, die neue Nutzer*innen durch die Kernfunktionen der Anwendung leitet.
*   **ag-grid Migration:** Umstellung der zentralen Übersichts-Tabellen von Standard-Datatables auf `ag-grid` für deutlich verbesserte Performance und erweiterte Filteroptionen.
*   **Job-Monitoring:** Re-Implementierung der Job-Übersicht mit einer neuen Grid-Bibliothek und Status-Labels für die Warteschlange.
*   **Icon-System:** Stabilisierung des Icon-Pickers und Integration von Standard-Bootstrap-Glyphicons.

---

## Version 0.5 (Juni 2019)
### Initial-Phase
{: .no_toc }
*   **Mapping-Grundlagen:** Erster Prototyp der Karten-Engine auf Basis von **Leaflet**. Fokus auf dem dynamischen Styling von GeoJSON-Inhalten und der Ablösung statischer Abhängigkeiten.

