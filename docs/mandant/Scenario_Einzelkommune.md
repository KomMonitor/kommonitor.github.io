# Praxisvorlage: Szenario A – Die „All-in-One“ Kommune
## Integrierte Sozialberichterstattung und interne Fachplanung

[zurück zur Übersicht](./index.md)

Dieses Schema beschreibt die Umsetzung in einer Stadtverwaltung, die KomMonitor sowohl für die Information der Bürger*innen als auch für die hochsensible interne Sozialplanung nutzt.

---

## 1. Die Organisationsstruktur
In einer Einzelkommune wird in der Regel nur ein Mandant benötigt. Die fachliche Trennung erfolgt über eine klare Hierarchie von Untergruppen.

* **Mandant: Stadt Musterstadt** (Wurzelknoten)
    * **Untergruppe: Amt für Statistik & Stadtforschung** (Fokus: Öffentliche Daten/Open Data)
    * **Untergruppe: Fachbereich Sozialplanung** (Fokus: Interne Quartiersanalyse)
    * **Untergruppe: Jugendhilfeplanung** (Fokus: Kleinräumige Bedarfsplanung)

---

## 2. Administrative Rollenverteilung
Die Verwaltung wird so aufgeteilt, dass das Statistikamt die Basisstruktur pflegt, während die Fachplaner die Hoheit über ihre sensiblen Daten behalten.

| Akteur | Administrative Rolle | Funktion im System |
| :--- | :--- | :--- |
| **Zentral-Admin (IT)** | **kommonitor-creator** | Erstellt den Mandanten und die Grundstruktur. |
| **Statistik-Leitung** | **client-resources-creator** | Pflegt offizielle Raumebenen (Bezirke) und veröffentlicht Open-Data-Indikatoren. |
| **Fachplaner Sozial** | **unit-resources-creator** | Verwaltet interne Indikatoren und kleinräumige Geodaten des eigenen Teams. |

---

## 3. Daten-Matrix: Öffentliche Transparenz vs. Interne Analyse
Der Schutz sensibler Daten erfolgt über die Wahl der Raumebene und den Status der öffentlichen Lesefreigabe.

| Datensatz (Indikator) | Raumebene | Sichtbarkeit | Eigentümer (Ownership) |
| :--- | :--- | :--- | :--- |
| **Arbeitslosenquote** | Stadtbezirk | **Öffentlich** (isPublic = EIN) | Amt für Statistik |
| **Altersstruktur** | Stadtteil | **Öffentlich** (isPublic = EIN) | Amt für Statistik |
| **SGB-II-Bezug (Detail)** | **Baublock** | **Intern** (isPublic = AUS) | Fachbereich Sozialplanung |
| **KITA-Plätze (Bedarf)** | **Wohnquartier** | **Intern** (isPublic = AUS) | Jugendhilfeplanung |

---

## 4. Implementierungs-Checkliste
1. [ ] **Mandant einrichten**: Der IT-Admin registriert die „Stadt Musterstadt“ mit aktiviertem Mandanten-Toggle.
2. [ ] **Öffentliche Ebenen bereitstellen**: Das Statistikamt lädt Raumebenen (Bezirke/Stadtteile) hoch und schaltet diese für anonyme Nutzer frei.
3. [ ] **Interne Ebenen isolieren**: Die Fachplanung lädt kleinräumige Ebenen (z. B. Baublöcke) hoch. Diese erhalten **keine** öffentliche Lesefreigabe.
4. [ ] **Datensatz-Eigentümerschaft**: Beim Upload sensibler Indikatoren (z. B. Kinderarmut) wählt die Fachplanung die eigene Gruppe als Eigentümer. Damit ist der Zugriff für andere Ämter zunächst gesperrt.
5. [ ] **Interne Kooperation**: Soll das Jugendamt die Daten der Sozialplanung lesen dürfen, muss die Sozialplanung dies im Freigabe-Dialog explizit für die Gruppe „Jugendhilfeplanung“ erlauben.

---

## 5. Besonderheit dieses Szenarios
Dieses Modell ermöglicht eine **Zwei-Ebenen-Strategie**:
* **Bürger-Service**: Transparente Sozialberichterstattung auf groben, datenschutzkonformen Ebenen.
* **Fachplanungs-Werkstatt**: Hochauflösende Analysen auf kleinsten Einheiten (Baublöcken), die nur für berechtigte Fachnutzer nach Login sichtbar sind.