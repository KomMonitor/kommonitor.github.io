# Praxisvorlage: Interkommunales Monitoring „Sozialplanung & Armut“

[zurück zur Übersicht](./index.md)

Dieses Schema beschreibt die Umsetzung einer kooperativen Datenhaltung zwischen einem Kreis und seinen angehörigen Kommunen am Beispiel Kinderarmut.

---

## 1. Die Organisationsstruktur
* **Mandant: Gemeinsame Sozialplanung Kreis X** (Wurzelknoten)
    * **Untergruppe: Kreis-Sozialamt (Projektleitung)**
    * **Untergruppe: Kommune A – Jugendamt**
    * **Untergruppe: Kommune B – Jugendamt**
    * **Untergruppe: Kommune C – Jugendamt**

---

## 2. Administrative Rollenverteilung
| Akteur | Administrative Rolle | Befugnis in der Praxis |
| :--- | :--- | :--- |
| **Kreis-Administrator** | **client-user-creator** | Verwaltet Nutzer für den gesamten Mandanten und alle Kommunen. |
| **Jugendamt-Leitung A** | **unit-user-creator** | Verwaltet nur die Nutzer der eigenen Gruppe „Kommune A“. |
| **Kreis-Datenplaner** | **client-resources-creator** | Darf Indikatoren für den gesamten Projekt-Mandanten anlegen. |

---

## 3. Daten-Matrix: Beispiel „Kinderarmut“
* **Eigentümer (Ownership):** Kreis-Sozialamt.
* **Öffentliche Lesefreigabe (isPublic):** Deaktiviert.

**Explizite Zugriffsrechte im Freigabe-Dialog:**
| Ziel-Gruppe | Lese-Recht | Editier-Recht | Zweck |
| :--- | :--- | :--- | :--- |
| **Kommune A** | **Ja** | Nein | Nutzung der Kreisdaten als Vergleichswerte. |
| **Kommune B** | **Ja** | **Ja** | Ergänzung eigener lokaler Zeitreihen. |
| **Kommune C** | **Ja** | Nein | Information der Gremien. |

---

## 4. Implementierungs-Checkliste
1. [ ] **Mandant erstellen**: Organisationseinheit mit Mandanten-Toggle registrieren.
2. [ ] **Hierarchie anlegen**: Untergruppen für Jugendämter korrekt einhängen.
3. [ ] **Nutzer-Registrierung**: In Keycloak User sofort ihrer Fachgruppe zuweisen.
4. [ ] **Daten-Upload**: Kreis wählt sich selbst als Eigentümer (Ownership).
5. [ ] **Freigabe**: Leserechte für Kommunen A, B und C manuell im Dialog setzen.