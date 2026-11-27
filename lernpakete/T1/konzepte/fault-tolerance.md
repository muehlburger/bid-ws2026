---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Fault Tolerance
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Fault Tolerance“ S. 43", "DDIA 2e, Kap. 2 „Hardware and Software Faults“ S. 44", "DDIA 2e, Kap. 2 „Humans and Reliability“ S. 47"]
klausurrelevant: false
status: Ausblick
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/fault-tolerance.md:577fbee13808]
stand: 2026-11-27
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/fault-tolerance.md), erzeugt am 2026-11-27 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Fault Tolerance

## In einem Satz

Fault Tolerance (Fehlertoleranz) ist die Fähigkeit eines Systems, seinen Dienst weiter zu erbringen, obwohl bestimmte Teile fehlerhaft sind.

## Warum das wichtig ist

Fehlertoleranz ist der Mechanismus, der einen [Fault](fault-vs-failure.md) daran hindert, zum Failure zu werden. Sie kostet Geld, weil sie Redundanz verlangt. Die Managementfrage lautet daher: Welche Fehler wollen wir überstehen, und was ist uns das wert?

## Wie es funktioniert

Fehlertoleranz gilt immer nur für bestimmte Arten und eine bestimmte Zahl von Faults. Kein System übersteht alles. Drei Fehlerquellen:

| Quelle | Eigenheit | Gegenmittel |
|---|---|---|
| Hardware | häufig, aber meist voneinander unabhängig | Redundanz: gespiegelte Platten, mehrere Rechner, mehrere Standorte |
| Software | stark korreliert, weil überall derselbe Code läuft; kann viele Knoten zugleich treffen | Tests, Isolation von Prozessen, Überwachung, schrittweises Ausrollen |
| Menschen | Konfigurationsänderungen sind eine Hauptursache von Ausfällen | sichere Bedienoberflächen, Testumgebungen, schnelles Zurückrollen, Lernen ohne Schuldzuweisung |

Redundanz auf Softwareebene über mehrere Maschinen hat einen Zusatznutzen: Einzelne Rechner können für Wartung abgeschaltet werden, während der Dienst weiterläuft (Rolling Upgrade).

Ob die Toleranz tatsächlich funktioniert, zeigt nur der Ernstfall. Deshalb lösen manche Organisationen Faults absichtlich aus (Fault Injection, Chaos Engineering), um die Mechanismen laufend zu prüfen.

## Am Modehändler

- Hardware: Der Bestandsdienst läuft auf mehreren Rechnern mit Replication; fällt einer aus, übernehmen die anderen.
- Software: Alle Kassen der 42 Filialen laufen mit derselben Version. Ein Programmfehler, etwa bei der Zeitumstellung, trifft alle gleichzeitig; Redundanz hilft hier nicht. Neue Versionen werden daher zuerst in wenigen Filialen ausgerollt.
- Menschen: Eine falsch eingespielte Preisliste ist wahrscheinlicher als ein Hardwaredefekt. Wichtig sind ein rascher Weg zurück und eine Nachbesprechung, die nach Ursachen im Ablauf sucht.
- Test: In einer ruhigen Nacht wird die Leitung einer Filiale gezielt getrennt, um zu sehen, ob die Kasse puffert.

## Trade-offs und Entscheidungsregel

- Zuerst festlegen, welche Faults toleriert werden müssen: ein Rechner, ein Standort, ein Bedienfehler.
- Hardware-Redundanz hilft nur gegen unabhängige Fehler. Gegen korrelierte Fehler helfen Vielfalt, schrittweises Ausrollen und Rückwege.
- Fehlertoleranz macht das System komplexer; nicht mehr einbauen, als der Schaden rechtfertigt, siehe [Simplicity](simplicity.md).
- Verteilte Fehlertoleranz bringt eigene Probleme mit, siehe Kapitel 9.

## Typische Fehlvorstellungen

- „Mit Redundanz ist das System sicher.“ Nur gegen die Fehlerart, für die sie gebaut wurde.
- „Hardware ist die Hauptursache von Ausfällen.“ Häufiger sind Software- und Bedienfehler.
- „Wer den Fehler gemacht hat, ist schuld.“ Fehler von Menschen zeigen meist Schwächen im Gesamtsystem aus Technik und Organisation.

## Selbsttest

1. Warum schützt Redundanz schlecht gegen Softwarefehler?
2. Was ist der Zweck von Chaos Engineering?
3. Nenne zwei Maßnahmen gegen Bedienfehler.

<details><summary>Lösung</summary>

1. Weil alle redundanten Knoten denselben Code ausführen und der Fehler sie gleichzeitig trifft.
2. Fehlertoleranz-Mechanismen durch absichtlich ausgelöste Faults regelmäßig zu prüfen.
3. Zum Beispiel Testumgebung, schnelles Zurückrollen, schrittweises Ausrollen, klare Bedienoberflächen.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Fault Tolerance anhand der Seite `fault-tolerance.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich beschreibe dir ein System mit seinen Komponenten. Finde mit mir die Single Points of Failure und frage bei jedem, ob sich Fehlertoleranz dort lohnt.*
- *Stelle mir nacheinander drei Fragen zu Fault Tolerance, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Fault vs. Failure](fault-vs-failure.md)
- Replication
- [Verteilt vs. Single-Node](distributed-vs-single-node.md)
- Backward und Forward Compatibility: Voraussetzung für Rolling Upgrades

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Fault Tolerance“ S. 43
- DDIA 2e, Kap. 2 „Hardware and Software Faults“ S. 44
- DDIA 2e, Kap. 2 „Humans and Reliability“ S. 47
