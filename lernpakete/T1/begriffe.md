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
erzeugt_aus: [konzepte/entscheidungskette.md:e790ccbcf4c9, konzepte/big-data-5v.md:623805e0ce1d, konzepte/distributed-vs-single-node.md:fbfaa3586b67, konzepte/kap-02.md:048fda0e6ac9, konzepte/fault-vs-failure.md:d3986e698565, konzepte/batch-vs-stream.md:b369d96514c9, konzepte/timeliness.md:87b829edc18e, konzepte/scalability.md:6c2649674631, konzepte/scaling-up-vs-scaling-out.md:86b3c54a6b78, konzepte/response-time.md:b002fd4dd734, konzepte/maintainability.md:6409b0470fb5, konzepte/simplicity.md:cb97c1c74e69, konzepte/operational-vs-analytical-systems.md:cb46e2f0659b, konzepte/load.md:b53d7df111f0, konzepte/fault-tolerance.md:e02dd6e95d1d, konzepte/column-oriented-storage.md:890405d446b6, konzepte/crisp-dm.md:cb96496dd6a2, konzepte/system-of-record.md:c7c2af8bc15d, konzepte/derived-data.md:954fed77a4e9, konzepte/skalenniveau-und-kenngroessen.md:e2bec2a23f93, konzepte/percentiles.md:c58fd8d780dc, konzepte/star-schema.md:8e008044732e, konzepte/fragen-kap-01-02.md:54102833fedc]
stand: 2026-11-27
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
