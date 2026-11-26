---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Selbsttest Kapitel 1 und 2
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 1 „Trade-Offs in Data Systems Architecture“ S. 1", "DDIA 2e, Kap. 2 „Defining Nonfunctional Requirements“ S. 33"]
klausurrelevant: false
status: Ausblick
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/fragen/fragen-kap-01-02.md:0f043fcc9192]
stand: 2026-11-26
version: 1
---
<!-- Auszug aus dem BID-Wiki (fragen/fragen-kap-01-02.md), erzeugt am 2026-11-26 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Selbsttest Kapitel 1 und 2

Zwölf Fragen in den Formen der Klausur: Auswahl, Zuordnung, Reihung, Richtig/Falsch, kleine Rechnung, Szenario. Erst selbst antworten, dann die Lösung aufklappen. Jede Lösung nennt die Seite, auf der die Begründung steht. Alle Zahlen sind Annahmen für die Aufgabe.

### 1 Auswahl
Welche zwei Merkmale kennzeichnen ein operatives System? (a) Abfragen sind fest im Programmcode. (b) Jede Abfrage liest einen großen Teil der Daten. (c) Gelesen werden wenige Datensätze über einen Schlüssel. (d) Geschrieben wird gesammelt einmal pro Nacht.

<details><summary>Lösung</summary>

(a) und (c). Siehe [Operational vs. Analytical Systems (OLTP vs. OLAP)](operational-vs-analytical-systems.md).

</details>

### 2 Zuordnung
System of Record oder Derived Data? Bestandsbuchungen, Bestandsanzeige im Shop, Filialstammdaten, Suchindex für Artikel, Faktentabelle im Warehouse, Prognosetabelle.

<details><summary>Lösung</summary>

System of Record: Bestandsbuchungen, Filialstammdaten. Derived Data: Bestandsanzeige, Suchindex, Faktentabelle, Prognosetabelle. Prüfregel: Lässt es sich aus einer anderen Quelle neu berechnen? Siehe [System of Record](system-of-record.md) und [Derived Data](derived-data.md).

</details>

### 3 Reihung
Ordne nach abnehmendem Eigenbetrieb: (a) fertige Prognose-Anwendung als Software as a Service, (b) selbst geschriebenes Modell auf eigenem Server, (c) vom Anbieter betriebenes Warehouse, (d) selbst installierte Datenbank auf gemieteten virtuellen Maschinen.

<details><summary>Lösung</summary>

b, d, c, a. Siehe Cloud vs. Self-Hosting.

</details>

### 4 Richtig oder falsch
(a) Ein Data Lake erzwingt beim Schreiben ein Schema. (b) Ein Timeout bei einem Netzaufruf beweist, dass der Aufruf nicht ausgeführt wurde. (c) Simplicity bedeutet, zufällige Komplexität zu vermeiden. (d) Skalierbarkeit ist eine feste Eigenschaft eines Produkts.

<details><summary>Lösung</summary>

(a) falsch, (b) falsch, (c) richtig, (d) falsch. Siehe Data Lake, [Verteilt vs. Single-Node](distributed-vs-single-node.md), [Simplicity](simplicity.md), [Scalability](scalability.md).

</details>

### 5 Szenario
Die nächtliche Absatzprognose läuft zwei Stunden unter Volllast und steht 22 Stunden still. Die Kassendatenbank hat gleichmäßige, niedrige Last; das Team hat Erfahrung mit ihrem Betrieb. Welche Komponente spricht eher für die Cloud?

<details><summary>Lösung</summary>

Die Prognose: stark schwankende Last, Rechenleistung nur stundenweise nötig. Die Kassendatenbank kann im Eigenbetrieb bleiben: vorhersehbare Last, vorhandenes Know-how, und die Kasse soll ohne Internet funktionieren. Siehe Cloud vs. Self-Hosting.

</details>

### 6 Szenario
Ein Berater schlägt für die Prognose aus rund 50 Mio. Umsatzzeilen ein Cluster aus zehn Rechnern vor. Welche Frage stellst du zuerst, und welche Alternative prüfst du?

<details><summary>Lösung</summary>

Frage: Welches Problem zwingt uns zu dieser Komplexität? Alternative: eine einzelne, gut ausgestattete Maschine mit spaltenorientierter Verarbeitung. Verteilt wird erst, wenn Datenmenge, Ausfallsicherheit oder Standortverteilung es verlangen. Siehe [Verteilt vs. Single-Node](distributed-vs-single-node.md) und DuckDB.

</details>

### 7 Rechnung
24 Mio. Umsatzzeilen pro Jahr, 300 Verkaufstage, 8 Stunden pro Tag. (a) Zeilen pro Sekunde im Mittel? (b) Spitze beim Sechsfachen? (c) Schreibvorgänge pro Sekunde in der Spitze, wenn jede Zeile drei Werte fortschreibt?

<details><summary>Lösung</summary>

(a) 24 Mio. / 300 = 80.000 pro Tag; 8 Stunden = 28.800 Sekunden; rund 2,8 pro Sekunde. (b) rund 17 pro Sekunde. (c) rund 50 pro Sekunde. Für einen Rechner wenig. Siehe [Load](load.md).

</details>

### 8 Rechnung
Zehn Antwortzeiten in Millisekunden, sortiert: 60, 70, 70, 80, 90, 100, 110, 130, 300, 990. Bestimme Median, Mittelwert und p90. Ist das Ziel *p90 unter 250 ms* erfüllt?

<details><summary>Lösung</summary>

Median: Mitte zwischen 5. und 6. Wert, 95. Mittelwert: Summe 2.000 durch 10, also 200. p90: der Wert, unter oder auf dem 9 von 10 Messungen liegen, 300. Das Ziel ist verfehlt. Der Mittelwert liegt mehr als doppelt so hoch wie der Median, weil ein Ausreißer ihn verzerrt. Siehe [Percentiles](percentiles.md) und SLO und SLA.

</details>

### 9 Zuordnung
Fault oder Failure? (a) Eine Platte fällt aus, die Spiegelplatte übernimmt. (b) Der Shop zeigt zehn Minuten keine Bestände. (c) Eine Filiale ist offline, die Kasse puffert. (d) Die Prognose ist zum vereinbarten Zeitpunkt nicht fertig. (e) Alle Bestände sind wegen eines Rechenfehlers falsch.

<details><summary>Lösung</summary>

Fault: a, c. Failure: b, d, e. Maßstab ist der geforderte Dienst. Siehe [Fault vs. Failure](fault-vs-failure.md).

</details>

### 10 Reihung
Bringe den Ablauf eines Retry Storm in die richtige Reihenfolge: (a) Kassen wiederholen sofort, (b) Bestandsdienst wird langsam, (c) Last steigt weiter, (d) Timeouts an den Kassen, (e) Dienst bleibt überlastet, obwohl die Spitze vorbei ist.

<details><summary>Lösung</summary>

b, d, a, c, e. Gegenmittel am Client: Exponential Backoff, Circuit Breaker; am Server: Load Shedding, Backpressure. Siehe Throughput.

</details>

### 11 Rechnung
Ein SLA sichert 99,5 Prozent Verfügbarkeit je Monat mit 30 Tagen zu. Wie viele Minuten Ausfall sind erlaubt?

<details><summary>Lösung</summary>

30 Tage = 43.200 Minuten; 0,5 Prozent davon sind 216 Minuten, also 3 Stunden 36 Minuten. Siehe SLO und SLA.

</details>

### 12 Szenario
(a) Die Prognose dauert zu lang; die Daten passen in den Hauptspeicher eines großen Rechners. (b) Der Bestandsdienst erreicht am Aktionstag seine Grenze, die Last teilt sich nach Filialen, und ein Rechnerausfall darf den Dienst nicht stoppen. Scaling up oder Scaling out?

<details><summary>Lösung</summary>

(a) Scaling up: größere Maschine, keine Verteilung nötig. (b) Scaling out mit Aufteilung nach Filiale in einer Shared-Nothing-Architektur, weil neben der Last auch Ausfallsicherheit gefordert ist. Siehe [Scaling up vs. Scaling out](scaling-up-vs-scaling-out.md) und Shared-Nothing.

</details>

## Wie weiter

Unsichere Antworten zeigen, welche Seite noch einmal gelesen werden sollte. Übersicht: Kapitel 1, [Kapitel 2](kap-02.md). Weiter mit Selbsttest Kapitel 3 bis 5.

## Quelle und Weiterlesen

- DDIA 2e, Kap. 1 „Trade-Offs in Data Systems Architecture“ S. 1
- DDIA 2e, Kap. 2 „Defining Nonfunctional Requirements“ S. 33
