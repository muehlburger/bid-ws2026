---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Derived Data
lernziele: [L5]
wiki: []
quellen: ["DDIA 2e, Kap. 1 „Systems of Record and Derived Data“ S. 10"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/derived-data.md:503a8d032fd8]
stand: 2026-11-27
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/derived-data.md), erzeugt am 2026-11-27 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Derived Data

## In einem Satz

Derived Data (abgeleitete Daten) entstehen, indem vorhandene Daten kopiert, umgeformt oder verdichtet werden; sie sind redundant, lassen sich aber jederzeit aus ihrer Quelle neu erzeugen.

## Warum das wichtig ist

Keine einzelne Darstellung bedient alle Zugriffe gut. Eine Buchungstabelle ist ideal zum Schreiben, aber zu langsam für die Shop-Anzeige und unhandlich für die Prognose. Abgeleitete Daten kaufen Lesegeschwindigkeit mit Redundanz. Für das Management heißt das: Jede zusätzliche Kopie braucht einen Verantwortlichen, der sie aktuell hält, sonst entstehen zwei Wahrheiten.

## Wie es funktioniert

Typische Formen:

| Form | Was wird abgeleitet |
|---|---|
| Cache | Ergebnis einer teuren Abfrage, kurzzeitig vorgehalten |
| Index | Suchstruktur über vorhandene Datensätze |
| Materialized View | gespeichertes Abfrageergebnis |
| Denormalisierte Kopie | zusammengeführte Tabellen, siehe Normalisierung vs. Denormalisierung |
| Trainiertes Modell | Muster aus historischen Daten |

Die Ableitung läuft entweder periodisch als Batch Processing oder laufend als Stream Processing. Geht eine Ableitung verloren, wird sie aus dem [System of Record](system-of-record.md) neu gebaut. Das Buch formuliert es so: „If you lose derived data, you can re-create it from the original source.“ (DDIA 2e, Kap. 1 „Systems of Record and Derived Data“ S. 10)

## Am Modehändler

Aus den Kassenbons und Bestandsbuchungen leitet der Händler drei Dinge ab: die Bestandsanzeige im Shop (laufend), die Faktentabelle im Warehouse (nächtlich) und daraus die Absatzprognose je Artikel und Filiale. Stellt sich heraus, dass die Prognose einen Rechenfehler enthält, wird der Code korrigiert und die Prognose aus den unveränderten Umsatzzeilen neu gerechnet.

## Trade-offs und Entscheidungsregel

- Ableiten lohnt sich, wenn deutlich öfter gelesen als geschrieben wird oder wenn die Abfrage auf den Originaldaten zu teuer ist.
- Jede Ableitung kostet: Speicherplatz, Rechenzeit beim Aktualisieren und die Gefahr, dass sie der Quelle hinterherhinkt.
- Regel: Schreibe nur in die Quelle, leite alles andere automatisch ab, und halte fest, wie alt eine Ableitung höchstens sein darf.

## Typische Fehlvorstellungen

- „Redundanz ist immer schlecht.“ Unkontrollierte Redundanz ist schlecht; bewusst abgeleitete Kopien sind ein Standardwerkzeug.
- „Abgeleitete Daten sind immer aktuell.“ Zwischen Änderung der Quelle und Aktualisierung der Kopie vergeht Zeit, von Millisekunden bis zu einem Tag.
- „Ein Machine-Learning-Modell ist kein Datum.“ Im Sinne des Buches ist auch ein trainiertes Modell eine Ableitung aus Trainingsdaten.

## Selbsttest

1. Nenne drei abgeleitete Datenbestände des Modehändlers.
2. Richtig oder falsch: Abgeleitete Daten müssen nicht gesichert werden, weil sie unwichtig sind.
3. Was ist der Preis dafür, dass die Shop-Anzeige schnell aus einer abgeleiteten Tabelle liest?

<details><summary>Lösung</summary>

1. Zum Beispiel Bestandsanzeige im Shop, Suchindex, Warehouse-Faktentabelle, Prognosetabelle.
2. Falsch in der Begründung. Sie sind rekonstruierbar, aber der Neuaufbau kann Stunden dauern; ob man sie sichert, ist eine Kostenabwägung.
3. Jede Buchung muss zusätzlich die Kopie aktualisieren, und die Anzeige kann kurz veraltet sein.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Derived Data anhand der Seite `derived-data.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich beschreibe dir einen Datenfluss in zwei Sätzen. Zeichne daraus eine Kette Quelle → Ableitungen und sag mir, wo eine Kopie veralten kann.*
- *Stelle mir nacheinander drei Fragen zu Derived Data, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [System of Record](system-of-record.md)
- Materialized View
- CQRS: Lesemodelle als systematische Ableitung
- Batch Processing und Stream Processing: die zwei Wege, Ableitungen zu erzeugen

## Quelle und Weiterlesen

- DDIA 2e, Kap. 1 „Systems of Record and Derived Data“ S. 10
