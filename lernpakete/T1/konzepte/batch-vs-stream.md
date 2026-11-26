---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Batch vs. Stream
lernziele: [L10]
wiki: []
quellen: ["DDIA 2e, Kap. 13 „Batch and Stream Processing“ S. 544", "DDIA 2e, Kap. 11 „Batch Processing“ S. 451", "DDIA 2e, Kap. 12 „Stream Processing“ S. 487"]
klausurrelevant: true
status: Pflicht
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/vergleiche/batch-vs-stream.md:caf72cc27723]
stand: 2026-11-26
version: 1
---
<!-- Auszug aus dem BID-Wiki (vergleiche/batch-vs-stream.md), erzeugt am 2026-11-26 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Batch vs. Stream

## In einem Satz

Batch verarbeitet eine abgeschlossene Datenmenge in einem Lauf, Stream verarbeitet eine endlose Folge von Events fortlaufend; der eigentliche Unterschied ist, ob die Eingabe ein Ende hat.

## Warum das wichtig ist

„Batch oder Streaming?“ ist die häufigste Architekturfrage rund um Big Data und wird oft nach Mode statt nach Bedarf entschieden. Die richtige Entscheidungsgröße ist die geforderte Aktualität ([Timeliness](timeliness.md)): Wie alt darf das Ergebnis sein, und was ist es wert, wenn es jünger ist? Streaming, das niemand braucht, ist teure Komplexität; Batch, wo Sekunden zählen, liefert wertlose Zahlen.

## Wie es funktioniert

| Kriterium | Batch Processing | Stream Processing |
|---|---|---|
| Eingabe | begrenzt, bekannt („gestern“) | unbegrenzt, läuft weiter |
| Ende des Jobs | ja | nie |
| Alter des Ergebnisses | Stunden bis ein Tag | Sekunden bis Minuten |
| Kennzahl | Throughput | Verzögerung, Rückstand |
| Fehler beheben | Job neu starten | Checkpoints, Idempotenz, Replay |
| Zeitbegriff | einfach: alles liegt vor | schwierig: verspätete Events, Windowing |
| Betrieb | läuft zu festen Zeiten | läuft dauernd, braucht Überwachung rund um die Uhr |
| typische Aufgaben | Berichte, Training, ETL | Anzeigen, Alarme, Abgleich von Systemen |

Gemeinsam ist beiden das Prinzip: Eingaben werden nicht verändert, Ausgaben sind [Derived Data](derived-data.md) und lassen sich neu erzeugen. Deshalb verwenden moderne Engines dieselbe Logik für beides; Batch ist dann der Sonderfall eines Streams mit Ende. Zwischenformen gibt es auch: Ein Batch im Viertelstundentakt oder ein Stream in Mikro-Stapeln liegen nahe beieinander.

## Am Modehändler

| Aufgabe des Händlers | Geforderte Aktualität | Entscheidung |
|---|---|---|
| Absatzprognose aus rund 50 Mio. Umsatzzeilen | Stand vom Vorabend | Batch, nachts |
| Montagsbericht für die Geschäftsführung | Vorwoche | Batch |
| Anzeige „noch 2 Stück in Graz“ | Sekunden bis wenige Minuten | Stream |
| Alarm bei auffälligen Retouren an einer Kasse | Minuten | Stream |
| Neuberechnung nach Änderung der Prognosemerkmale | einmalig über die Historie | Batch (Reprocessing) |

Der Kassenbon ist in beiden Welten dasselbe Event: Er fließt sofort in die Bestandsanzeige und nachts in die Historie.

## Trade-offs und Entscheidungsregel

Entscheidungsregel in drei Schritten:

1. Geforderte Aktualität als Zahl festhalten. Reicht ein Tag oder eine Stunde, ist Batch die Antwort.
2. Wenn Minuten oder Sekunden nötig sind: prüfen, ob das für den ganzen Datenfluss gilt oder nur für eine Kennzahl. Nur diese wird gestreamt.
3. Den Batch behalten, als genaue Nachrechnung und für historische Neuberechnung.

Streaming kostet Dauerbetrieb, schwierigere Tests und Antworten auf Verspätung und Doppelverarbeitung (Exactly-once im Stream). Batch kostet Wartezeit.

## Typische Fehlvorstellungen

- „Streaming ist die moderne Form, Batch die alte.“ Beide lösen verschiedene Aufgaben.
- „Big Data heißt Streaming.“ Große Datenmengen werden überwiegend im Batch ausgewertet.
- „Echtzeit schadet nie.“ Sie kostet laufend Geld und Aufmerksamkeit.
- „Man muss sich für eines entscheiden.“ Fast jedes Unternehmen betreibt beides nebeneinander.

## Selbsttest

1. Was ist der grundlegende Unterschied zwischen Batch und Stream?
2. Szenario: Die Geschäftsführung will jeden Morgen den Umsatz des Vortags je Filiale sehen. Batch oder Stream?
3. Szenario: Die Filiale soll gewarnt werden, wenn ein Artikel in der nächsten Stunde auszugehen droht. Batch oder Stream?

<details><summary>Lösung</summary>

1. Die Eingabe ist beim Batch begrenzt, beim Stream unbegrenzt.
2. Batch; Tagesaktualität genügt und der Zeitraum ist abgeschlossen.
3. Stream; die Information verliert ihren Wert innerhalb von Minuten.

</details>

## Frag deinen AI-Agenten

- „Ich nenne dir zehn Anforderungen. Frage je Anforderung nach der Aktualität und entscheide mit mir zwischen Batch und Stream.“
- „Spiele den Skeptiker: Warum braucht mein Dashboard kein Streaming?“

## Verwandt

- Batch Processing
- Stream Processing
- [Timeliness](timeliness.md)
- Lambda vs. Kappa
- Selbsttest Kapitel 11 und 12

## Quelle und Weiterlesen

- DDIA 2e, Kap. 13 „Batch and Stream Processing“ S. 544
- DDIA 2e, Kap. 11 „Batch Processing“ S. 451
- DDIA 2e, Kap. 12 „Stream Processing“ S. 487
