---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Scalability
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Scalability“ S. 49", "DDIA 2e, Kap. 2 „Principles for Scalability“ S. 52"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/scalability.md:5d14280f7378]
stand: 2026-11-25
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/scalability.md), erzeugt am 2026-11-25 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Scalability

## In einem Satz

Scalability (Skalierbarkeit) beschreibt, wie gut ein System mit wachsender Last zurechtkommt und was man tun muss, damit die Leistung bei mehr Last erhalten bleibt.

## Warum das wichtig ist

Ein System, das heute zuverlässig läuft, tut das bei zehnfacher Last nicht automatisch. Skalierbarkeit ist aber kein Etikett, das ein Produkt hat oder nicht hat. Die Aussage *X skaliert* ist leer. Sinnvoll sind nur Fragen wie: Wenn die Last auf bestimmte Weise wächst, welche Möglichkeiten haben wir, und was kosten sie?

## Wie es funktioniert

1. **Last beschreiben:** Welche Größen wachsen? Siehe [Load](load.md).
2. **Leistung beobachten:** Was passiert mit [Response Time](response-time.md) und Throughput, wenn die Last steigt und die Ressourcen gleich bleiben?
3. **Ressourcen anpassen:** Um wie viel müssen sie wachsen, damit die Leistung gleich bleibt? Im Idealfall verdoppelt doppelte Hardware die tragbare Last (lineare Skalierbarkeit).

Die zwei Wege, Ressourcen zu erhöhen, vergleicht [Scaling up vs. Scaling out](scaling-up-vs-scaling-out.md).

Grundsätze aus dem Buch, in eigenen Worten:

- Es gibt keine Architektur, die für jede Anwendung skaliert. Sie hängt davon ab, welche Operationen häufig sind.
- Eine Architektur, die für eine Laststufe passt, passt selten für das Zehnfache. Bei jeder Größenordnung neu nachdenken.
- Nicht weiter als etwa eine Größenordnung vorausplanen.
- Ein System in Teile zerlegen, die weitgehend unabhängig arbeiten; das ist der Kern von Sharding und Shared-Nothing.
- Nichts komplizierter machen als nötig: Reicht eine Maschine, ist sie die bessere Lösung.

## Am Modehändler

Die Lastfrage des Händlers lautet nicht *Skaliert unser System?*, sondern zum Beispiel: Was geschieht, wenn aus 42 Filialen 84 werden und sich Bons und Artikel verdoppeln? Die Bestandsanzeige braucht dann mehr Buchungen pro Sekunde; sie lässt sich nach Filialen aufteilen. Die nächtliche Absatzprognose braucht länger; ob eine größere Maschine genügt, zeigt eine Messung. Eine Verhundertfachung zu planen, wäre heute verschwendeter Aufwand.

## Trade-offs und Entscheidungsregel

- Erst messen, wo der Engpass liegt, dann dort skalieren.
- Solange das Produkt klein ist, zählen Einfachheit und Änderbarkeit mehr als hypothetische Skalierung.
- Bei vorhersehbarer Last von Hand skalieren; automatische Anpassung lohnt sich bei stark schwankender Last und bringt eigene Überraschungen.
- Skalierbarkeit kostet [Simplicity](simplicity.md).

## Typische Fehlvorstellungen

- „Technologie X ist skalierbar.“ Ohne Angabe der Last und der Operationen ist die Aussage wertlos.
- „Skalierbar heißt schnell.“ Ein skalierbares System kann für die einzelne Anfrage langsam sein.
- „Man sollte von Anfang an für riesige Last bauen.“ Das bindet Aufwand und Komplexität für einen Fall, der vielleicht nie eintritt.

## Selbsttest

1. Warum ist die Aussage „unsere Datenbank skaliert“ unvollständig?
2. Was bedeutet lineare Skalierbarkeit?
3. Wie weit voraus sollte man Skalierung laut Faustregel planen?

<details><summary>Lösung</summary>

1. Sie nennt weder die Art der Last noch die Operationen noch die Kosten.
2. Doppelte Ressourcen tragen doppelte Last bei gleicher Leistung.
3. Etwa eine Größenordnung.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Scalability anhand der Seite `scalability.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich behaupte: „Wir brauchen ein verteiltes System, weil wir wachsen.“ Zerlege diese Aussage mit mir in Lastparameter, Engpass und Alternativen und sag mir, was noch fehlt.*
- *Stelle mir nacheinander drei Fragen zu Scalability, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Load](load.md)
- [Scaling up vs. Scaling out](scaling-up-vs-scaling-out.md)
- Shared-Nothing
- Sharding

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Scalability“ S. 49
- DDIA 2e, Kap. 2 „Principles for Scalability“ S. 52
