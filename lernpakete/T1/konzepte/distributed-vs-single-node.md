---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Verteilt vs. Single-Node
lernziele: [L10]
wiki: []
quellen: ["DDIA 2e, Kap. 1 „Distributed Versus Single-Node Systems“ S. 19", "DDIA 2e, Kap. 1 „Problems with Distributed Systems“ S. 20"]
klausurrelevant: true
status: Pflicht
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/vergleiche/distributed-vs-single-node.md:1bc5b60e30c4]
stand: 2026-11-27
version: 1
---
<!-- Auszug aus dem BID-Wiki (vergleiche/distributed-vs-single-node.md), erzeugt am 2026-11-27 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Verteilt vs. Single-Node

## In einem Satz

Ein verteiltes System besteht aus mehreren Rechnern (Nodes, Knoten), die über ein Netzwerk zusammenarbeiten; ein Single-Node-System erledigt die Aufgabe auf einer einzigen Maschine.

## Warum das wichtig ist

Verteilung gilt oft als Zeichen für Professionalität. Tatsächlich ist sie eine Kostenentscheidung: Sie löst bestimmte Probleme und schafft dafür neue. Die Leitfrage lautet: Welches Problem zwingt uns zu dieser zusätzlichen Komplexität?

## Wie es funktioniert

Gründe, die Verteilung erzwingen oder rechtfertigen:

- Die Aufgabe ist von Natur aus verteilt (mehrere Standorte, mehrere Geräte).
- Mehrere Cloud-Dienste arbeiten zusammen.
- [Fault Tolerance](fault-tolerance.md): Fällt eine Maschine aus, übernimmt eine andere.
- [Scalability](scalability.md): Datenmenge oder Last übersteigen eine Maschine.
- Kurze Wege zu weltweit verteilten Nutzerinnen.
- Elastizität bei stark schwankender Last.
- Rechtliche Vorgaben zum Speicherort.

Dem stehen die Kosten gegenüber: Jeder Aufruf über das Netz kann fehlschlagen oder hängen, ohne dass man weiß, ob er ausgeführt wurde. Aufrufe sind viel langsamer als lokale. Fehler sind schwer zu finden, und Daten über mehrere Dienste konsistent zu halten, ist Aufgabe der Anwendung. Mehr dazu in Partial Failure.

Moderne Einzelrechner haben viele Kerne, viel Hauptspeicher und schnelle Platten. Das Buch hält fest, dass ein einfaches Programm auf einem Rechner in manchen Fällen deutlich schneller ist als ein Cluster mit über hundert Kernen.

## Am Modehändler

Der Händler ist an einer Stelle zwangsläufig verteilt: 42 Filialen und ein Onlineshop buchen an verschiedenen Orten und müssen einen gemeinsamen Bestand ergeben. Der Shop soll außerdem den Ausfall eines Servers überstehen. Die nächtliche Absatzprognose dagegen passt auf eine Maschine: Rund 50 Mio. Umsatzzeilen in [spaltenorientierter Speicherung](column-oriented-storage.md) verarbeitet ein Werkzeug wie DuckDB auf einem gut ausgestatteten Rechner.

## Trade-offs und Entscheidungsregel

- Schafft es eine Maschine, dann nimm eine Maschine.
- Verteile, wenn einer der oben genannten Gründe nachweislich vorliegt, und nenne ihn ausdrücklich.
- Verteile nur den Teil, der es braucht.
- Bei großen Datenmengen ist es oft günstiger, die Rechnung zu den Daten zu bringen als umgekehrt.
- Preis: mehr Betrieb, schwierigere Fehlersuche, schwächere Garantien, siehe Replication und Sharding.

## Typische Fehlvorstellungen

- „Mehr Rechner sind automatisch schneller.“ Abstimmung und Netzverkehr fressen den Gewinn oft auf.
- „Big Data braucht immer ein Cluster.“ Die Größe, ab der eine Maschine nicht mehr reicht, liegt höher als meist angenommen.
- „Verteilt heißt ausfallsicher.“ Ohne durchdachte Fehlerbehandlung fällt ein verteiltes System häufiger aus, weil mehr Teile kaputtgehen können.

## Selbsttest

1. Nenne drei legitime Gründe für ein verteiltes System.
2. Richtig oder falsch: Ein Aufruf über das Netz, der in ein Timeout läuft, wurde sicher nicht ausgeführt.
3. Welche Komponente des Modehändlers muss verteilt sein, welche nicht?

<details><summary>Lösung</summary>

1. Zum Beispiel inhärente Verteilung, Fehlertoleranz, Skalierbarkeit, Latenz, Elastizität, rechtliche Vorgaben.
2. Falsch. Man weiß es nicht; genau das macht verteilte Systeme schwierig.
3. Die Bestandsführung über 42 Filialen und Shop ist inhärent verteilt; die nächtliche Prognose kommt mit einem Rechner aus.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Verteilt vs. Single-Node anhand der Seite `distributed-vs-single-node.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich schlage dir eine verteilte Architektur für eine Aufgabe vor. Frage mich nach Datenmenge, Last und Ausfalltoleranz und beurteile dann, ob ein einzelner Rechner genügt hätte.*
- *Stelle mir nacheinander drei Fragen zu Verteilt vs. Single-Node, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Scaling up vs. Scaling out](scaling-up-vs-scaling-out.md)
- Shared-Nothing
- [Simplicity](simplicity.md)
- DuckDB

## Quelle und Weiterlesen

- DDIA 2e, Kap. 1 „Distributed Versus Single-Node Systems“ S. 19
- DDIA 2e, Kap. 1 „Problems with Distributed Systems“ S. 20
