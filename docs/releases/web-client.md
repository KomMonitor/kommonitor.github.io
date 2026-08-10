---
layout: default
title: Web-Client
parent: Release Info
nav_order: 1
date: 2026-08-10
description: Release-Informationen für den KomMonitor Web-Client
---

# Release Info (Web-Client)
{: .no_toc }

Release Informationen für den KomMonitor Web-Client.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine detaillierte Übersicht der wichtigsten Neuerungen, Verbesserungen und architektonischen Änderungen des KomMonitor Web-Clients.

---

## Version 5.1.x

### 5.1.5 (10.08.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Choroplethenkarte-Legende:
{: .no_toc }
Ein fehlerhafter unbegrenzter Legendeneintrag in Choroplethenkarten wurde behoben, der auftrat, wenn keine negativen Werte im Datensatz vorhanden waren.

##### Zeitreihen-Berichte:
{: .no_toc }
Inkonsistente Darstellungen in Zeitreihendiagrammen, die bei nicht chronologisch sortierten Zeitstempeln auftreten konnten, wurden korrigiert.

#### Änderungen
{: .no_toc }

##### Zeitreihen- und Boxplot-Diagramme im Berichtswesen:
{: .no_toc }
Die Übersichtsdiagramme für Zeitreihen und Boxplots in Berichten wurden verbessert. Standardmäßig werden nun maximal 5 Flächen pro Übersichtsdiagramm angezeigt, um die Lesbarkeit zu steigern.

---

### 5.1.4 (17.07.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Wertebereich-Filter:
{: .no_toc }
Fehlerbehebung bei der Filterung von Indikatorwerten: Wenn globale Indikatorgenauigkeit und indikatoren-spezifische Genauigkeit unterschiedlich eingestellt waren, wurden Werte nicht korrekt gefiltert.

---

### 5.1.3 (05.06.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Filter-Konfiguration:
{: .no_toc }
Die administrativen Filter-Einstellungen können nun über den Parameter `showFilterConfigForGeodataEditRoleNames` gezielt für Nutzer mit Bearbeitungsberechtigungen auf Datensätzen freigeschaltet werden.

#### Fehlerbehebungen
{: .no_toc }

##### Globale Filter:
{: .no_toc }
Probleme beim Abruf von Indikatoren und Geodaten bei aktiven globalen Filtern wurden behoben. Es wird nun sichergestellt, dass Datensätze korrekt gefiltert werden.

---

### 5.1.2 (27.05.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Adresssuche:
{: .no_toc }
Die Adresssuche lässt sich nun über die Parameter `geocoderLanguage` und `geocoderCountryCodes` auch für Adressen außerhalb Deutschlands und in weiteren Sprachen konfigurieren (setzt einen kompatiblen Geocoding-Dienst voraus).

---

### 5.1.1 (15.05.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Radardiagramme:
{: .no_toc }
Probleme mit der Funktion „Raumeinheits-Selektion aufheben" und der damit verbundenen Entfernung von Raumeinheiten aus dem Radardiagramm wurden behoben.

#### Änderungen
{: .no_toc }

##### Wartungs-Release:
{: .no_toc }
Offizielles Wartungs-Release zur Stabilisierung der 5.1.x-Linie.

---

### 5.1.0 (06.05.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Reporting Tool:
{: .no_toc }
Umfangreiche Verbesserungen des Reporting Tools: Die Vorschau zeigt sofort ausgewählte Karten- und Tabellenseiten an, während Daten im Hintergrund aufbereitet werden (beschleunigter Aufbau). Die Benutzerführung wurde überarbeitet, sodass Daten- und Parameterauswahl klar von der Vorschaugenerierung getrennt sind. Hinweistexte, eine sichtbare Fortschrittsanzeige sowie eine optimierte Hintergrundverarbeitung von Kartenbildern wurden ergänzt.

##### Erreichbarkeitsanalyse:
{: .no_toc }
Überarbeiteter Workflow für die Erreichbarkeitsanalyse im Reporting, inklusive unterstützender Informationen zur Bedienung.

---

## Version 5.0.x

### 5.0.0 (23.03.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Prozess-Methodik (Processes API):
{: .no_toc }
Einführung der neuen KomMonitor Processes API (OGC API – Processes Standard mit Prefect-Orchestrierung), die die bisherigen Komponenten Processing Engine und Processing Scheduler ablöst. Skripte können nun als Prozesse mit dynamischen Prozessbeschreibungen angelegt, auf Abruf ausgeführt und mit individuellen Zeitreihen-Methodiken und Ausführungsintervallen pro Indikator konfiguriert werden.

##### Skriptverwaltung:
{: .no_toc }
Die Skriptverwaltung unterstützt explizite Raumebenen-Auswahl (auch mehrere Ebenen gleichzeitig), On-Demand-Ausführung einzelner Skripte sowie detaillierte Job-Zusammenfassungen mit berechneten Indikatoren, Zeitpunkten und Fehlerinformationen.

##### Reporting-Performance:
{: .no_toc }
Implementierung eines asynchronen Lade-Konzepts („Preview-First"): Berichtsseiten zeigen sofort eine Vorschau, während Geodaten im Hintergrund geladen werden. Dies reduziert die wahrgenommene Ladezeit bei umfangreichen Berichten erheblich.

---

## Version 4.4.x

### 4.4.5 (10.08.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Choroplethenkarte-Legende:
{: .no_toc }
Ein fehlerhafter unbegrenzter Legendeneintrag in Choroplethenkarten wurde behoben, der auftrat, wenn keine negativen Werte im Datensatz vorhanden waren.

##### Zeitreihen-Berichte:
{: .no_toc }
Inkonsistente Darstellungen in Zeitreihendiagrammen, die bei nicht chronologisch sortierten Zeitstempeln auftreten konnten, wurden korrigiert.

#### Änderungen
{: .no_toc }

##### Zeitreihen- und Boxplot-Diagramme im Berichtswesen:
{: .no_toc }
Die Übersichtsdiagramme für Zeitreihen und Boxplots in Berichten wurden verbessert. Standardmäßig werden nun maximal 5 Flächen pro Übersichtsdiagramm angezeigt, um die Lesbarkeit zu steigern.

### 4.4.4 (17.07.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Wertebereich-Filter:
{: .no_toc }
Fehlerbehebung bei der Filterung von Indikatorwerten: Wenn globale Indikatorgenauigkeit und indikatoren-spezifische Genauigkeit unterschiedlich eingestellt waren, wurden Werte nicht korrekt gefiltert.

---

### 4.4.3 (05.06.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Filter-Konfiguration:
{: .no_toc }
Übernahme der Filter-Sichtbarkeitskonfiguration aus dem 5.x-Zweig für Nutzer der 4.4er Wartungslinie.

#### Fehlerbehebungen
{: .no_toc }

##### Metadaten-Fix:
{: .no_toc }
Behebung redundanter Metadaten-Abrufe zur Vermeidung von Fehlern bei globalen Filtern.

---

### 4.4.2 (29.05.2026)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Sichtbarkeit:
{: .no_toc }
Der Bereich Filter-Einstellungen ist nun auch für Administratoren von Ressourcen verfügbar. Technisches Release zur Synchronisation interner Metadaten und Versions-Templates.

---

### 4.4.0 & 4.4.1 (15.05.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Feature-Backports:
{: .no_toc }
Integration der Performance-Optimierungen für das Berichtswesen (asynchrone Generierung von Geodaten-Features) in die stabile 4.4.x-Linie.

#### Fehlerbehebungen
{: .no_toc }

##### Radar-Diagramme:
{: .no_toc }
Konsistente Interaktions-Fixes für komplexe Diagramm-Typen beim Abwählen von Objekten.

---

## Version 4.3.x

### 4.3.6 (20.04.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Raumfilter-Logik:
{: .no_toc }
Verfeinerung der räumlichen Selektionsalgorithmen und Behebung von Kantenfällen bei der Filterung komplexer Geometrien.

---

### 4.3.3 - 4.3.5 (24.03.2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Processes API Integration:
{: .no_toc }
Berechnungs-Skripte können nun als Prozesse aus einer laufenden Processes API-Instanz ausgewählt werden. Die Skriptverwaltung wurde um eine Job-Tabelle zur Überwachung laufender und abgeschlossener Berechnungen erweitert. Skripte lassen sich direkt über den `/schedule`-Endpunkt einplanen.

##### Klassifizierung:
{: .no_toc }
Verbesserungen der Jenks-Klassifizierungsmethode und Behebung fehlerhafter Klassifizierungseinstellungen für spezielle Datensituationen.

#### Fehlerbehebungen
{: .no_toc }

##### Skriptverwaltung:
{: .no_toc }
Mehrere Fehlerbehebungen in der Skriptverwaltung, bei Indikator- und Georessourcen-Selektionen sowie bei der Prozess-API-Kommunikation.

#### Änderungen
{: .no_toc }

##### Bereinigung:
{: .no_toc }
Veraltete JavaScript-Skript-Ressourcen wurden entfernt. Die Skript-Vorschau wurde zugunsten der neuen Job-basierten Ausführung abgelöst.

---

### 4.3.2 (12.01.2026)
{: .no_toc }

#### Fehlerbehebungen
{: .no_toc }

##### Batch-Aktualisierung:
{: .no_toc }
Fehlerbehebung bei der Batch-Aktualisierung von Indikatoren in Kombination mit den neuen Aggregationsoptionen der Importer API (Aggregationen werden bei Batch-Updates aktuell noch nicht unterstützt).

---

### 4.3.0 - 4.3.1 (11.12.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Datenaggregation beim Import:
{: .no_toc }
Beim Datenimport können Indikatordaten automatisch für höhere Raumebenen über Referenzspalten aggregiert werden. Unterstützte Aggregationsfunktionen: Summe, Anzahl, Mittelwert, Median, Minimum, Maximum.

#### Fehlerbehebungen
{: .no_toc }

##### Raumebenen-Ebenensteuerung:
{: .no_toc }
Behebung von doppelten Einträgen für Raumebenen als Grenzlinien-Layer in der Ebenensteuerung.

---

## Version 4.2.x

### 4.2.0 - 4.2.1 (09.09.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Backport 3.4.x-Funktionen:
{: .no_toc }
Integration der Funktionen aus der 3.4.x-Linie (aktive Filter-Banner, Raumfilter für Georessourcen, konfigurierbares Reporting mit PPTX-Export, Kartenprojektionen in Diagrammen) in die mandantenfähige 4.x-Linie.

#### Fehlerbehebungen
{: .no_toc }

##### Bilanzierungsanzeige:
{: .no_toc }
Korrektur der Darstellung für Indikatoren mit ausschließlich positiven oder negativen Werten in Zwei-Zeitpunkt-Bilanzierungsszenarien.

---

## Version 4.1.x

### 4.1.0 - 4.1.1 (27.05.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Backport 3.2.x & 3.3.x-Funktionen:
{: .no_toc }
Integration der Funktionen aus der 3.2.x- und 3.3.x-Linie in die mandantenfähige 4.x-Linie, darunter das globale Filter-System, Nutzerfavoriten, Farbthemen und das überarbeitete Filter-Modal.

##### Barrierefreiheit:
{: .no_toc }
Verbesserte Unterstützung für assistierende Technologien und Tastaturnavigation für komplexe UI-Widgets. Favicon hinzugefügt.

---

## Version 4.0.x

### 4.0.0 (Beta-Phase)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Mandantenfähigkeit (Multi-Tenant):
{: .no_toc }
Grundlegende Architekturumstellung auf ein mandantenorientiertes Benutzer- und Rechtesystem. Mehrere unabhängige Mandanten können innerhalb einer KomMonitor-Instanz mit getrennter Nutzerverwaltung und eigenen Ressourcen betrieben werden. Hierarchische Mandanten- und Untergruppen mit flexibler Verschachtelung, gruppen-spezifische Datenzugriffskontrolle und Keycloak-Integration für vereinfachte Nutzergruppen-Zuweisung.

##### Berechtigungskonzept:
{: .no_toc }
Neues Benutzermenü auf Basis eines granularen Berechtigungsmodells mit Synchronisation von Benutzergruppen. Explizite Datensatz-Eigentümerschaft mit gruppenbasierten Zugriffskontrollen und neuem öffentlichen Veröffentlichungs-Schalter.

##### Tabellen-Ansicht:
{: .no_toc }
Performantes Gitter-Layout für Ressourcen-Tabellen für flüssiges Scrollen auch bei großen Datenmengen.

#### Fehlerbehebungen
{: .no_toc }

##### Datenintegrität:
{: .no_toc }
Verbesserte Handhabung von leeren Werten und fehlenden Datenpunkten in Berechnungs-Skripten.

---

## Version 3.4.x

### 3.4.0 - 3.4.3 (März 2026)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Aktive Filter-Banner:
{: .no_toc }
Permanente visuelle Hinweise für aktive Anzeigefilter und den Bilanzierungsmodus, sodass Nutzerinnen und Nutzer stets erkennen, ob ein Filter aktiv ist.

##### Raumfilter für Georessourcen:
{: .no_toc }
Der räumliche Filter greift nun auch auf Punkte, Linien und Polygone an. Der Download ermöglicht wahlweise den gesamten oder nur den gefilterten Datensatz.

##### Konfigurierbares Reporting:
{: .no_toc }
Auswahl der Hintergrundkarte für Berichte, Karten-Screenshot-Caching pro Raumebene, selektives Ausblenden von Berichtsabschnitten und PowerPoint-Export (PPTX).

##### Zahlenformatierung:
{: .no_toc }
Konsistente Darstellung formatierter Zahlen (Tausender-Trennzeichen, Dezimaltrennzeichen) in Filter-Komponenten.

#### Fehlerbehebungen
{: .no_toc }

##### Klassifizierung:
{: .no_toc }
Optimierte Farbpaletten und Klasseneinteilung für Sonderfälle (weniger als 5 eindeutige Werte, Bilanzierung, Schwellenwert-Klassifizierung). Automatische Klassen-Reduktion bei Jenks und Quantil wenn eindeutige Werte die Klassenanzahl unterschreiten.

##### Messwerkzeug:
{: .no_toc }
Kartenverschiebungs-Fehler beim Klicken wurde behoben.

---

## Version 3.3.x

### 3.3.0 (05.05.2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Design & Theming:
{: .no_toc }
Einführung von Farbthemen für alle Komponenten und Unterstützung benutzerdefinierter Farbschemata. Dezimalzahlen werden nun einheitlich mit Komma als Dezimaltrennzeichen und Punkt als Tausendertrennzeichen dargestellt, mit indikatoren-spezifischer Genauigkeitskonfiguration.

#### Änderungen
{: .no_toc }

##### Begrifflichkeiten:
{: .no_toc }
Standardisierte Terminologie (z. B. „Raumebene", „Raumeinheit", „Feature") für eine konsistentere Benutzeroberfläche.

---

## Version 3.2.x

### 3.2.0 - 3.2.1 (Januar - Februar 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Globale Filter:
{: .no_toc }
Der Web-Client unterstützt nun aktive globale Filter für eingeschränktes Laden von Indikatoren und Georessourcen. Filter-Konfigurationen können in den allgemeinen Einstellungen angelegt und bearbeitet werden.

##### Favoriten:
{: .no_toc }
Angemeldete Nutzerinnen und Nutzer können Indikatoren, Georessourcen und Themen als Favoriten markieren und über einen dedizierten Reiter im Themenbaum schnell aufrufen.

#### Änderungen
{: .no_toc }

##### Zugriffsrechte bei Batch-Updates:
{: .no_toc }
Bei Batch-Updates und skriptbasierten Berechnungen werden Zugriffsrechte für neu verknüpfte Raumeinheiten aus den Indikator-Metadaten übernommen.

---

## Version 3.1.x

### 3.1.0 - 3.1.8 (August 2024 - Januar 2025)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Konfigurierbarkeit:
{: .no_toc }
Neue Parameter für die Anzeige von Mittelwerten in Legenden und Diagrammen, Unterstützung für ColorBrewer-Divergenzpaletten, CSV-Export kompatibel mit Excel-Format sowie erweitertes Widget-Control für zusätzliche HTML-Elemente.

#### Fehlerbehebungen
{: .no_toc }

##### Diagramm-Referenzen:
{: .no_toc }
Neue Referenzwerte für Ranking-Diagramme zur Korrektur von Fehlern in Zeitreihen-Berichten. Korrekte Behandlung von Leer-Werten in Berechnungs-Skripten (Summe, Quotient, Prozent, Promille, Subtraktion).

##### Keycloak-Unterstützung:
{: .no_toc }
Aktualisierte Keycloak-JS-Bibliothek für Kompatibilität mit Keycloak-Versionen > 25.0.

---

## Version 3.0.x

### 3.0.0 - 3.0.5 (Juni - Juli 2024)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Erreichbarkeitsanalysen:
{: .no_toc }
Integration von Erreichbarkeits-Zonen direkt in die Hauptkarte, szenario-basierte Erreichbarkeitsanalyse mit Indikatorstatistik-Verschneidung für Versorgungsanalysen sowie spontaner Geo-/Adressdaten-Import (CSV mit Geocoding über OpenStreetMap/Nominatim; GeoJSON/ESRI Shapefile).

##### Metadaten-Tab:
{: .no_toc }
Umstrukturierte Legende: Metadaten, Klassifizierungsoptionen und verknüpfte Ressourcen befinden sich nun in eigenen Reitern.

##### Regionale Referenzwerte:
{: .no_toc }
Neue Benutzeroberfläche für den Vergleich mit regionalen Durchschnittswerten (Gesamtsumme, Mittelwert, nicht-zuordenbar) in Zeitreihen.

#### Änderungen
{: .no_toc }

##### Technik-Update:
{: .no_toc }
Modernisierung der Basis-Technologien (Leaflet, ag-Grid, weitere Bibliotheken) für eine zukunftssichere Anwendung.

---

## Version 2.2.x

### 2.2.0 - 2.2.2 (Januar 2024)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### OGC API – Features:
{: .no_toc }
Datenimport für Raumeinheiten, Georessourcen und Indikatoren unterstützt nun den OGC API – Features-Standard (setzt Importer API ab v3.2.0 voraus).

#### Fehlerbehebungen
{: .no_toc }

##### Stabilität:
{: .no_toc }
Fehlerbehebungen beim Löschen einzelner Georessourcen, bei partiellen Raumebenen-Updates und bei der Vergabe von Publisher-Rollen.

---

## Version 2.1.x

### 2.1.0 - 2.1.17 (August 2023 - Dezember 2023)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Rollenmanagement:
{: .no_toc }
Umstellung der Berechtigungsverwaltung auf ein tabellarisches RBAC-Grid mit Checkboxen für lesen, bearbeiten und löschen je Datensatz und Organisationseinheit.

##### Navigation:
{: .no_toc }
Klickbare Fortschrittsbalken für direktes Springen zwischen Verwaltungsmenü-Unterabschnitten.

##### Reporting:
{: .no_toc }
Template-basiertes Reporting mit konfigurierbarer Metadaten- und Indikatordaten-Befüllung; Isochronen-Generierung um Georessourcen in Berichten.

#### Fehlerbehebungen
{: .no_toc }

##### Skripting-Logik:
{: .no_toc }
Korrekte Behandlung von fehlenden Werten in Berechnungs-Skripten (Quotient, Prozent, Promille, Multiplikation, Division) sowie Optimierung mathematischer Grundlagen für Diagramme.

---

## Version 2.0.x

### 2.0.0 - 2.0.1 (Juli 2022)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Rechteverwaltung:
{: .no_toc }
Grundlegende Erweiterung des Rechtesystems mit vier Rollen pro Organisation (Betrachter, Bearbeiter, Herausgeber, Ersteller). Nutzerverwaltung erfolgt nun vollständig über Keycloak. Alle Backend-Dienste sind Keycloak-gesichert.

##### Erreichbarkeits-Analysen (Beta):
{: .no_toc }
Erste Beta-Phase für Erreichbarkeits-Zonen, POI-Analysen und Puffer-Zonen. Geocoding-Prototyp für adressbasierte POI-Imports über OpenStreetMap/Nominatim.

---

## Version 1.7.x

### 1.7.0 (Februar 2022)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### ZIP-Export:
{: .no_toc }
Funktion zum Herunterladen von Indikatordaten als Archiv inklusive Metadaten.

---

## Version 1.6.x

### 1.6.0 (Dezember 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Skriptverwaltung:
{: .no_toc }
Erweiterungen in der administrativen Verwaltung von Berechnungs-Skripten.

#### Änderungen
{: .no_toc }

##### Metadaten-Caching:
{: .no_toc }
Implementierung einer Zwischenspeicherung für Metadaten zur Beschleunigung der Anzeige.

---

## Version 1.5.x

### 1.5.0 (November 2021)
{: .no_toc }

#### Änderungen
{: .no_toc }

##### Job-Monitoring:
{: .no_toc }
Verbesserte Übersicht laufender Hintergrundprozesse mit Statusanzeigen.

---

## Version 1.4.x

### 1.4.0 (September 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Suche & Filter:
{: .no_toc }
Einführung einer globalen Suchfunktion für alle Datentabellen.

---

## Version 1.0.x - 1.3.x

### 1.0.0 - 1.3.0 (Mai 2021 - August 2021)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Geführte Tour:
{: .no_toc }
Einführung einer interaktiven Einführung für neue Nutzerinnen und Nutzer.

#### Änderungen
{: .no_toc }

##### Tabellen-Migration:
{: .no_toc }
Umstellung der zentralen Übersichts-Tabellen auf ag-Grid für verbesserte Performance bei großen Datenmengen.

---

## Version 0.5.x

### Initial-Phase (Juni 2019)
{: .no_toc }

#### Neue Features
{: .no_toc }

##### Mapping-Grundlagen:
{: .no_toc }
Erster Prototyp der Karten-Engine (Leaflet-Integration) mit Fokus auf dynamischem Styling von Geodaten.
