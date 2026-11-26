---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Timeliness
lernziele: [L10]
wiki: []
quellen: ["DDIA 2e, Kap. 13 „Timeliness and Integrity“ S. 571"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/timeliness.md:6f27971eb21a]
stand: 2026-11-26
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/timeliness.md), erzeugt am 2026-11-26 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Timeliness

## In einem Satz

Timeliness (Aktualität) ist die Eigenschaft, dass Nutzer den Zustand eines Systems auf aktuellem Stand sehen; eine Verletzung ist vorübergehend und heilt durch Warten.

## Warum das wichtig ist

„Wie aktuell müssen die Daten sein?“ ist die Frage, die über Batch oder Streaming entscheidet, und sie ist eine fachliche Frage mit einer Zahl als Antwort: Sekunden, Minuten, ein Tag. Wer sie nicht stellt, baut entweder zu teuer oder liefert veraltete Information. Aktualität ist außerdem nicht dasselbe wie Geschwindigkeit: Eine Abfrage kann in Millisekunden antworten und trotzdem den Stand von gestern liefern ([Response Time](response-time.md)).

## Wie es funktioniert

In Systemen mit [Derived Data](derived-data.md) entsteht eine Verzögerung zwischen dem Schreiben im [System of Record](system-of-record.md) und dem Sichtbarwerden in den abgeleiteten Systemen:

| Weg der Daten | typische Verzögerung (Größenordnung) |
|---|---|
| nächtlicher Batch | bis zu einem Tag |
| Batch im Stundentakt | bis zu einer Stunde |
| Stream über ein Log | Sekunden |
| gemeinsame Transaktion | keine |

Solange nur die Aktualität leidet, ist das System in einem Zustand, der „noch nicht fertig“, aber nicht falsch ist. Sobald alle Änderungen verarbeitet sind, stimmt alles (Eventual Consistency). Das unterscheidet Timeliness grundlegend von Integrity: Dort hilft Warten nicht. Wer in bestimmten Situationen sofortige Aktualität braucht, etwa dass eine Kundin ihre eigene Bestellung sofort sieht, löst das gezielt für diesen Fall (Read-after-Write).

## Am Modehändler

Drei Anforderungen des Händlers, drei verschiedene Antworten:

- **Absatzprognose:** Sie darf den Stand von gestern Abend verwenden. Ein nächtlicher Batch genügt.
- **Bestandsanzeige „noch 2 Stück in Graz“:** Ist sie eine Stunde alt, fährt die Kundin umsonst in die Filiale. Gefordert sind Sekunden bis wenige Minuten; das rechtfertigt einen Stream.
- **Kassenbon:** Der Betrag muss sofort stimmen. Das leistet die Transaktion des Kassensystems, kein abgeleitetes System.

Zeigt die Anzeige zehn Sekunden lang noch drei statt zwei Stück, ist das eine kleine Verletzung der Timeliness: ärgerlich, aber in zehn Sekunden behoben.

## Trade-offs und Entscheidungsregel

Mehr Aktualität kostet: dauerhaft laufende Verarbeitung, Überwachung, schwierigere Fehlerbehandlung. Sofortige Aktualität über Systemgrenzen verlangt Koordination, die bei Ausfällen alles anhält. Regel: Für jeden Datenfluss die geforderte Aktualität als Zahl festhalten und die einfachste Lösung wählen, die sie erfüllt. Im Zweifel ist Integrity wichtiger als Timeliness, siehe Timeliness vs. Integrity.

## Typische Fehlvorstellungen

- „Aktuell heißt schnell.“ Antwortzeit und Aktualität sind verschiedene Größen.
- „Veraltete Daten sind falsche Daten.“ Sie sind richtig für einen früheren Zeitpunkt.
- „Alle Daten müssen in Echtzeit vorliegen.“ Die meisten Entscheidungen brauchen das nicht.

## Selbsttest

1. Worin unterscheidet sich eine Verletzung der Timeliness von einer Verletzung der Integrity?
2. Eine Abfrage antwortet in 20 Millisekunden mit dem Bestand von gestern. Welche Eigenschaft ist gut, welche schlecht?
3. Szenario: Die Personalplanung für nächste Woche nutzt Umsatzdaten. Welche Aktualität reicht?

<details><summary>Lösung</summary>

1. Sie ist vorübergehend und verschwindet durch Warten; eine Integritätsverletzung bleibt, bis sie repariert wird.
2. Die Antwortzeit ist gut, die Timeliness schlecht.
3. Tagesaktualität; ein nächtlicher Batch genügt.

</details>

## Frag deinen AI-Agenten

- „Ich nenne dir sechs Datenflüsse eines Händlers. Frage mich je Fluss nach der geforderten Aktualität und schlage die einfachste Lösung vor.“
- „Erkläre den Unterschied zwischen Antwortzeit und Aktualität mit einem Alltagsbeispiel.“

## Verwandt

- Integrity
- Timeliness vs. Integrity
- [Batch vs. Stream](batch-vs-stream.md)
- Replication Lag
- [Response Time](response-time.md)

## Quelle und Weiterlesen

- DDIA 2e, Kap. 13 „Timeliness and Integrity“ S. 571
