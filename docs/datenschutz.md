# Handreichung: Datenschutz und Umgang mit personenbezogenen Daten in KomMonitor

## Einführung
Der Schutz personenbezogener Daten und die Einhaltung der DSGVO sind zentrale Säulen beim Betrieb von Software in der kommunalen Verwaltung. **KomMonitor** ist als Werkzeug für das kommunale Monitoring (z. B. in der Sozialplanung) darauf ausgelegt, das Prinzip der **Datensparsamkeit** konsequent umzusetzen.

Dieses Dokument dient als Orientierungshilfe für Fachplaner, IT-Abteilungen, Datenschutzbeauftragte und Personalräte. Es erläutert, wie KomMonitor mit Nutzerdaten umgeht, welche Rolle die Identitätsmanagement-Komponente **Keycloak** spielt und wie die Protokollierung (Logging) ausgestaltet ist.

---

## FAQ – Datenschutz & Datensicherheit

### 1. Nutzerverwaltung und Keycloak

**Welche personenbezogenen Daten der User werden in Keycloak gespeichert?**
Keycloak fungiert als Single Sign-On (SSO) Lösung. Folgende Daten werden verarbeitet:
* **Stammdaten:** Benutzername (Login), interne Keycloak-ID (UUID), Passwort (gehasht).
* **Optionale Klardaten:** E-Mail-Adresse, Vorname, Nachname. Diese werden oft von der Fachadministration (z. B. Sozialplanung) gepflegt, um Ansprechpartner identifizieren und kontaktieren zu können.
* **Berechtigungen:** Zuweisung zu Gruppen/Rollen (z. B. "Fachplaner_Gesundheitsamt").
* **Metadaten:** Zeitpunkt der Account-Erstellung sowie der letzte Login.

**Wer hat Zugriff auf die Nutzerdaten in Keycloak?**
Der Zugriff ist streng auf Administratoren beschränkt:
* **Server-Admin (IT-Dienstleister):** Hat Zugriff auf die Datenbankebene zur technischen Wartung.
* **Fachadministrator (z. B. Sozialplanung):** Benötigt Zugriff auf die Keycloak-Oberfläche, um Accounts zu verwalten und Rechte zuzuweisen.
* **Einfache Fachnutzer:** Haben **keinen** Einblick in die Daten anderer Nutzer. Sie nutzen Keycloak lediglich als Login-Maske für KomMonitor.

**Kann eine bestehende Keycloak-Instanz des IT-Dienstleisters genutzt werden?**
**Ja.** Keycloak unterstützt "Realms" (Mandanten). KomMonitor kann als eigener Client in einer bestehenden Instanz betrieben werden. Auch eine Anbindung an ein städtisches **LDAP / Active Directory** ist möglich, um bestehende Dienst-Accounts zu synchronisieren.

---

### 2. Datenspeicherung und Fachdaten

**Speichert KomMonitor personenbezogene Daten der Anwender?**
KomMonitor nutzt zur Personalisierung (z. B. Favoriten für Indikatoren oder Themenbäume) lediglich die **technische Keycloak-ID (UUID)**. Der Fachdienst selbst speichert keine Klarnamen. Eine Zuordnung erfolgt nur temporär während einer aktiven Sitzung.

**Werden Veränderungen an Fachdaten mit User-Namen protokolliert?**
**Nein.** KomMonitor speichert keine "Verfahrensdaten" im Sinne einer Änderungshistorie mit Bezug auf Klarnamen. Das System ist auf die Bereitstellung und Analyse von Daten optimiert, nicht auf die Überwachung von Bearbeitungsschritten einzelner Personen.

---

### 3. Protokollierung (Logging) und Überwachung

**Was wird in den Protokolldateien gespeichert?**
In den Fachdiensten von KomMonitor werden lediglich technische Autorisierungsvorgänge geloggt. Dabei tauchen nur IDs auf:
`access for 78222505-2f08... to entity b711c7bb... authorized? True`
Nur der Server-Admin kann diese IDs theoretisch über Keycloak einer Person zuordnen. Dies ist jedoch zweckgebunden (z. B. Fehlersuche) und durch den Vertrag zur Auftragsverarbeitung (AVV) geregelt.

**Wie steht es um das Logging von User-Aktionen in Keycloak?**
* Keycloak kann theoretisch eine Vielzahl von Events loggen (Login-Erfolge, Passwortänderungen, Admin-Aktionen).
* **Standardkonfiguration:** Für KomMonitor-Realms ist dieses detaillierte User-Event-Logging **standardmäßig deaktiviert**.
* **Konfigurierbarkeit:** Die IT kann das Logging bei Bedarf (z. B. zur Revisionssicherheit oder Gefahrenabwehr) gezielt aktivieren. Ohne diese explizite Aktivierung findet keine verhaltensbezogene Protokollierung statt.

**Wann werden die Protokolle gelöscht?**
Das Logging erfolgt standardmäßig über **Docker-Container**. 
* Die Logs sind an die **Lebensdauer des Containers** gebunden. Wird ein Container neu gestartet (z. B. bei Wartungsarbeiten oder Updates), werden die alten Logs gelöscht.
* Die Protokolle werden **nicht** bei jedem einfachen Schließen des Browsers durch einen User gelöscht, sondern verbleiben im flüchtigen Speicher des Servers, bis der Dienst neu gestartet wird.

> **Referenz:** [Keycloak Dokumentation - Auditing & Events](https://www.keycloak.org/docs/latest/server_admin/#_events) | [Docker Logging Driver Configuration](https://docs.docker.com/engine/logging/configure/)

---

### 4. Gegenüberstellung

Um die Anforderungen typischer Rahmen-Dienstvereinbarungen (Rahmen-DV) zu erfüllen, unterscheidet KomMonitor strikt zwischen notwendigen Systemdaten und (nicht vorhandenen) verhaltensbezogenen Verfahrensdaten.

| Protokolltyp | Inhalt / Beispiel | Zweck | Speicherdauer |
| :--- | :--- | :--- | :--- |
| **Systemprotokolldaten** | Docker-Logs, Fehlermeldungen (Stacktraces). | Technischer Betrieb & Stabilität. | Bis zum Container-Neustart. |
| **Authentifizierungs-Events** | Login-Zeitpunkt, IP-Adresse, Fehlversuche. | IT-Sicherheit & Forensik. | **Deaktiviert** (Default). |
| **Zugriffsprotokolle** | `User-ID [UUID]` hat Zugriff auf `Indikator-ID`. | Nachweis der Autorisierung. | Bis zum Container-Neustart. |
| **Verfahrensdaten** | "Wer hat welchen Wert wann geändert?" | Leistungs- oder Verhaltenskontrolle. | **Wird nicht erhoben.** |

---

### Anhang: kompakter Textbaustein

*Kategorien personenbezogener Daten:*
* **Identifikationsdaten:** Benutzername, Vorname, Nachname, E-Mail-Adresse (in Keycloak).
* **Technische Daten:** IP-Adresse (kurzzeitig zur Sitzungssteuerung), interne technische User-ID (UUID), Zeitstempel des letzten Logins.
* **Authentifizierungsdaten:** Passwörter (ausschließlich gehasht in Keycloak).

*Regelfristen für die Löschung:*
* **Nutzerdaten:** Werden bei Ausscheiden aus der Organisation oder bei Widerruf der Zugriffsberechtigung in Keycloak gelöscht.
* **Protokolldaten:** Systemlogs in Docker-Containern werden standardmäßig bei jedem Neustart der Dienste automatisiert gelöscht.

*Technische und organisatorische Maßnahmen (TOMs):*
* **Trennungskontrolle:** Strikte Trennung von Identitätsmanagement (Keycloak) und Fachanwendung (KomMonitor).
* **Zugriffskontrolle:** Passwortgeschützter Zugang, differenziertes Rollenkonzept, HTTPS/TLS-Verschlüsselung.
