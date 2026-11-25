---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Simplicity
lernziele: [L10]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Simplicity: Managing Complexity“ S. 54"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/simplicity.md:e5511ab6fa82]
stand: 2026-11-25
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/simplicity.md), erzeugt am 2026-11-25 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Simplicity

## In einem Satz

Simplicity (Einfachheit) bedeutet, ein System so zu bauen, dass Menschen es verstehen können, indem man unnötige Komplexität vermeidet.

## Warum das wichtig ist

Komplexität ist der Hauptgrund, warum Softwareprojekte langsam, teuer und fehleranfällig werden. In einem unübersichtlichen System dauert jede Änderung länger, und bei jeder Änderung steigt die Gefahr, etwas Unbeabsichtigtes zu zerstören. Einfachheit ist deshalb keine Stilfrage, sondern die Voraussetzung für [Maintainability](maintainability.md). Aus ihr folgt die Prüffrage dieses Kurses: Welches Problem zwingt uns zu dieser zusätzlichen Komplexität?

## Wie es funktioniert

Zwei Arten von Komplexität:

- **Essential Complexity** (wesentliche Komplexität) steckt im Problem selbst. Ein Händler mit 42 Filialen hat nun einmal 42 Orte, an denen gebucht wird.
- **Accidental Complexity** (zufällige Komplexität) entsteht nicht aus dem Problem, sondern aus der Lösung, im Buch: aus den Grenzen der Werkzeuge.

Die Grenze ist nicht scharf und verschiebt sich mit besseren Werkzeugen. Ziel ist, die zufällige Komplexität zu senken.

Das wichtigste Mittel ist **Abstraction** (Abstraktion): Eine einfache Schnittstelle verbirgt viele Details und lässt sich für viele Zwecke wiederverwenden. SQL ist ein Beispiel. Wer eine Abfrage schreibt, muss nicht wissen, wie die Daten auf der Platte liegen oder welcher Index verwendet wird.

Folgen hoher Komplexität: Budgets und Zeitpläne werden überschritten, und Änderungen bringen leichter Fehler mit, weil versteckte Annahmen und unerwartete Wechselwirkungen übersehen werden. Ein in Komplexität versunkenes Projekt heißt salopp *Big Ball of Mud*. Einen objektiven Maßstab für Einfachheit gibt es nicht.

## Am Modehändler

Zwei Entwürfe für die nächtliche Absatzprognose aus rund 50 Mio. Umsatzzeilen:

| | Entwurf A | Entwurf B |
|---|---|---|
| Aufbau | Cluster aus mehreren Rechnern mit verteilter Verarbeitung | eine gut ausgestattete Maschine mit einer spaltenorientierten Engine wie DuckDB |
| Betrieb | Cluster verwalten, Ausfälle einzelner Knoten behandeln | ein Rechner, ein Lauf |
| Reicht für die Last? | ja | ja |

Beide erfüllen die Anforderung. Entwurf A enthält Komplexität, die kein Problem des Händlers löst. Entwurf B ist die bessere Wahl, solange die Datenmenge nicht um Größenordnungen wächst. Die Filialanbindung dagegen ist wesentlich komplex: Sie lässt sich nicht wegvereinfachen, nur sauber kapseln.

## Trade-offs und Entscheidungsregel

- Die einfachste Lösung wählen, die die Anforderungen (SLO) erfüllt.
- Jeden zusätzlichen Baustein mit dem Problem begründen, das er löst.
- Weniger Bausteine sind fast immer leichter zu verstehen als mehr.
- Preis der Einfachheit: gelegentlich geringere Spitzenleistung und der Verzicht auf Vorsorge für Fälle, die vielleicht nie eintreten, siehe [Scalability](scalability.md).

## Typische Fehlvorstellungen

- „Einfach heißt wenig Funktion.“ Einfach heißt: verständlich für die Aufgabe, die zu lösen ist.
- „Komplexe Architektur zeigt Kompetenz.“ Sie zeigt oft, dass niemand gefragt hat, welches Problem gelöst wird.
- „Abstraktion macht alles einfacher.“ Eine schlechte Abstraktion verbirgt Details, die man doch kennen muss.

## Selbsttest

1. Unterscheide Essential und Accidental Complexity an je einem Beispiel des Modehändlers.
2. Welches Mittel nennt das Buch als wichtigstes gegen zufällige Komplexität?
3. Richtig oder falsch: Ein Cluster ist für die nächtliche Prognose die professionellere Lösung.

<details><summary>Lösung</summary>

1. Wesentlich: 42 Filialen buchen an verschiedenen Orten. Zufällig: ein Cluster für eine Aufgabe, die eine Maschine schafft.
2. Abstraktion.
3. Falsch. Wenn eine Maschine die Anforderung erfüllt, ist sie die bessere Lösung.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Simplicity anhand der Seite `simplicity.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich zeige dir eine Architekturskizze in Worten. Frage bei jedem Baustein: Welches Problem zwingt uns zu dieser Komplexität? Streiche mit mir, was keine Antwort hat.*
- *Stelle mir nacheinander drei Fragen zu Simplicity, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Maintainability](maintainability.md)
- [Verteilt vs. Single-Node](distributed-vs-single-node.md)
- [Scalability](scalability.md)
- DuckDB

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Simplicity: Managing Complexity“ S. 54
