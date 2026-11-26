---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: begriffe
titel: Begriffe zu T1
lernziele: [L1, L5, L8, L10]
wiki: []
quellen: []
klausurrelevant: true
sprache: de-AT
erzeugt: true
erzeugt_aus: [konzepte/entscheidungskette.md:31e0b7928e57, konzepte/big-data-5v.md:68d5fa99749f, konzepte/distributed-vs-single-node.md:7e7fcde50e94, konzepte/kap-02.md:4920a7f1cb94, konzepte/fault-vs-failure.md:df9dbd04b889, konzepte/batch-vs-stream.md:ec73ca1ce481, konzepte/timeliness.md:fc858851d931, konzepte/scalability.md:f83386234fca, konzepte/scaling-up-vs-scaling-out.md:048b74476a25, konzepte/response-time.md:eb393a0a17d5, konzepte/maintainability.md:36316b580247, konzepte/simplicity.md:812aff8023a1, konzepte/operational-vs-analytical-systems.md:f8243ae05407, konzepte/load.md:c2d22e39dd1e, konzepte/fault-tolerance.md:ccd6647b250b, konzepte/column-oriented-storage.md:2c9903cc53f3, konzepte/crisp-dm.md:eb9a9d95aea6, konzepte/system-of-record.md:4dab83b81495, konzepte/derived-data.md:6bdd70fbe5b0, konzepte/skalenniveau-und-kenngroessen.md:b528270ac76c, konzepte/percentiles.md:cd20ed0eca37, konzepte/star-schema.md:757125ed1579, konzepte/fragen-kap-01-02.md:34d42566cb01]
stand: 2026-11-26
version: 1
---

# Begriffe zu T1

Erzeugt aus den Konzeptseiten des Pakets (Abschnitt „In einem Satz“); nicht von Hand ändern. Fachbegriffe bleiben Englisch, die deutsche Erklärung steht in Klammern. Jede Zeile führt zur Seite mit Mechanismus, Beispiel am Modehändler und Selbsttest.

| Begriff | In einem Satz | Seite |
|---|---|---|
| Batch vs. Stream | Batch verarbeitet eine abgeschlossene Datenmenge in einem Lauf, Stream verarbeitet eine endlose Folge von Events fortlaufend; der eigentliche Unterschied ist, ob die Eingabe ein Ende hat. | [Batch vs. Stream](konzepte/batch-vs-stream.md) |
| Big Data und die 5V | Big Data liegt vor, wenn Menge, Geschwindigkeit oder Vielfalt der Daten die Verarbeitungskapazität der bisher angemessenen Werkzeuge übersteigen; die 5V (Volume, Velocity, Variety, Veracity, Value) sind Merkmale, mit denen man Daten beschreibt, keine Definition „Big Data = groß“. | [Big Data und die 5V](konzepte/big-data-5v.md) |
| CRISP-DM | CRISP-DM (Cross-Industry Standard Process for Data Mining) ist ein Orientierungsrahmen für Datenprojekte mit sechs Phasen: Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, Deployment; Rücksprünge zwischen den Phasen sind normal. | [CRISP-DM](konzepte/crisp-dm.md) |
| Derived Data | Derived Data (abgeleitete Daten) entstehen, indem vorhandene Daten kopiert, umgeformt oder verdichtet werden; sie sind redundant, lassen sich aber jederzeit aus ihrer Quelle neu erzeugen. | [Derived Data](konzepte/derived-data.md) |
| Entscheidungskette | Die Entscheidungskette (eigene Synthese dieser Lehrveranstaltung, kein Begriff des Buches) ordnet jede Architekturentscheidung in vier Stufen: Anforderung, Datencharakteristik, Einschränkungen und Trade-offs, Entscheidung; Technologien kommen zuletzt. | [Entscheidungskette](konzepte/entscheidungskette.md) |
| Fault vs. Failure | Ein Fault (Fehlerzustand) liegt vor, wenn ein Teil des Systems nicht mehr richtig arbeitet; ein Failure (Ausfall) liegt vor, wenn das System als Ganzes den geforderten Dienst nicht mehr erbringt. | [Fault vs. Failure](konzepte/fault-vs-failure.md) |
| Kapitel 2 – Defining Nonfunctional Requirements | Funktionale Anforderungen sagen, was ein System tun soll. Nichtfunktionale Anforderungen (Nonfunctional Requirements) sagen, wie gut: wie schnell, wie zuverlässig, bei welcher Last, mit welchem Pflegeaufwand. Das Kapitel gibt diesen vier Eigenschaften eine genaue Bedeutung und Messgrößen. Damit wird aus dem Wunsch *schnell und stabil* etwas, das sich vereinbaren, prüfen und bezahlen lässt. | [Kapitel 2 – Defining Nonfunctional Requirements](konzepte/kap-02.md) |
| Maintainability | Maintainability (Wartbarkeit) beschreibt, wie leicht sich ein System über Jahre betreiben, verstehen und verändern lässt. | [Maintainability](konzepte/maintainability.md) |
| Operational vs. Analytical Systems (OLTP vs. OLAP) | Operative Systeme (OLTP, Online Transaction Processing) erfassen und ändern einzelne Datensätze im Tagesgeschäft; analytische Systeme (OLAP, Online Analytical Processing) werten sehr viele Datensätze gemeinsam aus, um Entscheidungen zu unterstützen. | [Operational vs. Analytical Systems (OLTP vs. OLAP)](konzepte/operational-vs-analytical-systems.md) |
| Percentiles | Ein Percentile (Perzentil) gibt an, unter welchem Wert ein bestimmter Anteil aller Messungen liegt: Beim 95. Perzentil (p95) der Response Time sind 95 von 100 Anfragen schneller und 5 langsamer. | [Percentiles](konzepte/percentiles.md) |
| Response Time | Die Response Time (Antwortzeit) ist die Zeit vom Absenden einer Anfrage bis zum Eintreffen der Antwort, gemessen dort, wo die Nutzerin sitzt. | [Response Time](konzepte/response-time.md) |
| Scalability | Scalability (Skalierbarkeit) beschreibt, wie gut ein System mit wachsender Last zurechtkommt und was man tun muss, damit die Leistung bei mehr Last erhalten bleibt. | [Scalability](konzepte/scalability.md) |
| Scaling up vs. Scaling out | Scaling up (vertikal skalieren) heißt, auf eine stärkere Maschine umzuziehen; Scaling out (horizontal skalieren) heißt, die Last auf mehrere Maschinen zu verteilen. | [Scaling up vs. Scaling out](konzepte/scaling-up-vs-scaling-out.md) |
| Simplicity | Simplicity (Einfachheit) bedeutet, ein System so zu bauen, dass Menschen es verstehen können, indem man unnötige Komplexität vermeidet. | [Simplicity](konzepte/simplicity.md) |
| Skalenniveau und Kenngrößen | Das Skalenniveau eines Merkmals (nominal, ordinal, metrisch) bestimmt, welches Diagramm und welche Kenngröße sinnvoll sind; bei schiefen Verteilungen beschreibt der Median den typischen Fall, der Mittelwert das Gesamtvolumen. | [Skalenniveau und Kenngrößen](konzepte/skalenniveau-und-kenngroessen.md) |
| System of Record | Ein System of Record (führendes System, auch *Source of Truth*) ist der Ort, an dem eine Information zum ersten Mal und verbindlich festgehalten wird; widersprechen sich zwei Systeme, gilt sein Wert. | [System of Record](konzepte/system-of-record.md) |
| Timeliness | Timeliness (Aktualität) ist die Eigenschaft, dass Nutzer den Zustand eines Systems auf aktuellem Stand sehen; eine Verletzung ist vorübergehend und heilt durch Warten. | [Timeliness](konzepte/timeliness.md) |
| Verteilt vs. Single-Node | Ein verteiltes System besteht aus mehreren Rechnern (Nodes, Knoten), die über ein Netzwerk zusammenarbeiten; ein Single-Node-System erledigt die Aufgabe auf einer einzigen Maschine. | [Verteilt vs. Single-Node](konzepte/distributed-vs-single-node.md) |
