---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Scaling up vs. Scaling out
lernziele: [L10]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Shared-Memory, Shared-Disk, and Shared-Nothing Architectures“ S. 51", "DDIA 2e, Kap. 2 „Principles for Scalability“ S. 52"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/vergleiche/scaling-up-vs-scaling-out.md:6dc908caf506]
stand: 2026-11-25
version: 1
---
<!-- Auszug aus dem BID-Wiki (vergleiche/scaling-up-vs-scaling-out.md), erzeugt am 2026-11-25 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Scaling up vs. Scaling out

## In einem Satz

Scaling up (vertikal skalieren) heißt, auf eine stärkere Maschine umzuziehen; Scaling out (horizontal skalieren) heißt, die Last auf mehrere Maschinen zu verteilen.

## Warum das wichtig ist

Wenn ein System an seine Grenze kommt, sind das die zwei grundsätzlichen Auswege. Sie unterscheiden sich weniger in der Hardware als in den Folgen für Software, Betrieb und Risiko. Die Entscheidung bestimmt, ob das System einfach bleibt oder zu einem verteilten System wird.

## Wie es funktioniert

| | Scaling up | Scaling out |
|---|---|---|
| Vorgehen | mehr Kerne, mehr Hauptspeicher, schnellere Platten in einer Maschine | mehr Maschinen, verbunden über das Netz |
| Architektur | Shared-Memory | Shared-Nothing |
| Software | bleibt weitgehend unverändert | muss Daten aufteilen (Sharding) und Ausfälle behandeln |
| Kosten | steigen schneller als die Leistung; es gibt eine Obergrenze | wachsen etwa mit der Zahl der Knoten, dazu Betriebsaufwand |
| Ausfall | eine Maschine ist ein Single Point of Failure | einzelne Knoten dürfen ausfallen, wenn Replication eingerichtet ist |
| Standorte | einer | mehrere möglich |
| Anpassung | Umzug auf neue Maschine | Knoten hinzufügen oder entfernen |

Zum Preis der großen Maschine hält das Buch fest, dass ein Spitzenrechner mit doppelter Ausstattung in der Regel deutlich mehr als das Doppelte kostet. Umgekehrt nutzt doppelte Ausstattung nicht automatisch doppelte Last, weil Engpässe bleiben.

Die Wege schließen einander nicht aus. Üblich ist: zuerst vertikal, solange es wirtschaftlich ist, und horizontal erst dort, wo ein konkreter Grund vorliegt.

## Am Modehändler

- Die nächtliche Absatzprognose dauert zu lange. Die Daten passen in eine Maschine, die Verarbeitung ist ein einzelner Lauf: Scaling up, also mehr Kerne und Hauptspeicher, ist der einfachste Weg.
- Der Bestandsdienst stößt am Aktionssamstag an seine Grenze. Die Last teilt sich natürlich nach Filiale, und der Dienst soll den Ausfall eines Rechners überstehen: Scaling out mit Aufteilung nach Filiale.

## Trade-offs und Entscheidungsregel

- Reicht eine größere Maschine und ist ihr Ausfall verkraftbar: Scaling up.
- Übersteigt die Last jede einzelne Maschine, ist Ausfallsicherheit oder Standortverteilung gefordert oder schwankt die Last stark: Scaling out.
- Vor beidem prüfen, ob sich die Last senken lässt, etwa durch einen passenden Index oder eine Materialized View.
- Preis von Scaling out: die gesamte Komplexität verteilter Systeme, siehe [Verteilt vs. Single-Node](distributed-vs-single-node.md).

## Typische Fehlvorstellungen

- „Scaling out ist die moderne, Scaling up die veraltete Lösung.“ Einzelne Maschinen sind heute sehr leistungsfähig; vertikal ist oft die vernünftigere Wahl.
- „Mit doppelt so vielen Knoten geht alles doppelt so schnell.“ Nur bei Arbeit, die sich ohne Abstimmung aufteilen lässt.
- „Scaling up hat keine Grenze, solange man zahlt.“ Irgendwann gibt es keine größere Maschine.

## Selbsttest

1. Welche Architektur gehört zu Scaling out?
2. Nenne zwei Gründe, die für Scaling out sprechen, obwohl eine größere Maschine reichen würde.
3. Szenario: Die Prognose dauert fünf Stunden und soll in drei fertig sein; die Daten passen in den Hauptspeicher eines großen Rechners. Welcher Weg?

<details><summary>Lösung</summary>

1. Shared-Nothing.
2. Ausfallsicherheit, Verteilung auf mehrere Standorte, stark schwankende Last.
3. Scaling up: größere Maschine, keine Verteilung nötig.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Scaling up vs. Scaling out anhand der Seite `scaling-up-vs-scaling-out.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich schildere dir einen Engpass. Lass mich zuerst selbst zwischen Scaling up und Scaling out entscheiden und greife meine Begründung dann an ihrer schwächsten Stelle an.*
- *Stelle mir nacheinander drei Fragen zu Scaling up vs. Scaling out, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- Shared-Nothing
- [Scalability](scalability.md)
- [Load](load.md)
- [Simplicity](simplicity.md)

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Shared-Memory, Shared-Disk, and Shared-Nothing Architectures“ S. 51
- DDIA 2e, Kap. 2 „Principles for Scalability“ S. 52
