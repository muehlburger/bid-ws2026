---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Load
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Understanding Load“ S. 50", "DDIA 2e, Kap. 2 „Case Study: Social Network Home Timelines“ S. 34"]
klausurrelevant: false
status: Ausblick
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/load.md:0c71477ed3c4]
stand: 2026-11-26
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/load.md), erzeugt am 2026-11-26 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Load

## In einem Satz

Load (Last) ist die Arbeit, die ein System zu bewältigen hat, beschrieben durch wenige messbare Größen, die Load Parameters (Lastparameter).

## Warum das wichtig ist

Wer nicht sagen kann, wie groß die Last ist und wie sie wächst, kann weder Hardware planen noch über [Scalability](scalability.md) sprechen. Welche Parameter zählen, hängt vom System ab. Sie zu benennen, ist der erste Schritt jeder Architekturdiskussion und braucht keine Technik, nur Kenntnis des Geschäfts.

## Wie es funktioniert

Typische Lastparameter:

- Anfragen oder Buchungen pro Sekunde, im Mittel und in der Spitze
- Datenmenge pro Tag und Gesamtbestand
- Verhältnis von Lese- zu Schreibzugriffen
- Zahl gleichzeitig aktiver Nutzerinnen
- Größe der einzelnen Anfrage
- Fan-out: wie viele Folgeoperationen eine Anfrage auslöst

Gleicher Datendurchsatz kann sehr Unterschiedliches bedeuten: Sehr viele winzige Anfragen pro Sekunde und wenige riesige Dateien pro Minute können dieselbe Datenmenge pro Sekunde ergeben, verlangen aber völlig andere Systeme.

Oft bestimmt nicht der Durchschnitt die Architektur, sondern die Verteilung: wenige extreme Fälle, etwa ein Artikel, den plötzlich alle wollen. Und die Last lässt sich verschieben: Wer Ergebnisse beim Schreiben vorberechnet, hat mehr Schreib- und weniger Leselast, siehe Materialized View.

## Am Modehändler

Rechenbeispiel mit Annahmen: Rund 50 Mio. Umsatzzeilen pro Jahr, 300 Verkaufstage, 10 Stunden Öffnungszeit.

- Zeilen pro Tag: 50 Mio. geteilt durch 300, rund 167.000.
- Zeilen pro Sekunde im Mittel: 167.000 geteilt durch 36.000 Sekunden, rund 5.
- Spitze, angenommen das Fünffache: rund 25 pro Sekunde.
- Aktualisiert jede Zeile den Bestand und drei vorberechnete Summen (Fan-out 4): rund 100 Schreibvorgänge pro Sekunde.

Das ist für eine einzelne Maschine wenig. Die Leselast des Shops kann deutlich höher liegen, weil jede Produktseite Bestände abfragt. Der zweite Lasttyp ist die Prognose: ein Lauf pro Nacht über den gesamten Bestand.

## Trade-offs und Entscheidungsregel

- Lastparameter zuerst in Geschäftsgrößen ausdrücken (Bons, Artikel, Filialen), dann umrechnen.
- Mittelwert und Spitze getrennt angeben.
- Für jedes Wachstumsszenario prüfen, welcher Parameter wächst: Mehr Filialen erhöhen die Schreiblast, mehr Shop-Besuche die Leselast, mehr Historie die Datenmenge.
- Erst wenn die Zahlen eine Maschine überfordern, über [Scaling](scaling-up-vs-scaling-out.md) nachdenken.

## Typische Fehlvorstellungen

- „Last ist die Datenmenge.“ Die Datenmenge ist nur ein Parameter von mehreren.
- „Der Durchschnitt reicht.“ Ausgelegt wird auf die Spitze.
- „Große Zahlen pro Jahr bedeuten hohe Last.“ Umgerechnet auf Sekunden sind sie oft klein.

## Selbsttest

1. Rechne: 36 Mio. Bonzeilen pro Jahr, 300 Tage, 10 Stunden pro Tag. Wie viele Zeilen pro Sekunde im Mittel?
2. Was versteht man unter Fan-out?
3. Welcher Lastparameter wächst, wenn der Händler die Historie von fünf auf zehn Jahre verlängert?

<details><summary>Lösung</summary>

1. 36 Mio. geteilt durch 300 ergibt 120.000 pro Tag; geteilt durch 36.000 Sekunden ergibt rund 3,3 pro Sekunde.
2. Die Zahl der Folgeoperationen, die eine einzelne Anfrage auslöst.
3. Der Gesamtbestand an Daten und damit die Laufzeit der Prognose, nicht die Buchungen pro Sekunde.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Load anhand der Seite `load.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Frage mich nach den Geschäftszahlen meines Unternehmens und leite mit mir daraus drei Lastparameter in Operationen pro Sekunde ab. Kennzeichne jede Annahme.*
- *Stelle mir nacheinander drei Fragen zu Load, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Scalability](scalability.md)
- Throughput
- Materialized View
- Hot Spot

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Understanding Load“ S. 50
- DDIA 2e, Kap. 2 „Case Study: Social Network Home Timelines“ S. 34
