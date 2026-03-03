# Praxisvorlage: Szenario B – Strikte Trennung (N+1 Mandanten)
## Autarke Datenhaltung für Kreis und Kommunen

[zurück zur Übersicht](./index.md)

Dieses Schema beschreibt die Umsetzung in einem Kreis, in dem sowohl die Kreisverwaltung als auch jede einzelne Kommune völlig eigenständig und abgeschottet voneinander ihre Sozialplanung betreiben.

---

## 1. Die Organisationsstruktur
In diesem Szenario wird für jede Kommune und für die Kreisverwaltung jeweils ein **eigener, separater Mandant** (Wurzelknoten) eingerichtet. Es besteht keine hierarchische Verbindung zwischen den Mandanten.

* **Mandant 1: Kreisverwaltung (Sozialamt)** (isMandant = EIN)
* **Mandant 2: Stadt A (Jugendamt/Sozialplanung)** (isMandant = EIN)
* **Mandant 3: Gemeinde B (Sozialwesen)** (isMandant = EIN)
* **Mandant 4: Stadt C (Sozialplanung)** (isMandant = EIN)

---

## 2. Administrative Rollenverteilung
Die Trennung wird technisch dadurch erzwungen, dass Mandanten-Administratoren keine Rechte außerhalb ihres eigenen Mandanten besitzen.

| Akteur | Administrative Rolle | Befugnis im System |
| :--- | :--- | :--- |
| **IT-Dienstleister** | **kommonitor-creator** | Globaler System-Admin. Einzige Rolle, die alle Mandanten technisch betreuen kann. |
| **Kreis-Admin** | **client-*-creator** | Volle Admin-Rechte nur innerhalb des Kreis-Mandanten. |
| **Kommune A Admin** | **client-*-creator** | Volle Admin-Rechte nur innerhalb des Mandanten der Stadt A. |

---

## 3. Daten-Matrix: Absolute Isolation
In diesem Modell gibt es keinen Datenaustausch über das Usergruppen-Konzept zwischen den Mandanten. Datenredundanz wird zugunsten der Datensouveränität in Kauf genommen.

| Datensatz (Beispiel) | Mandant (Eigentümer) | Sichtbarkeit | Zugriff durch Dritte |
| :--- | :--- | :--- | :--- |
| **Altersarmut Kreis** | Kreisverwaltung | Intern (isPublic = AUS) | Nur Kreis-Mitarbeiter |
| **Kinderarmut Stadt A** | Stadt A | Intern (isPublic = AUS) | Nur Stadt A-Mitarbeiter |
| **Sozialatlas Stadt C** | Stadt C | **Öffentlich** (isPublic = EIN) | Alle (Bürger & andere Mandanten) |

---

## 4. Implementierungs-Checkliste
1. [ ] **Mandanten-Setup**: Der IT-Dienstleister registriert für jede Kommune und den Kreis einen eigenen Mandanten mit aktiviertem Mandanten-Toggle.
2. [ ] **Zuweisung der Admins**: Pro Mandant wird mindestens ein lokaler Mandanten-Admin ernannt, der nur für seinen Bereich zuständig ist.
3. [ ] **Datenhoheit**: Jede Kommune lädt ihre eigenen Raumebenen (z. B. Sozialräume oder Quartiere) in ihren eigenen Mandanten hoch.
4. [ ] **Kein "kommonitor-creator" für Mandanten**: Um die Sperren nicht zu umgehen, darf die Rolle **kommonitor-creator** keinesfalls an kommunale oder kreiseigene Nutzer vergeben werden.
5. [ ] **Datenaustausch (Optional)**: Sollten Daten dennoch geteilt werden, erfolgt dies ausschließlich über die Aktivierung des **isPublic**-Flags (Open Data Prinzip). Ein interner Austausch zwischen geschützten Gruppen verschiedener Mandanten ist technisch ausgeschlossen.

---

## 5. Strategische Vorteile dieses Szenarios
* **Maximale Autonomie**: Jede Kommune entscheidet völlig frei über ihre Daten, Themenstrukturen und Nutzer.
* **Datenschutz-Garantie**: Es ist technisch unmöglich, dass ein Nutzer aus Kommune A versehentlich Zugriff auf interne Planungsdaten von Kommune B erhält.
* **Souveränität**: Die Kreisverwaltung hat keinen direkten Zugriff auf die (nicht-öffentlichen) Arbeitsdaten der Kommunen, was das Vertrauen in die Systemnutzung bei sensiblen Themen stärkt.