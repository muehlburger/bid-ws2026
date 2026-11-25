---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: klausur
titel: "So fragt die Klausur zu T1"
lernziele: [L1, L5, L8, L10]
wiki: [konzepte/big-data-5v.md, konzepte/entscheidungskette.md, konzepte/crisp-dm.md, konzepte/skalenniveau-und-kenngroessen.md]
quellen: ["DDIA 2e, Kap. 1 „Distributed Versus Single-Node Systems“ S. 19", "DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40"]
begriffe: [Big Data und die 5V, Entscheidungskette, CRISP-DM, Skalenniveau und Kenngrößen, Batch vs. Stream]
klausurrelevant: true
sprache: de-AT
erzeugt: false
stand: 2026-11-25
version: 1
---

# So fragt die Klausur zu T1

Erst ohne Agent lösen, dann vergleichen. Acht Beispielitems aus dem Termin: fünf wurden im Termin live gezeigt (K1, K7, K3, K5, K6), drei kommen im Quiz Q1 (K2, K4, K8). Die Klausur verwendet dieselben Formen und Entscheidungsmuster, aber nie dieselben Items; der Hinweis „So ändert die Klausur diese Frage“ sagt, worauf du dich einstellen kannst. Die Lösungen stehen gesammelt am Ende.

### K1 Big-Data-Verständnis

Typ: Auswahl (Multiple Choice)
Lernziel: L1

Welche Aussage passt zum Verständnis von **Big Data und die 5V** in dieser Lehrveranstaltung?

- (a) Big Data beginnt ab 1 TB.
- (b) Big Data liegt vor, wenn Menge, Geschwindigkeit oder Vielfalt der Daten die Verarbeitungskapazität der bisher angemessenen Werkzeuge übersteigen; große Datenmengen allein rechtfertigen aber noch kein verteiltes System.
- (c) Sobald Daten aus mehreren Filialen stammen, ist ein verteiltes System nötig.
- (d) Big Data bezeichnet ausschließlich Streaming-Daten.

So ändert die Klausur diese Frage: andere Distraktoren aus den vier Fehlschlüssen, oder ein Kollege behauptet eine Zeilengrenze und du wählst die passende Antwort.

### K2 Beobachtung und Big-Data-Eigenschaft

Typ: Zuordnung
Lernziel: L1

Ordne jeder Beobachtung die Eigenschaft zu, die sie beschreibt: Velocity, Variety, Veracity, Volume.

1. „Kassenbons entstehen laufend, rund 20.000 Zeilen pro Tag.“
2. „Wetter, Kalender und Rezensionen werden kombiniert.“
3. „Kassenausfälle erzeugen Lücken in den Daten.“
4. „Historie aller Filialen seit 2019.“

So ändert die Klausur diese Frage: andere Beobachtungen aus einem anderen Unternehmen (Spital, Energieversorger), gleiche vier Eigenschaften.

### K3 CRISP-DM reihen

Typ: Reihung
Lernziel: L5

Bringe die Phasen von **CRISP-DM** in die übliche (kanonische) Abfolge; Rücksprünge sind in der Praxis normal: Modeling, Business Understanding, Deployment, Data Preparation, Evaluation, Data Understanding.

So ändert die Klausur diese Frage: Die Phasen stehen in anderer Reihenfolge, oder du ordnest sechs Tätigkeiten des Händlers den Phasen zu.

### K4 Phase erkennen

Typ: Auswahl
Lernziel: L5

In welcher CRISP-DM-Phase wird geprüft, ob das Prognosemodell die Geschäftsziele (weniger Stockouts, weniger Abverkauf) tatsächlich erreicht? (a) Data Understanding, (b) Modeling, (c) Evaluation, (d) Deployment.

So ändert die Klausur diese Frage: eine andere Tätigkeit (Entscheidung klären, Merkmale ableiten, nächtlichen Lauf einrichten), gleiche Phasen.

### K5 Diagramm wählen

Typ: Auswahl
Lernziel: L8

Der Verkaufspreis ist metrisch skaliert. Welches Diagramm zeigt seine Verteilung angemessen? (a) Kreisdiagramm, (b) Histogramm, (c) Liniendiagramm über die Artikelnummer, (d) Balkendiagramm der Filialen.

So ändert die Klausur diese Frage: ein nominales Merkmal mit zwei Kategorien (Aktion oder regulär) oder eine Zuordnung von vier Merkmalen zu **Skalenniveau und Kenngrößen**.

### K6 Median und Mittelwert

Typ: einfache Rechenaufgabe (numerisch)
Lernziel: L8

Tagesmengen eines Artikels: 1, 1, 2, 1, 5, 1, 3. Gib Median und Mittelwert an. Welche Kenngröße beschreibt den typischen Tag robuster?

So ändert die Klausur diese Frage: andere sieben Zahlen, oder du deutest Median 1 und Mittelwert 1,6 aus dem Datensatz (Schiefe erkennen, Kenngröße begründen).

### K7 Szenario nächtliche Prognose

Typ: Szenario (Auswahl)
Lernziel: L10

Ein Händler aktualisiert seine Absatzprognose einmal pro Nacht aus rund 50 Mio. historischen Umsatzzeilen (plus 20.000 neue je Tag); das Ergebnis wird am nächsten Morgen benötigt. Welche Architektur ist am angemessensten?

- (a) Event-Streaming, weil täglich neue Daten entstehen.
- (b) Ein nächtlicher Batch-Lauf auf einem Rechner oder Datenbankserver, weil die Aktualitätsanforderung das zulässt und die Menge dort verarbeitbar ist.
- (c) Ein verteilter Cluster, weil 50 Mio. Zeilen Big Data sind.
- (d) Streaming, weil die Filialen räumlich verteilt sind.

So ändert die Klausur diese Frage: der Zwilling mit umgekehrter Bedingung (Anzeige in Sekunden, dann ist die aufwendigere Lösung richtig), oder die Frage, welcher Umstand den Wechsel zu verteilter Verarbeitung rechtfertigt (Laufzeit sprengt das Nachtfenster). Begründe entlang der **Entscheidungskette**; **Batch vs. Stream** entscheidet die Aktualität.

### K8 Zwei Aussagen

Typ: Richtig/Falsch
Lernziel: L10

1. „Eine Stammdatentabelle mit 84 Filialen kann Bestandteil eines Big-Data-Systems sein, ist für sich genommen aber kein Big-Data-Problem.“
2. „Sobald ein Datensatz mehrere Millionen Zeilen umfasst, ist eine verteilte Verarbeitung erforderlich.“

So ändert die Klausur diese Frage: andere Aussagen zu den vier Fehlschlüssen oder zur Datenrate gegen Aktualität. Richtig/Falsch macht höchstens ein Zehntel der Klausurpunkte aus.

## Lösungen

K1: (b). Distraktor (c) ist der Fehlschluss „Herkunft ist Architektur“, (a) erfindet eine Grenze, (d) verwechselt Big Data mit Streaming (Seite [Big Data und die 5V](konzepte/big-data-5v.md)).

K2: 1 Velocity, 2 Variety, 3 Veracity, 4 Volume. Velocity ist die Datenrate, nicht die Frage, wie schnell ein Ergebnis gebraucht wird; das ist die Aktualitätsanforderung der Anwendung ([Big Data und die 5V](konzepte/big-data-5v.md), [Timeliness](konzepte/timeliness.md)).

K3: Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, Deployment ([CRISP-DM](konzepte/crisp-dm.md)).

K4: (c) Evaluation prüft gegen das Geschäftsziel aus dem Business Understanding, nicht nur gegen eine technische Metrik ([CRISP-DM](konzepte/crisp-dm.md)).

K5: (b) Histogramm; der Preis ist metrisch. Kreis- und Balkendiagramme passen zu nominalen Merkmalen, die Artikelnummer ist ein Name ([Skalenniveau und Kenngrößen](konzepte/skalenniveau-und-kenngroessen.md)).

K6: Sortiert 1, 1, 1, 1, 2, 3, 5: Median 1; Mittelwert 14 durch 7 gleich 2. Der Median ist robuster gegen den Ausreißer 5 ([Skalenniveau und Kenngrößen](konzepte/skalenniveau-und-kenngroessen.md), [Percentiles](konzepte/percentiles.md)).

K7: (b). (c) und (d) sind die Fehlschlüsse „Volume, also verteilt“ und „Herkunft ist Architektur“; (a) verwechselt Datenrate mit Aktualität. Verteilt wird erst, wenn Laufzeit, Datenmenge, Verfügbarkeit oder Wachstum einen Rechner überschreiten ([Verteilt vs. Single-Node](konzepte/distributed-vs-single-node.md), [Batch vs. Stream](konzepte/batch-vs-stream.md)).

K8: 1 richtig, 2 falsch. Erst wenn Laufzeit, Datenmenge, Verfügbarkeits- oder Skalierungsanforderungen die Single-Node-Lösung überschreiten, ist Verteilung gerechtfertigt ([Verteilt vs. Single-Node](konzepte/distributed-vs-single-node.md)).
