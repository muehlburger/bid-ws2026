---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Big Data und die 5V
lernziele: [L1]
wiki: []
quellen: ["Laney, D. (2001): 3D Data Management: Controlling Data Volume, Velocity, and Variety. META Group", "DDIA 2e, Kap. 1 „Distributed Versus Single-Node Systems“ S. 19"]
klausurrelevant: true
status: Pflicht
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/big-data-5v.md:039ce49b124c]
stand: 2026-11-26
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/big-data-5v.md), erzeugt am 2026-11-26 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Big Data und die 5V

## In einem Satz

Big Data liegt vor, wenn Menge, Geschwindigkeit oder Vielfalt der Daten die Verarbeitungskapazität der bisher angemessenen Werkzeuge übersteigen; die 5V (Volume, Velocity, Variety, Veracity, Value) sind Merkmale, mit denen man Daten beschreibt, keine Definition „Big Data = groß“.

## Warum das wichtig ist

Das Wort „Big Data“ löst Reflexe aus: Cluster, Streaming, neue Plattform. Die 5V bremsen den Reflex, weil sie Fragen stellen statt Urteile zu fällen. Welches V ist in diesem Szenario wirklich relevant, und was folgt daraus noch nicht? Die drei ersten V gehen auf Laney (2001) zurück; Veracity und Value kamen später aus der Praxis dazu. Im Buch kommen die V nicht vor; es spricht von Last, Datenmenge und Anforderungen.

## Wie es funktioniert

| Merkmal | Bedeutung | Frage an ein Szenario |
|---|---|---|
| Volume | Menge | Wie viele Zeilen, wie viele Gigabyte, wie schnell wächst es? |
| Velocity | Datenrate, also wie schnell Daten entstehen | Wie viele Ereignisse je Sekunde oder je Tag? |
| Variety | Vielfalt der Quellen und Formate | Tabellen, Ereignisströme, Freitext, Bilder? |
| Veracity | Verlässlichkeit | Lücken, Duplikate, Ausfälle, gemischte Formate? |
| Value | Nutzen | Welche Entscheidung wird damit besser? |

Zwei Dinge sind getrennt zu halten. Erstens: Velocity ist die Datenrate und nicht die Frage, wie schnell ein Ergebnis gebraucht wird; das ist eine Anforderung der Anwendung ([Timeliness](timeliness.md)). Zweitens: Ob Daten „big“ sind, ist relativ zur Verarbeitungskapazität angemessener Werkzeuge. Eine Datenbank oder eine spaltenorientierte Engine verarbeitet 50 Mio. Zeilen auf einem Rechner; dass eine Tabellenkalkulation daran scheitert, macht die Daten nicht zu Big Data ([Verteilt vs. Single-Node](distributed-vs-single-node.md)).

## Am Modehändler

Größenordnungen, keine Messwerte: rund 1,9 Mio. Umsatzzeilen je Quartal für 42 Filialen, Historie seit 2019 etwa 50 Mio. Zeilen (Volume); Kassenbons entstehen laufend, rund 20.000 Zeilen je Tag (Velocity); Stammdaten, Aktionskalender, Wetter, Rezensionen (Variety); Kassenausfälle, Retouren, Lücken (Veracity); bessere Bestellmengen, weniger Stockouts, weniger Abverkauf (Value). Für die nächtliche Prognose sind Volume und Variety relevant, erzwingen aber keine Verteilung. Für die Bestandsanzeige ist keines der V entscheidend, sondern die Aktualitätsanforderung.

## Trade-offs und Entscheidungsregel

- Jedes V ist eine Frage, keine Antwort. Erst alle fünf stellen, dann sagen, welche relevant sind und welche nicht.
- Aus einem relevanten V folgt noch keine Architektur; das klärt die [Entscheidungskette](entscheidungskette.md).
- Preis der 5V: Sie sind grob. Für eine Entscheidung braucht man Zahlen ([Load](load.md)).

## Typische Fehlvorstellungen

- „Big Data beginnt ab einem Terabyte.“ Es gibt keine feste Grenze; der Maßstab sind die Werkzeuge.
- „Velocity hoch, also Streaming.“ Hohe Datenrate erlaubt trotzdem einen nächtlichen Batch; niedrige Datenrate kann trotzdem Sekundenreaktion erfordern.
- „Big Data bezeichnet nur Streaming-Daten.“ Die meisten Big-Data-Auswertungen laufen im Batch.

## Selbsttest

1. Ordne zu: „Kassenbons entstehen laufend“, „Wetter und Rezensionen werden kombiniert“, „Kassenausfälle erzeugen Lücken“, „Historie seit 2019“.
2. Richtig oder falsch: Eine Stammdatentabelle mit 84 Filialen ist ein Big-Data-Problem, weil sie zu einem Big-Data-System gehört.
3. Warum ist „Excel schafft es nicht“ kein Argument für Big Data?

<details><summary>Lösung</summary>

1. Velocity, Variety, Veracity, Volume.
2. Falsch. Sie kann Teil eines Big-Data-Systems sein, ist aber selbst klein, statisch und selten genutzt.
3. Der Maßstab ist die Verarbeitungskapazität angemessener Werkzeuge, etwa einer Datenbank, nicht die der Tabellenkalkulation.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir die 5V anhand der Seite `big-data-5v.md` im Lernpaket am Modehändler und stelle mir danach ein Szenario, in dem ich sage, welche V relevant sind und welche nicht.*
- *Ich habe Velocity und Aktualität verwechselt. Stelle beide in einer Tabelle gegenüber und frage mich dann an zwei Beispielen ab.*

## Verwandt

- [Entscheidungskette](entscheidungskette.md)
- [Load](load.md)
- [Timeliness](timeliness.md)
- [Verteilt vs. Single-Node](distributed-vs-single-node.md)

## Quelle und Weiterlesen

- Laney, D. (2001): 3D Data Management: Controlling Data Volume, Velocity, and Variety. META Group. Herkunft der ersten drei V.
- DDIA 2e, Kap. 1 „Distributed Versus Single-Node Systems“ S. 19: Was ein einzelner Rechner heute schafft.
