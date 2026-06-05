---
layout: default
title: Data Management
parent: Release Info
nav_order: 3
---

# Release Info (Data Management)
{: .no_toc }

Release Informationen für die KomMonitor Data Management API
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

Hier finden Sie eine Übersicht der wichtigsten Neuerungen, Datenbank-Updates und Sicherheitsverbesserungen der KomMonitor Data Management API ab Version 1.0.0. Diese Komponente bildet das Herzstück der Datenhaltung und Rechteverwaltung im KomMonitor-Ökosystem.

---

## Version 5.x
### Highlights & API-Änderungen
{: .no_toc }
*   **Web-Service Management:** Einführung neuer Endpunkte zur Verwaltung von externen Web-Services, inklusive Favoriten-Management, Filterung und differenzierter Rechtevergabe.
*   **Qualitative Klassifizierung:** Unterstützung für qualitative Klassifizierungsmethoden und Refactoring der JPA-Entitäten für Standard-Klassifizierungselemente.
*   **Export-Optionen:** Implementierung von GeoPackage-Export-Endpunkten für Indikatoren und Georessourcen zur besseren Interoperabilität.
*   **Themen-Steuerung:** Neue Endpunkte zur Festlegung der Anzeige-Reihenfolge von Themen (Topics) und erweiterte Filterstrategien.

### Datenbank & Technik
{: .no_toc }
*   **Schema-Erweiterung:** Integration neuer Tabellen zur Unterstützung der Web-Service-Verwaltung.
*   **Datenintegrität:** Einführung von Unique-Constraints für Keycloak-IDs in der `userinfo`-Tabelle und Ergänzung einer `precision`-Spalte für Indikatoren via Liquibase.
*   **Performance:** Refactoring der Feature-Abruflogik aus der PostgreSQL/PostGIS Datenbank zur Steigerung der Effizienz bei großen Datenmengen.

---

## Version 4.x
### Zugriffssteuerung & Sicherheit
{: .no_toc }
*   **Role-Based Access Control (RBAC):** Einführung einer gruppenbasierten Zugriffskontrolle und feingranularer Administrationsberechtigungen.
*   **Keycloak-Synchronisation:** Nahtlose Integration der Synchronisation von Keycloak-Gruppen und -Rollen direkt in die API.
*   **Berechtigungsevaluation:** Implementierung einer automatisierten Prüfung von Rechten beim Aktualisieren oder Löschen von Organisationseinheiten.

### API & Datenmodell
{: .no_toc }
*   **Erweiterte Nutzerinfo:** Endpunkte zur Verwaltung zusätzlicher Benutzerinformationen und Rollenzuweisungen.
*   **Filter-Endpunkte:** Neue Filter-Möglichkeiten für Indikatoren und Georessourcen innerhalb der OpenAPI-Spezifikation (OAS).
*   **Geometrie-Optimierung:** Implementierung des `TopologyPreservingSimplifier` zur Reduzierung der Geometrie-Komplexität und Senkung der Koordinaten-Präzision für Web-Optimierung.

---

## Version 3.x
### Framework & Migration
{: .no_toc }
*   **Spring Boot 3:** Vollständige Migration auf Spring Boot 3 und Springdoc (Jakarta Persistence) für eine zukunftssichere Basis.
*   **Sicherheit:** Einführung der Spring Security Konfiguration mit einem dedizierten `AuthenticationProvider` für JWT-Tokens.
*   **Public Endpoints:** Implementierung öffentlicher Endpunkte für Georessourcen und Indikatoren mit spezifischen Request-Regeln.

### Funktionalität & Performance
{: .no_toc }
*   **Regionale Referenzwerte:** Unterstützung für regionale Durchschnitts- und Vergleichswerte direkt im Datenmodell.
*   **Raumeinheiten-Outlines:** Funktionalität zur Bereitstellung von Umringen für Raumeinheiten.
*   **Optimierung:** Aktivierung der GZIP-Komprimierung für alle API-Antworten und Optimierung des Hibernate-Dialekts für PostgreSQL.

---

## Version 2.x
### Datenmanagement & CRUD
{: .no_toc }
*   **Einzeldatensatz-Management:** Implementierung vollständiger CRUD-Operationen (Create, Read, Update, Delete) für einzelne Datensätze von Georessourcen, Raumeinheiten und Indikatoren.
*   **Hierarchie-Konsistenz:** Unterstützung beim Umbenennen von Raumeinheiten unter automatischer Beibehaltung der hierarchischen Konsistenz.
*   **Geometrie-Optionen:** Neue Endpunkte zum Abruf von Georessourcen-Eigenschaften ohne Geometrie-Daten zur Bandbreiteneinsparung.

### Sicherheit & Speichermanagement
{: .no_toc }
*   **Rechte-Modell v2:** Implementierung eines neuen Zugriffskontrollmodells basierend auf Organisationseinheiten und granularen Berechtigungsstufen.
*   **Verschlüsselung:** Einführung der AES-CBC Verschlüsselung für sensible Antwort-Objekte.
*   **Datenbank-Pflege:** Automatische Ausführung von "VACUUM FULL" nach größeren Löschvorgängen zur Freigabe von Speicherplatz auf dem Host-System.

---

## Version 1.x
### Kern-Funktionalitäten
{: .no_toc }
*   **Initiales Datenmodell:** Erstimplementierung der Kernobjekte: Themen, Georessourcen, Raumeinheiten und Indikatoren.
*   **OGC-Integration:** Verwaltung von WMS, WFS und WCS Diensten inklusive tiefer Integration mit dem GeoServer.
*   **Berechnungs-Engine:** Bereitstellung der Scripting-API zur automatisierten Berechnung von Indikatoren.

### Geodaten-Verarbeitung
{: .no_toc }
*   **PostGIS-Integration:** Implementierung der Integration räumlicher Features von GeoJSON in PostGIS.
*   **Visualisierung:** Unterstützung für Styled Layer Descriptors (SLD) zur serverseitigen Visualisierung von Indikatoren.
*   **Import-Optimierung:** Effizienzsteigerung beim Datenimport durch Just-in-Time Abfragen von Gültigkeitszeiträumen.
