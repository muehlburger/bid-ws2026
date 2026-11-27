---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Kapitel 2 – Defining Nonfunctional Requirements
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Defining Nonfunctional Requirements“ S. 33", "DDIA 2e, Kap. 2 „Case Study: Social Network Home Timelines“ S. 34", "DDIA 2e, Kap. 2 „Describing Performance“ S. 37", "DDIA 2e, Kap. 2 „Reliability and Fault Tolerance“ S. 43", "DDIA 2e, Kap. 2 „Scalability“ S. 49", "DDIA 2e, Kap. 2 „Maintainability“ S. 52"]
klausurrelevant: true
status: Pflicht
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/kapitel/kap-02.md:409622b49034]
stand: 2026-11-27
version: 1
---
<!-- Auszug aus dem BID-Wiki (kapitel/kap-02.md), erzeugt am 2026-11-27 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Kapitel 2 – Defining Nonfunctional Requirements

## Worum es geht

Funktionale Anforderungen sagen, was ein System tun soll. Nichtfunktionale Anforderungen (Nonfunctional Requirements) sagen, wie gut: wie schnell, wie zuverlässig, bei welcher Last, mit welchem Pflegeaufwand. Das Kapitel gibt diesen vier Eigenschaften eine genaue Bedeutung und Messgrößen. Damit wird aus dem Wunsch *schnell und stabil* etwas, das sich vereinbaren, prüfen und bezahlen lässt.

Für diese Lehrveranstaltung ist es das wichtigste Grundlagenkapitel: Die Anforderungsliste, mit der jede Architekturentscheidung beginnt, entspricht seiner Gliederung.

## Die vier Eigenschaften

| Eigenschaft | Leitfrage | Seiten |
|---|---|---|
| **Performance** | Wie schnell antwortet das System, und wie viel schafft es? | [Response Time](response-time.md), Throughput, [Percentiles](percentiles.md), SLO und SLA |
| **Reliability** | Arbeitet es korrekt weiter, wenn etwas schiefgeht? | [Fault vs. Failure](fault-vs-failure.md), [Fault Tolerance](fault-tolerance.md) |
| **Scalability** | Was geschieht, wenn die Last wächst? | [Load](load.md), [Scalability](scalability.md), Shared-Nothing, [Scaling up vs. Scaling out](scaling-up-vs-scaling-out.md) |
| **Maintainability** | Lässt es sich über Jahre betreiben, verstehen und ändern? | [Maintainability](maintainability.md) (mit Operability und Evolvability), [Simplicity](simplicity.md) |

## Die Fallstudie des Kapitels

Das Kapitel beginnt mit einem Rechenbeispiel aus einem sozialen Netzwerk: Soll die Startseite bei jedem Aufruf frisch aus den Tabellen zusammengestellt oder beim Schreiben vorbereitet werden? Die Lehre daraus: Lastzahlen entscheiden über die Architektur, und vorbereitete Ergebnisse verlagern Arbeit vom Lesen zum Schreiben. In diesem Wiki steht dieselbe Überlegung am Modehändler in [Load](load.md) und Materialized View.

## Am Modehändler

- Performance: Die Bestandsanzeige braucht ein Ziel für das 99. Perzentil der Response Time; die nächtliche Absatzprognose braucht einen Fertigstellungszeitpunkt.
- Reliability: Der Ausfall einer Kasse darf nicht zum Ausfall der Anzeige für eine ganze Stadt werden.
- Scalability: Die Frage lautet nicht, ob das System skaliert, sondern was bei 84 statt 42 Filialen geschieht.
- Maintainability: Ein neues Bonfeld muss sich einführen lassen, ohne alle Kassen am selben Tag umzustellen.

## Lesehinweis

- Reihenfolge für den Einstieg: [Response Time](response-time.md), [Percentiles](percentiles.md), SLO und SLA, dann [Fault vs. Failure](fault-vs-failure.md), [Load](load.md), [Scalability](scalability.md), zuletzt [Simplicity](simplicity.md).
- Wer aus der Statistik kommt, beginnt mit [Percentiles](percentiles.md): Antwortzeiten sind rechtsschief verteilt, deshalb Median und Perzentile statt Mittelwert.
- Wer aus dem Management kommt, beginnt mit SLO und SLA und [Maintainability](maintainability.md).
- Achtung auf einen häufigen Kurzschluss: Eine kurze Response Time sagt nichts darüber, wie aktuell die gezeigten Daten sind. Das ist eine eigene Anforderung, siehe [Timeliness](timeliness.md).
- Die Klausur fragt aus diesem Kapitel vor allem Zuordnungen (Fault oder Failure), kleine Rechnungen (Perzentile, Last, Verfügbarkeit) und Szenario-Entscheidungen (Scaling up oder out).

## Selbsttest

[Selbsttest zu Kapitel 1 und 2](fragen-kap-01-02.md)

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Defining Nonfunctional Requirements“ S. 33
- DDIA 2e, Kap. 2 „Case Study: Social Network Home Timelines“ S. 34
- DDIA 2e, Kap. 2 „Describing Performance“ S. 37
- DDIA 2e, Kap. 2 „Reliability and Fault Tolerance“ S. 43
- DDIA 2e, Kap. 2 „Scalability“ S. 49
- DDIA 2e, Kap. 2 „Maintainability“ S. 52
