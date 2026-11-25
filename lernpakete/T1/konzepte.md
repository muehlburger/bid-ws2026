---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzeptpfad
titel: "Konzeptpfad T1"
lernziele: [L1, L5, L8, L10]
wiki: [konzepte/entscheidungskette.md, konzepte/kap-02.md, konzepte/percentiles.md]
quellen: ["DDIA 2e, Kap. 2 „Defining Nonfunctional Requirements“ S. 33"]
klausurrelevant: true
sprache: de-AT
erzeugt: false
stand: 2026-11-25
version: 1
---

# Konzeptpfad T1

Lies die Seiten in dieser Reihenfolge. **Pflicht** und **Kern** sind klausurrelevant und stehen auch in [T1_komplett.md](T1_komplett.md); **Ausblick** ist Vertiefung für Interessierte und wird in T1 nicht geprüft. Die Leitfrage sagt, worum es im Termin geht; die Seite erklärt das Konzept zeitlos. Jede Seite endet mit drei Selbsttestfragen.

## Zyklus 1: Wann wird aus einem Datenproblem ein Architekturproblem?

| Nr. | Seite | Leitfrage im Termin | Lernziel | Status | Lesezeit |
|---|---|---|---|---|---|
| 1 | [Entscheidungskette](konzepte/entscheidungskette.md) | In welcher Reihenfolge begründe ich eine Architekturentscheidung? | L10 | Pflicht | 5 min |
| 2 | [Big Data und die 5V](konzepte/big-data-5v.md) | Welche Merkmale der Daten sind im Szenario relevant, und was folgt daraus noch nicht? | L1 | Pflicht | 5 min |
| 3 | [Verteilt vs. Single-Node](konzepte/distributed-vs-single-node.md) | Welches Problem zwingt uns zu einem verteilten System? | L10 | Pflicht | 6 min |
| 4 | [Kapitel 2: Nonfunctional Requirements](konzepte/kap-02.md) | Welche vier Qualitäten messen jede Entscheidung, und mit welcher Messgröße? | L1 | Pflicht | 5 min |
| 5 | [Fault vs. Failure](konzepte/fault-vs-failure.md) | Was darf beim Händler kaputtgehen, ohne dass der Dienst ausfällt? | L1 | Pflicht | 5 min |
| 6 | [Batch vs. Stream](konzepte/batch-vs-stream.md) | Welche Anforderung rechtfertigt Streaming, und welche nicht? | L10 | Pflicht | 6 min |
| 7 | [Timeliness](konzepte/timeliness.md) | Warum ist Aktualität etwas anderes als Antwortzeit und Datenrate? | L10 | Kern | 5 min |
| 8 | [Scalability](konzepte/scalability.md) | Was heißt „skaliert“ ohne Angabe der Last? | L1 | Kern | 5 min |
| 9 | [Scaling up vs. Scaling out](konzepte/scaling-up-vs-scaling-out.md) | Vertikal zuerst oder horizontal: Was kostet welcher Weg? | L10 | Kern | 5 min |
| 10 | [Response Time](konzepte/response-time.md) | Woraus besteht die Antwortzeit der Bestandsanzeige? | L1 | Kern | 4 min |
| 11 | [Maintainability](konzepte/maintainability.md) | Wer betreibt und ändert das System in fünf Jahren? | L1 | Kern | 4 min |
| 12 | [Simplicity](konzepte/simplicity.md) | Welche Komplexität ist wesentlich, welche zufällig? | L10 | Kern | 4 min |
| 13 | [Operational vs. Analytical Systems](konzepte/operational-vs-analytical-systems.md) | Ist die Prognose ein operativer oder ein analytischer Zugriff? | L1 | Kern | 5 min |
| 14 | [Load](konzepte/load.md) | Wie rechnet man Geschäftszahlen in Last pro Sekunde um? | L1 | Ausblick | 5 min |
| 15 | [Fault Tolerance](konzepte/fault-tolerance.md) | Wie verhindert man, dass aus einem Fault ein Failure wird? | L1 | Ausblick | 5 min |
| 16 | [Column-Oriented Storage](konzepte/column-oriented-storage.md) | Warum schafft ein Rechner 50 Mio. Zeilen? (Vertiefung, Stoff von T2) | L10 | Ausblick | 5 min |

## Zyklus 2: CRISP-DM und das Case Canvas

| Nr. | Seite | Leitfrage im Termin | Lernziel | Status | Lesezeit |
|---|---|---|---|---|---|
| 17 | [CRISP-DM](konzepte/crisp-dm.md) | Welche Entscheidung soll besser werden, und in welcher Phase stehen wir? | L5 | Pflicht | 5 min |
| 18 | [System of Record](konzepte/system-of-record.md) | Was ist die Wahrheit, der Bon oder der Bestand? (Canvas-Feld 5, Vorschau auf T2) | L1 | Kern | 4 min |
| 19 | [Derived Data](konzepte/derived-data.md) | Warum ist die Prognose abgeleitete Information? | L5 | Kern | 4 min |

## Zyklus 3: Datenexploration

| Nr. | Seite | Leitfrage im Termin | Lernziel | Status | Lesezeit |
|---|---|---|---|---|---|
| 20 | [Skalenniveau und Kenngrößen](konzepte/skalenniveau-und-kenngroessen.md) | Welches Diagramm und welche Kenngröße passen zum Merkmal? Was ist der Sonntag ohne Zeile? | L8 | Pflicht | 6 min |
| 21 | [Percentiles](konzepte/percentiles.md) | Warum beschreiben Median und p95 eine Verteilung besser als der Mittelwert? | L8 | Pflicht | 5 min |
| 22 | [Star Schema](konzepte/star-schema.md) | Wie ist der Übungsdatensatz aufgebaut? (Vertiefung, Stoff von T2) | L8 | Ausblick | 4 min |
| 23 | [Selbsttest Kapitel 1 und 2](konzepte/fragen-kap-01-02.md) | Zwölf Fragen in den Formen der Klausur | L1 | Ausblick | 15 min |

Lesezeit für Pflicht und Kern: rund 80 Minuten, verteilt auf die Woche vor und nach dem Termin. Wer wenig Zeit hat, liest die Pflichtseiten und macht die Selbsttests; das reicht für Q1.
