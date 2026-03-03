## Glossar für Datenadministratoren

Dieses Glossar erläutert die zentralen Begriffe der KomMonitor-Mandantenfähigkeit und Datenmodellierung, um Fachplaner*innen ein sicheres Agieren im System zu ermöglichen.

### A
* **Administrator (global vs. lokal):** Ein globaler Administrator (Rolle: `kommonitor-creator`) hat Vollzugriff auf das gesamte System über alle Mandantengrenzen hinweg. Ein Mandanten-Administrator hingegen hat umfassende Rechte, die jedoch strikt auf seinen eigenen Mandanten (seine Kommunal- oder Kreisstruktur) begrenzt sind.
* **API (Application Programming Interface):** Die technische Schnittstelle, über die KomMonitor-Komponenten kommunizieren. Für Administratoren ist die Version wichtig, da die Mandantenfähigkeit erst ab der Data Management API Version 5.0.0 voll unterstützt wird.

### B
* **Benutzer (User):** Einzelpersonen, die über Zugangsdaten verfügen. In der neuen Systemlogik hängen die Rechte eines Nutzers ausschließlich von den Gruppen ab, in denen er Mitglied ist.

### C
* **Client-Admin-Rollen:** Administrative Rollen (z. B. `client-user-creator` oder `client-resources-creator`), die eine **hierarchische Wirkung** haben. Sie erlauben die Verwaltung der eigenen Gruppe sowie **aller** untergeordneten Gruppen und Teams.

### D
* **Datensatz:** Ein Sammelbegriff für alle in KomMonitor verwalteten Ressourcen, bestehend aus Indikatoren, Georessourcen oder Raumeinheiten.
* **Doppel-Mitgliedschaft:** Ein technisches Szenario, bei dem ein Benutzer Mitglied in Gruppen zweier verschiedener Mandanten ist. Dies wird im Hybrid-Modell genutzt, um gleichzeitig Zugriff auf zentrale Kreisdaten und interne Kommunaldaten zu erhalten.

### E
* **Eigentümerschaft (Ownership):** Die exklusive Zuordnung eines Datensatzes zu einer Organisationseinheit (Gruppe). Nur die Eigentümer-Gruppe hat das Recht, den Datensatz zu löschen oder die Zugriffsrechte für andere Gruppen zu verwalten.

### G
* **Georessource:** Räumliche Objektdaten (Punkte, Linien oder Flächen), wie zum Beispiel Standorte von Schulen, Kitas oder Verlauf von Radwegen.
* **Gruppe (Organisationseinheit):** Die Basiseinheit der Rechteverwaltung. In KomMonitor gibt es eine 1:1-Verknüpfung zwischen den fachlichen Teams (Orga-Einheiten) und den technischen Gruppen im Hintergrundsystem Keycloak.

### I
* **Indikator:** Eine berechnete Kennzahl (z. B. SGB-II-Quote), die räumlich auf Raumeinheiten aggregiert ist und oft über Zeitreihen hinweg beobachtet wird.
* **isMandant:** Ein technisches Kennzeichen (Flag) in der Admin-UI. Ist dieser Schalter aktiv, wird die Gruppe zum "Wurzelknoten" – also zur obersten Ebene eines neuen, isolierten Mandanten.
* **isPublic (Öffentliche Lesefreigabe):** Ein entscheidender Schalter für das Open-Data-Konzept. Ist `isPublic` aktiv, können anonyme Nutzer und alle anderen Mandanten den Datensatz lesend nutzen.

### K
* **Keycloak:** Das externe Identitäts- und Zugriffsmanagementsystem, das KomMonitor zur sicheren Verwaltung von Benutzern und Gruppen verwendet.

### M
* **Mandant (Tenant):** Ein logisch abgeschotteter Bereich innerhalb einer KomMonitor-Instanz. Daten und Nutzer eines Mandanten sind für andere Mandanten unsichtbar, sofern sie nicht explizit veröffentlicht wurden.
* **Metadaten:** "Daten über Daten". Sie beschreiben die Herkunft, Erhebungsmethode, Zeitbezüge und fachliche Definition eines Datensatzes.

### O
* **Obergruppe (Parent Group):** Die direkt übergeordnete Einheit in der Hierarchie. Eine Obergruppe kann ihre administrativen Aufgaben über `client`-Rollen an Untergruppen delegieren.

### P
* **parentID:** Der technische Verweis einer Gruppe auf ihre Obergruppe, der die hierarchische Baumstruktur innerhalb eines Mandanten definiert.

### R
* **Raumebene:** Die geographische Bezugseinheit für Daten (z. B. Stadtteile, statistische Bezirke oder Baublöcke). Raumeinheiten können wie Indikatoren entweder intern oder öffentlich geschaltet werden.
* **Ressourcenverwaltung:** Der Bereich in der KomMonitor Admin-UI, in dem Datensätze hochgeladen, editiert und mit Rechten versehen werden.

### T
* **Themenkatalog:** Die strukturelle Gliederung (z. B. "Demographie > Alter"), in der Datensätze für den Endnutzer im Web-Client einsortiert werden.

### U
* **Unit-Admin-Rollen:** Administrative Rollen (z. B. `unit-user-creator`), die **keine hierarchische Wirkung** haben. Sie erlauben die Verwaltung ausschließlich innerhalb der einen, spezifischen Gruppe, ohne Zugriff auf Untergruppen.
* **Untergruppe (Child Group):** Eine Gruppe, die einer anderen untergeordnet ist. Sie bildet die feinere Gliederung innerhalb eines Amtes oder Mandanten ab.

### W
* **Wurzelknoten:** Die oberste Gruppe einer Hierarchie. In KomMonitor ist dies immer die Gruppe, für die die Eigenschaft `isMandant` aktiviert wurde.