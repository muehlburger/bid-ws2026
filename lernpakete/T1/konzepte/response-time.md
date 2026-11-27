---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Response Time
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Describing Performance“ S. 37", "DDIA 2e, Kap. 2 „Latency and Response Time“ S. 38"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/response-time.md:32bf7d5c8056]
stand: 2026-11-27
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/response-time.md), erzeugt am 2026-11-27 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Response Time

## In einem Satz

Die Response Time (Antwortzeit) ist die Zeit vom Absenden einer Anfrage bis zum Eintreffen der Antwort, gemessen dort, wo die Nutzerin sitzt.

## Warum das wichtig ist

Die Response Time ist das, was Menschen von der Leistung eines Systems spüren. Lange Wartezeiten kosten Umsatz und Geduld. Wer sie steuern will, muss wissen, woraus sie besteht, denn ein schnellerer Server hilft nicht, wenn die Zeit im Netz oder in einer Warteschlange vergeht.

## Wie es funktioniert

Die Response Time setzt sich aus mehreren Anteilen zusammen:

| Anteil | Bedeutung |
|---|---|
| Network Latency | Laufzeit der Nachricht im Netz, hin und zurück |
| Queueing Delay | Wartezeit, bis der Dienst die Anfrage aufgreift, etwa weil alle Prozessorkerne belegt sind |
| Service Time | Zeit, in der der Dienst die Anfrage aktiv bearbeitet |

*Latency* (Latenz) ist der Sammelbegriff für Zeit, in der eine Anfrage wartet und nicht bearbeitet wird.

Die Abbildung zeigt eine Zeitachse für Client und Service. Die Anfrage läuft schräg zum Service (Netzlaufzeit), wartet (Queueing Delay), wird bearbeitet (Service Time) und läuft zurück. Die Response Time überspannt alles.

Zwei Folgerungen: Erstens wird am Client gemessen, weil der Dienst seine eigene Warteschlange und das Netz nicht sieht. Zweitens ist die Response Time kein fester Wert. Dieselbe Anfrage dauert einmal kurz, einmal lang. Man beschreibt sie deshalb als Verteilung mit [Percentiles](percentiles.md). Wenige langsame Anfragen können nachfolgende aufhalten (Head-of-Line Blocking).

## Am Modehändler

Eine Kundin öffnet im Onlineshop eine Produktseite, die den Bestand je Filiale zeigt. Der Bestandsdienst braucht für die Abfrage nur wenige Millisekunden Service Time. Trotzdem wartet die Kundin am Samstagvormittag spürbar länger, weil viele Anfragen gleichzeitig eintreffen und sich vor dem Dienst stauen. Gemessen wird deshalb im Browser, nicht nur im Dienst.

Für die nächtliche Absatzprognose ist die Response Time kein sinnvolles Maß. Dort zählen Laufzeit und Throughput.

## Trade-offs und Entscheidungsregel

- Für interaktive Systeme ist die Response Time die führende Kennzahl, für Batch-Läufe der Throughput.
- Immer aus Sicht der Nutzerin messen und Ziele als SLO festhalten.
- Vor dem Optimieren fragen, welcher Anteil dominiert: Netz, Warten oder Bearbeiten.
- Response Time ist nicht Aktualität. Eine Anzeige kann schnell antworten und trotzdem einen veralteten Bestand zeigen, siehe [Timeliness](timeliness.md).

## Typische Fehlvorstellungen

- „Response Time und Service Time sind dasselbe.“ Die Service Time ist nur ein Teil.
- „Die Messung am Server genügt.“ Sie unterschlägt Netz und Wartezeit.
- „Eine schnelle Antwort bedeutet aktuelle Daten.“ Geschwindigkeit der Abfrage und Alter der Daten sind zwei verschiedene Anforderungen.

## Selbsttest

1. Nenne die drei Anteile der Response Time.
2. Richtig oder falsch: Die Service Time enthält die Wartezeit in der Warteschlange.
3. Der Bestandsdienst meldet intern sehr kurze Bearbeitungszeiten, Kundinnen klagen über Wartezeiten. Wo liegt vermutlich die Ursache?

<details><summary>Lösung</summary>

1. Network Latency, Queueing Delay, Service Time.
2. Falsch. Die Wartezeit zählt nicht zur Service Time.
3. Im Queueing Delay oder im Netz; deshalb muss am Client gemessen werden.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Response Time anhand der Seite `response-time.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich beschreibe dir eine langsame Anwendung. Führe mich mit Fragen dahin, den dominierenden Anteil der Response Time zu finden, bevor du eine Maßnahme vorschlägst.*
- *Stelle mir nacheinander drei Fragen zu Response Time, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Percentiles](percentiles.md)
- Throughput
- SLO und SLA
- [Wegweiser Kapitel 2](kap-02.md)

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Describing Performance“ S. 37
- DDIA 2e, Kap. 2 „Latency and Response Time“ S. 38
