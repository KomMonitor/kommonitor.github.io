# Praxisvorlage: Hybrid-Modell „Zentrales Repository & Lokale Fachplanung“

[zurück zur Übersicht](./index.md)

Höchste Datensicherheit durch physische Trennung der Mandanten-Wurzelknoten.

---

## 1. Die Mandanten-Struktur
* **Mandant 1: Zentrale Datenplattform**: Öffentliche Basisindikatoren (Einwohner, SGB-II-Trend).
* **Mandant 2: Fachplanung Kreis**: Kreisinterne Berichte (nicht öffentlich).
* **Mandant 3: Fachplanung Kommune A**: Hochauflösende Detaildaten (z. B. auf Baublockebene).

---

## 2. Nutzer-Konfiguration (Doppel-Mitgliedschaft)
Nutzer können Mitglied in **1 bis n Gruppen** sein.
* **Beispiel Planer Kommune A**:
    * Mitgliedschaft in Gruppe „Kommune A“ (Mandant 3).
    * Mitgliedschaft in Gruppe „Leser Zentrale Daten“ (Mandant 1).
* **Ergebnis**: Der Planer sieht beide Datenbestände nahtlos nebeneinander im Web-Client.

---

## 3. Daten-Matrix & Freigaben
| Datensatz | Mandant (Eigentümer) | Status | Reichweite |
| :--- | :--- | :--- | :--- |
| **Basis-Indikatoren** | Zentrale Plattform | **isPublic = EIN** | Mandanten-übergreifend lesbar. |
| **Interne Analysen** | Fachplanung Kreis | **isPublic = AUS** | Streng isoliert im Kreis-Mandanten. |
| **Detailkarten** | Fachplanung Kommune A | **isPublic = AUS** | Streng isoliert; für Kreis-Admin unsichtbar. |

---

## 4. Implementierungs-Checkliste
1. [ ] **Mandanten-Setup**: Erstellung von mindestens zwei unabhängigen Mandanten-Wurzelknoten.
2. [ ] **Daten-Isolation**: Hochsensible Daten werden nur im kommunalen Mandanten hochgeladen.
3. [ ] **Zentral-Repository**: Kreis aktiviert **isPublic** für Vergleichsdaten im zentralen Mandanten.
4. [ ] **Keycloak-Zuweisung**: Planer manuell allen benötigten Gruppen über Mandantengrenzen hinweg zuweisen.
5. [ ] **Explizite Rechte**: Jede neue Untergruppe benötigt eine eigene manuelle Ressourcen-Freigabe.