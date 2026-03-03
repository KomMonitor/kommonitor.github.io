# Strategie-Leitfaden: KomMonitor Mandantenfähigkeit (2025/2026)

### Ein Ratgeber für die digitale Souveränität von Kommunen und Kreisen

[zurück zur Übersicht](./index.md)

---

## Inhaltsverzeichnis
- [Strategie-Leitfaden: KomMonitor Mandantenfähigkeit (2025/2026)](#strategie-leitfaden-kommonitor-mandantenfähigkeit-20252026)
    - [Ein Ratgeber für die digitale Souveränität von Kommunen und Kreisen](#ein-ratgeber-für-die-digitale-souveränität-von-kommunen-und-kreisen)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [1. Das Kernkonzept: "Vom Einzelschlüssel zum Gruppen-Zutritt"](#1-das-kernkonzept-vom-einzelschlüssel-zum-gruppen-zutritt)
  - [2. Die drei Säulen der Administration](#2-die-drei-säulen-der-administration)
  - [3. Das Datenmodell im Praxiskontext](#3-das-datenmodell-im-praxiskontext)
  - [4. Typische Use Cases und Szenarien](#4-typische-use-cases-und-szenarien)
  - [5. Praxis-Checklisten \& Anleitungen](#5-praxis-checklisten--anleitungen)
    - [5.1 Neuen Mandanten einrichten (Superadmin)](#51-neuen-mandanten-einrichten-superadmin)
    - [5.2 Internen Indikator (z. B. Altersarmut) anlegen](#52-internen-indikator-z-b-altersarmut-anlegen)
    - [5.3 Workflow: Vom internen Entwurf zur Veröffentlichung](#53-workflow-vom-internen-entwurf-zur-veröffentlichung)
    - [5.4 Anleitung: Zugriff für neue Teams einrichten (Die „Vererbungs-Falle“)](#54-anleitung-zugriff-für-neue-teams-einrichten-die-vererbungs-falle)
    - [5.5 Anleitung: Eigentümerschaft übertragen](#55-anleitung-eigentümerschaft-übertragen)
    - [5.6 Fehlerbehebung: „Ich sehe meine Daten nicht“](#56-fehlerbehebung-ich-sehe-meine-daten-nicht)
    - [5.7 Anleitung: Zusammenarbeit im Hybrid-Modell](#57-anleitung-zusammenarbeit-im-hybrid-modell)
  - [6. Aktuelle Limitationen \& Roadmap](#6-aktuelle-limitationen--roadmap)
  - [7. FAQ – Nach Themen strukturiert](#7-faq--nach-themen-strukturiert)
    - [Thema: Datenzugriff \& Sichtbarkeit](#thema-datenzugriff--sichtbarkeit)
    - [Thema: Technische Administration \& Synchronisation](#thema-technische-administration--synchronisation)
    - [Thema: Rollen \& Verantwortlichkeiten](#thema-rollen--verantwortlichkeiten)
    - [Thema: Zusammenarbeit \& Mandantengrenzen](#thema-zusammenarbeit--mandantengrenzen)
  - [8. Praxis-Musterschemata](#8-praxis-musterschemata)
    - [8.1 Szenario A: Die „All-in-One“ Kommune](#81-szenario-a-die-all-in-one-kommune)
    - [8.2 Szenario B: Strikte Trennung (N+1 Mandanten)](#82-szenario-b-strikte-trennung-n1-mandanten)
    - [8.3 Szenario C: Gemeinsame Sozialplanung](#83-szenario-c-gemeinsame-sozialplanung)
    - [8.4 Szenario D: Das Hybrid-Modell](#84-szenario-d-das-hybrid-modell)

---

## 1. Das Kernkonzept: "Vom Einzelschlüssel zum Gruppen-Zutritt"

Seit der Umstellung auf die neue Mandantenfähigkeit (***API >= 5.0.0***) (***CLIENT >= 4.0.0***) erfolgt der Zugriff nicht mehr über individuelle Rollenzuweisungen für jeden einzelnen Nutzer. 

* **Gruppenbasierte Rechte**: Nutzer erhalten ihre Befugnisse ausschließlich über die explizite Mitgliedschaft in Keycloak-Gruppen.
* **1:1 Zuordnung**: Jede Organisationseinheit in KomMonitor entspricht technisch exakt einer Gruppe in Keycloak.
* **Keine Hierarchie-Automatik**: Zugriffsrechte auf Datensätze werden **nicht** automatisch an Untergruppen vererbt; jede Freigabe muss explizit für die jeweilige Gruppe erfolgen.
* **Gleiche Rechte im Team**: Innerhalb einer Gruppe besitzen alle Mitglieder dieselben Berechtigungen bezüglich Datensätzen und administrativer Aufgaben.
* **Eigentümerschaft**: Datensätze gehören niemals einer Einzelperson, sondern immer einer Organisationseinheit (Gruppe).

---

## 2. Die drei Säulen der Administration

Die Administration wurde von einer globalen Rolle auf feingranulare administrative Rollen erweitert, die über intuitive Masken gesteuert werden.

| Bereich | Fokus der Administration | Reichweite (Beispiele) |
| :--- | :--- | :--- |
| **Nutzer** | Wer darf ins System? | Administrieren von Nutzern für eine Gruppe und deren Untergruppen. |
| **Ressourcen** | Welche Daten liegen vor? | Verwalten von Georessourcen, Indikatoren und Raumeinheiten. |
| **Themen** | Katalogstruktur | Administrieren von Themenbäumen in KomMonitor. |

> **Wichtig**: Rollen mit dem Präfix **client-*** wirken auf die eigene Gruppe und alle Untergruppen. Rollen mit **unit-*** wirken ausschließlich auf die eigene Gruppe. Administratoren nutzen dazu KomMonitor-Oberflächen, um Rechte einer Gruppe genau zu kontrollieren. 

---

## 3. Das Datenmodell im Praxiskontext

Fachplaner steuern die Mandantenfähigkeit über einfache Menüs, während im Hintergrund technische Parameter die Trennung sicherstellen.

| Eigenschaft | Bedeutung für die Planung | Praxis-Beispiel |
| :--- | :--- | :--- |
| **isMandant** | Kennzeichnet eine Gruppe als eigenständigen Wurzelknoten ohne Obergruppe. | Ein Kreis legt für "Gemeinde A" einen Mandanten an. |
| **parentID** | Definiert die hierarchische Einordnung innerhalb eines Mandanten. | Das "Team Sozialplanung" wird unter dem "Sozialamt" aufgehängt. |
| **ownership** | Legt die verantwortliche Gruppe für einen Datensatz fest. | Nur das Jugendamt kann die eigenen Kita-Daten löschen oder verwalten. |
| **isPublic** | Schaltet Daten mandantenübergreifend für die Öffentlichkeit frei. | Spielplatzstandorte werden als öffentlich verfügbare Daten markiert. |

---

## 4. Typische Use Cases und Szenarien

* **Szenario A: Die autarke Kommune**: Eine Stadt nutzt KomMonitor intern. Ein Mandant wird als Wurzelknoten erstellt. Fachämter werden als Untergruppen abgebildet.
* **Szenario B: Der Kreis als Hoster**: Jede Kommune sowie die Kreisverwaltung agiert als eigenständiger Mandant. Es besteht eine strenge Abgrenzung; ein Mandant kann einen anderen weder einsehen noch verwalten.
* **Szenario C:Interkommunales kreisweites Monitoring mit gemeinsamer Datenhaltung**: In einem Kreis wird in einem Mandanten eine gemeinsame Datenhaltung eingerichtet. Useruntergruppen erlauben gezielete Datenfreigaben.
* **Szenario D: Die Kooperations-Cloud**: Ein gemeinsamer Mandant wird für übergreifende Basisdaten genutzt, während sensible Fachdaten in separaten Mandanten der Kommunen verbleiben.

---

## 5. Praxis-Checklisten & Anleitungen

### 5.1 Neuen Mandanten einrichten (Superadmin)
1. Anmeldung als globaler Admin mit der Rolle **kommonitor-creator**.
2. In der Gruppenverwaltung eine neue Organisationseinheit registrieren.
3. Den Toggle **"Mandant"** explizit aktivieren.
4. Über den Button "Rechte verwalten" der neuen Gruppe die administrative Selbstverwaltung übertragen.

### 5.2 Internen Indikator (z. B. Altersarmut) anlegen
1. Metadaten und ressourcenspezifische Informationen für den neuen Datensatz eintragen.
2. Die zuständige Fachgruppe als **Eigentümer** hinterlegen.
3. Den Schalter für die öffentliche Lesefreigabe deaktiviert lassen.
4. Im Schritt "Datensatz-Freigaben" Lese- oder Editierrechte explizit für Partner-Gruppen auswählen.

### 5.3 Workflow: Vom internen Entwurf zur Veröffentlichung
Fachplaner arbeiten oft über längere Zeiträume an Indikatoren, bevor diese für andere Ämter oder die Öffentlichkeit sichtbar sein dürfen.

* **Der Entwurfs-Status:** Beim Registrieren eines neuen Indikators wählen Sie Ihre eigene Fachgruppe als **Eigentümer-Organisationseinheit**  Nur Mitglieder dieser Gruppe (oder übergeordnete Ressourcen-Admins) können den Datensatz bearbeiten oder löschen.
* **Zugriffsschutz:** Stellen Sie sicher, dass der Schalter **„Öffentliche Lesefreigabe“** (`isPublic`) deaktiviert bleibt.
* **Interne Abstimmung:** Falls ein anderes Amt den Entwurf prüfen soll, vergeben Sie im Prozessschritt „Datensatz-Freigaben“ explizit ein **Leserecht** für die entsprechende Gruppe.
* **Go-Live:** Wenn der Datensatz final ist, bearbeiten Sie die Metadaten und aktivieren Sie die **öffentliche Lesefreigabe**. Erst jetzt ist der Indikator für anonyme Nutzer und andere Mandanten sichtbar.

### 5.4 Anleitung: Zugriff für neue Teams einrichten (Die „Vererbungs-Falle“)
Ein häufiger Stolperstein: Eine neue Untergruppe wird angelegt, sieht aber die bestehenden Daten der Abteilung nicht.

* **Das Problem:** In KomMonitor werden Zugriffsrechte auf Datensätze **nicht** automatisch an Untergruppen vererbt.
* **Die Lösung:** Ein Nutzer der `Eigentümer Gruppe` des Datensatzes muss den Zugriff manuell freischalten.
* **Vorgehensweise:**
    1.  Öffnen Sie die **Ressourcenverwaltung** und wählen Sie den Datensatz zum Editieren aus.
    2.  Navigieren Sie zum Bereich **„Datensatz-Freigaben“**.
    3.  Suchen Sie die neue Untergruppe in der Liste der Organisationseinheiten und aktivieren Sie das Häkchen für **„Lesen“**.
    4.  Speichern Sie die Änderungen. Erst jetzt haben Mitglieder des neuen Teams Zugriff.

### 5.5 Anleitung: Eigentümerschaft übertragen
Wenn die Zuständigkeit für einen Indikator (z. B. von der Statistik zur Fachplanung) wechselt, muss die Eigentümerschaft angepasst werden.

* **Bedeutung:** Nur die Eigentümer-Gruppe besitzt das exklusive Recht, einen Datensatz zu löschen sowie Rechte anderer Gruppen am Datensatz anzupassen.
* **Voraussetzung:** Der ausführende Nutzer muss Mitglied der aktuellen `Eigentümer Gruppe` sein.
* **Schritte:**
    1.  Öffnen Sie die Bearbeitungsmaske des Datensatzes.
    2.  Wählen Sie im Feld **„Eigentümer-Organisationseinheit“** die neue Gruppe aus.
    3.  Nach dem Speichern hat die neue Gruppe die volle administrative Kontrolle über den Datensatz.

### 5.6 Fehlerbehebung: „Ich sehe meine Daten nicht“
Falls Nutzer trotz Anmeldung keine Inhalte sehen, prüfen Sie folgende Punkte:

* **Gruppenmitgliedschaft:** Prüfen Sie im Info-Fenster des Logins, ob der Nutzer tatsächlich Mitglied der berechtigten Gruppe ist.
* **Explizite Rechte:** Ist die Gruppe des Nutzers im Datensatz unter „Freigaben“ explizit mit Leserechten markiert? Denken Sie daran, dass die Mitgliedschaft in einer übergeordneten Gruppe nicht ausreicht.
* **Mandantengrenzen:** Befindet sich der Datensatz in einem anderen Mandanten? Ohne Mitgliedschaft in einer Gruppe dieses Mandanten oder eine öffentliche Freigabe (`isPublic`) bleibt der Datensatz unsichtbar.
* **Aktualisierung:** Nach Rechteänderungen muss die Seite oft neu geladen werden (Taste **F5**), damit die neuen Berechtigungen vom Browser abgerufen werden.

### 5.7 Anleitung: Zusammenarbeit im Hybrid-Modell
So nutzen Sie zentrale Kreisdaten und lokale Kommunaldaten gleichzeitig.

* **Doppel-Mitgliedschaft:** Der Nutzer muss in Keycloak Mitglied in mindestens zwei Gruppen sein: einer Gruppe seines eigenen Mandanten und einer Gruppe des zentralen Mandanten.
* **Anmeldung:** Das Login-Fenster in KomMonitor listet bei erfolgreicher Konfiguration alle Mandanten-Gruppen auf, denen Sie angehören.
* **Katalogansicht:** Im Themenkatalog werden nun automatisch die Daten beider Mandanten zusammengeführt dargestellt, sofern die Lese-Rechte für Ihre Gruppen jeweils erteilt wurden.

---

## 6. Aktuelle Limitationen & Roadmap

* **Themenverwaltung**: Themen sind aktuell noch mandantenübergreifend sichtbar. Benutzen Sie Präfixe im Namen (z.B. **STADT_X_Soziales**).
* **Einseitige Synchronisation**: Die Verknüpfung erfolgt nur von KomMonitor nach Keycloak. Manuelle Änderungen direkt in Keycloak führen zu Inkonsistenzen.
* **Einstellungen und Design**: Derzeit haben nur User mit der Superadmin-Rolle ***kommonitor-creator*** Zugriff auf die Einstellungen von KomMonitor. Einstellungen greifen demnach noch mandantenübergreifend. Workaround: pro Manant können  separate ***Web Client*** und ***Client Config*** Software-Komponenten beim IT-Dienstleister aufgesetzt werden, die eine mandantenspezifische Konfiguration für Einstellungen und Design abbilden. 
* **Ausblick**: Volle Mandantenfähigkeit für Themen, Designs und die Prozessierung folgt 2026.

---

## 7. FAQ – Nach Themen strukturiert

In diesem Abschnitt finden Sie Antworten auf die häufigsten Fragen, die bei der täglichen Arbeit mit dem Mandantenkonzept auftreten.

### Thema: Datenzugriff & Sichtbarkeit

**F: Warum sieht mein neues Team das von mir erstellte Thema (oder den Indikator) nicht?**
* **Antwort:** In KomMonitor gibt es keine automatische Rechtevererbung innerhalb der Gruppenhierarchie. Auch wenn ein Team eine Untergruppe Ihres Amtes ist, müssen Sie den Datensatz bearbeiten und der neuen Gruppe im Bereich „Datensatz-Freigaben“ explizit Leserechte zuweisen.

**F: Reicht es aus, einen Indikator auf „öffentlich“ zu stellen, damit er im Web-GIS erscheint?**
* **Antwort:** Nein, für die Sichtbarkeit im öffentlichen Bereich (ohne Login) müssen zwei Bedingungen erfüllt sein:
    1. Beim Indikator muss der Schalter **isPublic** aktiviert sein.
    2. Auch die zugrunde liegende Raumebene (z. B. Stadtbezirke) muss in der Admin UI explizit der Öffentlichkeit freigegeben worden sein. Ist die Ebene intern, bleibt auch der Indikator unsichtbar.

---

### Thema: Technische Administration & Synchronisation

**F: Ich bin Mandanten-Admin. Warum kann ich das Logo und das Design meiner KomMonitor-Instanz nicht ändern?**
* **Antwort:** Solche allgemeinen technischen Konfigurationen sind aktuell noch nicht mandantenspezifisch möglich. Diese Einstellungen werden derzeit noch global für die gesamte Instanz durch Systemadministratoren verwaltet. Eine Individualisierung pro Mandant ist für die Roadmap 2026 geplant.

**F: Ich habe in Keycloak eine Gruppe umbenannt, aber in KomMonitor steht noch der alte Name. Warum?**
* **Antwort:** Die technische Verknüpfung erfolgt lediglich einseitig von KomMonitor aus. Werden Gruppen direkt in Keycloak geändert, gelöscht oder verschoben, erfolgt keine automatische Synchronisation zurück nach KomMonitor. Dies führt zu inkonsistenten Systemzuständen. Führen Sie Namensänderungen daher immer über die KomMonitor Admin UI durch.

**F: Ich habe gerade Rechte vergeben, aber der Nutzer sieht keine Änderung. Was ist zu tun?**
* **Antwort:** Es ist oft notwendig, die Seite im Browser neu zu laden (z. B. über die Taste **F5**). Erst durch das Neuladen werden die aktuellsten Berechtigungen vom System abgerufen und in der Oberfläche wirksam.

---

### Thema: Rollen & Verantwortlichkeiten

**F: Kann ich die Eigentümerschaft eines Indikators nachträglich auf ein anderes Amt übertragen?**
* **Antwort:** Ja. Benutzer mit entsprechenden administrativen Rechten für die Eigentümer-Gruppe können in der Ressourcenverwaltung für jeden Datensatz eine neue Eigentümer-Organisationseinheit hinterlegen. Damit wechselt die volle Kontrolle (Löschen/Rechteverwaltung) zum neuen Amt.

**F: Warum schlägt das Anlegen eines Nutzers in Keycloak durch mich als Mandanten-Admin fehl?**
* **Antwort:** Als Mandanten-Admin müssen Sie den neuen Nutzer bereits während des Registrierungsvorgangs einer Ihrer verwaltbaren Gruppen zuweisen. Ein Nutzer ohne direkte Gruppenzuordnung fällt technisch nicht in Ihren Zuständigkeitsbereich und kann daher nur durch globale Administratoren angelegt werden.

---

### Thema: Zusammenarbeit & Mandantengrenzen

**F: Kann eine Gruppe gleichzeitig zu zwei verschiedenen Mandanten gehören?**
* **Antwort:** Nein. Jeder Mandant besitzt seine eigene, unabhängige Gruppenstruktur. Gruppen sind technisch fest einem einzigen Mandanten (Wurzelknoten) zugeordnet.

**F: Wie kann ich trotzdem Daten eines anderen Mandanten nutzen?**
* **Antwort:** Ein registrierter Benutzer kann Mitglied in mehreren Gruppen (1-n) gleichzeitig sein. Um Daten aus verschiedenen Mandanten zu sehen, muss der Nutzer in Gruppen beider Mandanten als Mitglied eingetragen sein (sog. Doppel-Mitgliedschaft).

## 8. Praxis-Musterschemata

### 8.1 Szenario A: Die „All-in-One“ Kommune
* **Struktur**: Ein Mandant "Stadt Musterstadt" mit Untergruppen für Statistik, Sozialplanung und Jugendhilfe.
* **Logik**: Das Statistikamt veröffentlicht Daten auf Bezirksebene für Bürger (isPublic = EIN). Die Sozialplanung nutzt kleinräumige Baublöcke für interne Zwecke (isPublic = AUS).
* **Vorteil**: Transparenz nach außen bei gleichzeitigem Datenschutz nach innen.
* ***[zur detaillierten Szenariomodellierung](./Scenario_Einzelkommune.md)***

### 8.2 Szenario B: Strikte Trennung (N+1 Mandanten)
* **Struktur**: Kreis und jede Kommune erhalten einen eigenen Mandanten-Wurzelknoten.
* **Logik**: Keine gegenseitige Einsicht. Austausch erfolgt nur über offizielle Open-Data-Schnittstellen (isPublic).
* **Vorteil**: Maximale Datensouveränität und Vertrauen der Kommunen in die Datentrennung.
* ***[zur detaillierten Szenariomodellierung](./Scenario_mandant_isolation.md)***

### 8.3 Szenario C: Gemeinsame Sozialplanung
* **Struktur**: Ein gemeinsamer Mandant "Sozialplanung Kreis X".
* **Logik**: Der Kreis ist Eigentümer zentraler Indikatoren (z.B. SGB-II-Quoten). Kommunen erhalten Lese- oder Editierrechte, um eigene lokale Daten im selben System zu ergänzen.
* **Vorteil**: Einheitliche Datenbasis für den gesamten Kreis ohne Redundanz.
* ***[zur detaillierten Szenariomodellierung](./Scenario_Social_Planning.md)***

### 8.4 Szenario D: Das Hybrid-Modell
* **Struktur**: Ein Mandant für "Zentrale Daten" (Kreis-Basisdaten) und separate Mandanten für "Kommunale Fachplanung".
* **Logik**: Nutzer sind Mitglied in beiden Mandanten gleichzeitig (Doppel-Mitgliedschaft).
* **Vorteil**: Planer sehen im Web-Client beide Welten nahtlos nebeneinander, aber die sensiblen Fachdaten bleiben im kommunalen Mandanten isoliert.
* ***[zur detaillierten Szenariomodellierung](./Scenario_Hybrid_Model.md)***