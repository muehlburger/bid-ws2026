---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: aufgaben
titel: "Aufgaben zu T1"
lernziele: [L1, L5, L8, L10]
wiki: [konzepte/entscheidungskette.md, konzepte/big-data-5v.md, konzepte/batch-vs-stream.md, konzepte/crisp-dm.md]
quellen: ["DDIA 2e, Kap. 1 „Distributed Versus Single-Node Systems“ S. 19", "DDIA 2e, Kap. 13 „Timeliness and Integrity“ S. 571"]
begriffe: [Entscheidungskette, Big Data und die 5V, Verteilt vs. Single-Node, Batch vs. Stream, Timeliness, CRISP-DM, System of Record, Derived Data]
klausurrelevant: true
sprache: de-AT
erzeugt: false
stand: 2026-11-26
version: 2
---

# Aufgaben zu T1

Zwei Aufgaben aus dem Termin, hier mit den drei Phasen für die Arbeit zu Hause: ohne Agent, mit Agent, ohne Agent. Im Termin selbst laufen beide Aufgaben in der Gruppe und ohne Agent. Aufgabe 3 (Notebook, Lernziel L8) steht in [uebung-notebook.md](uebung-notebook.md). Die Selbstkontrolle steht am Ende dieser Datei; sieh erst nach, wenn du Phase 3 abgeschlossen hast. Was auf diesem Blatt steht, hat ein Mensch geschrieben.

Der Fall: Ein Modehändler mit 42 Filialen und Onlineshop will zwei Datenprodukte: eine nächtliche Absatzprognose als Bestellvorschlag je Filiale und Artikel (Batch) und eine Bestandsanzeige „noch 2 Stück in Graz“ im Onlineshop (Stream). Zahlen zur Geschichte sind Größenordnungen; der Übungsdatensatz im Repo ist kleiner (12 Filialen, rund 400.000 Zeilen).

## Aufgabe 1: Vier Szenarien, fünf Leitfragen

### Auftrag

Gruppe zu vier bis fünf, 25 Minuten im Termin; zu Hause allein in etwa 30 Minuten. Material: diese Datei und ein Blatt Papier. Lernziele L10 (Batch oder Stream, ein Rechner oder mehrere, mit Begründung) und L1 (Anforderung als Qualität benennen). S1 und S2 bearbeiten alle (dieselben Kassendaten, zwei Entscheidungen); S3 und S4 sind Transferfälle, wenn Zeit bleibt. Beantworte für jedes Szenario die fünf Fragen in Stichworten und schreibe je Szenario einen Begründungssatz und eine Bedingung, unter der du anders entscheiden würdest. Begründe drei Dinge getrennt: die Aktualität (wie alt dürfen die Daten sein), die Verarbeitungsart (Batch oder Streaming) und die Verteilung (ein Rechner oder mehrere):

1. Welche Anforderungen hat das Szenario (Frist oder Aktualität, Aktualisierungsfrequenz, Verfügbarkeit)?
2. Welche Big-Data-Eigenschaften (5V) sind relevant, und welche nicht?
3. Reicht eine Single-Node-Lösung (ein Rechner, eine Datenbank)?
4. Batch oder Streaming?
5. Welche zusätzliche Komplexität wäre gerechtfertigt, und warum?

„Batch ja, verteilt nein“ ist eine zulässige Antwort, wenn du sie begründest. Denke in der **Entscheidungskette**: Anforderung, Datencharakteristik, Trade-offs, Entscheidung (Seite [Entscheidungskette](konzepte/entscheidungskette.md)).

**Die vier Szenarien**

- **S1** Jede Nacht laufen die Kassenumsätze aller 42 Filialen (rund 20.000 Zeilen pro Tag, Historie seit 2019, etwa 50 Mio. Zeilen) in eine Absatzprognose für die Bestellung der nächsten Woche; das Ergebnis muss um 6 Uhr früh vorliegen.
- **S2** Der Onlineshop soll anzeigen, ob ein Artikel in der Filiale Graz „noch 2 Stück“ hat. Zwei Fragen: Wie lange wartet die Kundin auf die Anzeige? Wie lange darf der letzte Verkauf in der Anzeige fehlen? Eine Seite kann schnell laden und trotzdem den Bestand von gestern zeigen.
- **S3** Für die Prognose sollen zusätzlich Wetterdaten (stündlich, 20 Stationen), Aktionskalender, Feiertage und Kundenrezensionen (Freitext) einfließen.
- **S4** Eine Excel-Liste mit 84 Filialen, Adresse und Verkaufsfläche wird einmal im Jahr aktualisiert und für einen Bericht ausgewertet.

### Phase 1 (ohne Agent)

Rund 15 Minuten, Geräte zu. Fülle für jedes Szenario das Raster mit den fünf Fragen aus und schreibe den Begründungssatz und die Bedingung handschriftlich; S1 und S2 zuerst. Entscheide zuerst, diskutiere dann; im Termin schreibt eine Person, alle entscheiden.

### Phase 2 (mit Agent)

Rund 10 Minuten. Lass den Agenten deine Begründungen prüfen, nicht schreiben: Prompt P1 aus [prompts.md](prompts.md) je Szenario („Prüfe meine Begründung gegen die Entscheidungskette und sag mir, welcher Schritt fehlt“). Danach Prompt G1 für das Szenario, bei dem du am unsichersten warst: Der Agent vertritt die Gegenposition, du verteidigst. Notiere eine Aussage des Agenten, die von den Konzeptseiten abweicht. Ohne Agent: Lies die Seiten [Verteilt vs. Single-Node](konzepte/distributed-vs-single-node.md) und [Batch vs. Stream](konzepte/batch-vs-stream.md) und prüfe deine Begründungen an den Entscheidungsregeln dort.

### Phase 3 (ohne Agent)

Rund 10 Minuten, Geräte zu. Zwei neue Szenarien, aus dem Gedächtnis, je ein Begründungssatz nach dem Muster Merkmal benennen, Anforderung prüfen, einfachste Lösung, Bedingung nennen:

- **Z1** Der Händler will den Wochenbericht je Filiale jeden Montag um 8 Uhr. Batch oder Stream, ein Rechner oder mehrere?
- **Z2** Der Onlineshop soll den letzten Artikel einer Variante nicht zweimal verkaufen. Batch oder Stream?

### Einstiegsstufe

Ohne Code und ohne Zahlenrechnung: Für jedes Szenario die Entscheidung ankreuzen (Batch oder Stream; ein Rechner oder mehrere) und einen Begründungssatz schreiben, der das relevante Merkmal und die Anforderung nennt.

### Vertiefungsstufe

Für S1 und S2: Nenne die Bedingung, unter der die andere Entscheidung richtig wäre. Für S1 zusätzlich: Welches der vier Signale (Laufzeit, Datenmenge, Verfügbarkeit, Wachstum) würde beim Händler am ehesten zuerst eintreten, und woran würde man es messen (Qualität und Messgröße aus [Kapitel 2](konzepte/kap-02.md))?

### Deklaration

Agent verwendet: nein / ja, wofür: Erklären, Prüfen, Abfragen, Gegenposition, anderes.

## Aufgabe 2: Case Canvas, Felder 1 bis 3

### Auftrag

Gruppe, 22 Minuten im Termin nach dem Rückblick auf die sechs Phasen von **CRISP-DM**; zu Hause allein in etwa 25 Minuten. Material: das Case Canvas (acht Felder auf einem Bogen A3; die Felder stehen unten) und ein Stift. Lernziele L1 (Anforderungen und Qualitäten) und L5 (CRISP-DM am Händler-Fall anwenden). Fülle für den Händler-Fall die ersten drei Felder aus. Schreibe ganze Sätze, keine Schlagworte.

**Das Case Canvas** begleitet alle fünf Termine. Unbenotet; die acht Felder sind die Entscheidungsmuster, die in der Klausur als Szenario-Aufgaben vorkommen.

| Nr. | Feld | Leitfrage | Termin |
|---|---|---|---|
| 1 | Problem | Welche Entscheidung soll besser werden? Wer trifft sie, wie oft, mit welcher Konsequenz bei Fehlern? | T1 |
| 2 | Daten | Welche Quellen, welche Granularität (Tag? Filiale? Artikel?), wie weit zurück, wie aktuell? | T1 |
| 3 | Big-Data-Eigenschaften | Welche V sind hier wirklich relevant und warum, und welche nicht? Was folgt daraus noch nicht? | T1 |
| 4 | Datenqualität | Welche Fehler darf die Pipeline durchlassen, welche nie? Was heilt von selbst? | T2 |
| 5 | Datenmodell | Was ist **System of Record**, was ist **Derived Data**? In welchem Format werden die Daten übergeben? | T2 |
| 6 | Methode | Wie entsteht die Prognose (Features, Modell, Baseline, nächtliche Pipeline), und wer verantwortet sie? | T4 |
| 7 | Evaluation | Woran messen wir? Fehler der Prognose an Testdaten; Ziel für die Antwortzeit der Anzeige als Perzentil | T4 |
| 8 | Architekturentscheidung | Performance, Reliability, Scalability, Maintainability: einfachste ausreichende Lösung, Trade-off, zuletzt Technologien; als Diagramm mit höchstens sechs Kästen | T5 |

### Phase 1 (ohne Agent)

Rund 12 Minuten, Geräte zu. Schreibe die Felder 1 bis 3 handschriftlich aus. Feld 1 beginnt mit der Entscheidung, nicht mit den Daten. Feld 3 endet mit dem Satz, was aus den relevanten V noch nicht folgt.

### Phase 2 (mit Agent)

Rund 8 Minuten. Prompt P3 aus [prompts.md](prompts.md): Erkläre dem Agenten in eigenen Worten, warum Business Understanding vor Data Understanding steht, und lass dich in drei Punkten bewerten. Dann Prompt A1 mit dem Thema CRISP-DM: fünf Fragen, eine nach der anderen. Ohne Agent: Lies die Seite [CRISP-DM](konzepte/crisp-dm.md) und ordne jede Zeile deines Canvas einer Phase zu.

### Phase 3 (ohne Agent)

Rund 5 Minuten, Geräte zu. Schreibe aus dem Gedächtnis die sechs Phasen in der üblichen Abfolge auf und markiere, in welcher Phase der Händler-Fall nach T1 steht. Dann ein Zwillingsfall in drei Sätzen: Ein Händler will Retouren vorhersagen. Welche Entscheidung soll besser werden, welche Daten braucht er, welches V ist relevant?

### Einstiegsstufe

Die drei Felder in je zwei bis drei Sätzen ausfüllen; keine Zahlen nötig außer den Größenordnungen aus dem Fall.

### Vertiefungsstufe

Feld 2 zusätzlich mit Granularität und Historie begründen: Warum Tag, Filiale und Variante, und warum mindestens zwei volle Jahre? Feld 3 zusätzlich: Welche Qualität aus Kapitel 2 ist für die Prognose die führende, und mit welcher Messgröße würdest du sie vereinbaren?

### Deklaration

Agent verwendet: nein / ja, wofür: Erklären, Prüfen, Abfragen, Gegenposition, anderes.

## Selbstkontrolle

Erst lesen, wenn Phase 3 abgeschlossen ist.

### Aufgabe 1

**Musterlösung je Szenario**

| Szenario | Anforderungen, relevante V | Reicht ein Rechner? | Batch oder Stream | Gerechtfertigte Komplexität |
|---|---|---|---|---|
| S1 | Ergebnis bis 6 Uhr (Stunden Spielraum), täglich, Verlässlichkeit des Laufs; Volume moderat (50 Mio. Zeilen Historie, 20.000 je Tag), Datenrate laufend und dieselbe wie in S2, Value hoch | Ja. Eine Datenbank oder eine spaltenorientierte Engine verarbeitet 50 Mio. Zeilen in Sekunden bis Minuten. Excel scheitert, aber Excel ist nicht der Maßstab | Batch, nächtlich | Keine Verteilung. Gerechtfertigt erst, wenn die Laufzeit das Nachtfenster sprengt, die Daten Speicher oder Platte eines Rechners übersteigen, Ausfallsicherheit gefordert ist oder das Zehnfache absehbar ist. Musterantwort: „Batch ja, verteilt nein.“ |
| S2 | Zwei Anforderungen getrennt: Antwortzeit der Seite (Performance, Sekundenbruchteile) und Aktualität des Bestands (**Timeliness**: der letzte Verkauf darf höchstens Sekunden fehlen); Verfügbarkeit rund um die Uhr. Datenrate wie in S1, Datenmenge je Ereignis klein. Anders ist die Anforderung, nicht die Daten | Rechenleistung ja. Die Frage ist, woher der Bestand kommt; ein nächtlicher Lauf ist für die Aktualität strukturell ungeeignet | Kein Nachtlauf. Zwei begründete Lösungen: ein Ereignisstrom aus den Kassen mit Zustand je Artikel und Filiale, oder die direkte Abfrage des führenden Bestandssystems (System of Record), wenn dessen Last und Verfügbarkeit das zulassen; die zweite ist einfacher und gewinnt, solange nichts dagegen spricht | Event-Log oder Broker (Reihenfolge, Duplikate, Ausfälle) nur, wenn Last oder Verfügbarkeit die direkte Abfrage ausschließen. Gerechtfertigt durch die Aktualität des Bestands, nicht durch Menge, Datenrate oder die Antwortzeit einer Abfrage |
| S3 | Integration heterogener Quellen (Zeitreihen, Kalender, Freitext) und Qualitätssicherung; weiterhin nächtlich; Variety, Veracity | Ja. Die Komplexität liegt in Datenflüssen, Schemata und Joins, nicht in der Rechenleistung | Batch | Eine Integrations- und Qualitätsschicht (Schema, Joins, Textvorverarbeitung, Prüfregeln); keine Verteilung. Brücke zu T2: Datenqualität ist Teil der Zuverlässigkeit |
| S4 | Jährlicher Bericht, 84 Zeilen; keine Eigenschaft relevant | Ja, eine Tabellenkalkulation reicht | Batch, trivial | Keine. Die Tabelle kann Stammdaten eines größeren Systems sein, ist aber selbst kein Big-Data-Problem |

**So klingt eine gute Begründung (S1):** „Volume ist vorhanden, rechtfertigt aber allein kein verteiltes System. Da das Ergebnis erst am nächsten Morgen benötigt wird, ist eine Batch-Lösung zunächst angemessen. Erst wenn Laufzeit, Datenmenge, Verfügbarkeit oder Skalierungsanforderungen einen Rechner überschreiten, ist eine verteilte Architektur gerechtfertigt.“

**Zwei typische Fehlbegründungen:** „Volume vorhanden, also verteilt“ (die Menge allein erzwingt nichts). „Die Daten kommen laufend, also Streaming“ (Datenrate wird mit der Aktualitätsanforderung verwechselt: hohe Datenrate erlaubt trotzdem nächtlichen Batch, niedrige Datenrate kann trotzdem Sekundenreaktion erfordern). Weitere: „Die Filialen sind verteilt, also verteiltes System“ (Herkunft ist nicht Architektur); „Excel schafft es nicht, also Big Data“ (falscher Maßstab); „Echtzeit ist immer besser“ (jede Sekunde weniger Verzögerung kostet Komplexität).

**Bedingung für die andere Entscheidung (Vertiefungsstufe):** S1 wird verteilt, wenn der Lauf trotz Optimierung regelmäßig nicht um 6 Uhr fertig ist (Signal Laufzeit, Qualität Performance, Messgröße Laufzeit des Nachtlaufs), wenn die Daten nicht mehr auf einen Rechner passen, wenn ein Ausfall nicht tolerierbar ist (Reliability) oder wenn das Zehnfache absehbar ist (Scalability). S2 käme mit Batch aus, wenn die Anzeige den Stand von gestern Abend zeigen dürfte, etwa „in der Regel vorrätig“ statt „noch 2 Stück“.

**Phase 3, Zwillingsszenarien:** Z1 Batch auf einem Rechner; die Aktualitätsanforderung liegt bei Tagen, der Zeitraum ist abgeschlossen. Z2 Stream oder eine direkte Abfrage des System of Record beim Kauf; die Aktualität ist in Sekunden verlangt, hier ist die aufwendigere Lösung richtig.

### Aufgabe 2

**Musterbeispiel (zum Vergleichen, nicht zum Abschreiben)**

- **Feld 1 Problem:** Die Filialleitung bestellt wöchentlich je Artikel nach; zu viel bindet Kapital und endet im Abverkauf, zu wenig erzeugt Stockouts. Gesucht ist eine Absatzprognose je Filiale und Artikel für die nächsten 7 Tage, die die Bestellmenge vorschlägt; zusätzlich sollen Tage mit auffällig fehlendem Absatz (möglicher Stockout oder Kassenausfall) markiert werden.
- **Feld 2 Daten:** Variantenumsatz je Tag, Filiale und Variante (Menge, Preis, Aktionskennzeichen) seit mindestens zwei Jahren; Stammdaten (Filiale, Abteilung, Warengruppe, Marke, Saison); Aktions- und Feiertagskalender; optional Wetter je Filialort. Granularität Tag, Filiale, Variante, weil Bestellung und Stockout auf dieser Ebene entstehen. Zwei volle Jahre, damit jede Saison zweimal vorkommt.
- **Feld 3 Big-Data-Eigenschaften:** Volume ja (mehrere Millionen Zeilen pro Jahr, wächst täglich), aber allein kein Grund für ein verteiltes System; Variety ja (Transaktionen, Stammdaten, Kalender, Wetter); Veracity ja (Lücken durch Kassenausfälle, fehlende Intervalle, Duplikate); Velocity: Daten entstehen laufend, aber die Anwendung braucht das Ergebnis erst am nächsten Morgen; entscheidend ist die Aktualitätsanforderung, nicht die Datenrate. Nur eine Echtzeit-Bestandsanzeige bräuchte Streaming. Konsequenz: Die einfachste ausreichende Lösung ist eine nächtliche Batch-Pipeline auf einem Rechner; ob mehr nötig ist, begründet Feld 8 in T5.

**Vier Fragen, die fast immer kommen:** Welche Granularität? Die, auf der die Entscheidung fällt, aggregierbar. Velocity ja, also Streaming? Nein, die Aktualitätsanforderung entscheidet. Wie viel Historie? Mindestens zwei volle Jahre. Ist Wetter Pflicht? Nein, erst prüfen, ob es die Prognose verbessert; jede Quelle kostet Integration.

**Vertiefungsstufe:** Führende Qualität der Prognose ist Performance im Sinn eines Fertigstellungszeitpunkts (Messgröße: Laufzeit des Nachtlaufs, Ziel „fertig bis 6 Uhr“); dazu Reliability (ein fehlgeschlagener Lauf muss auffallen und wiederholbar sein).

**Phase 3:** Abfolge Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, Deployment; nach T1 steht der Fall bei Business Understanding und Data Understanding. Zwillingsfall Retouren: Entscheidung ist etwa die Vorbereitung von Lager und Kundendienst auf erwartete Rücksendungen; Daten sind Umsatzzeilen mit negativer Menge je Tag, Filiale und Variante samt Stammdaten; relevant sind Veracity (Retouren sind in den Daten Buchungen mit negativer Menge und müssen richtig erkannt werden) und Variety, nicht Volume.
