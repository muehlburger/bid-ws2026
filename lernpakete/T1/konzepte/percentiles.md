---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Percentiles
lernziele: [L8]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40", "DDIA 2e, Kap. 2 „Use of Response Time Metrics“ S. 41"]
klausurrelevant: true
status: Pflicht
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/percentiles.md:d0f9f6d7c90e]
stand: 2026-11-25
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/percentiles.md), erzeugt am 2026-11-25 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Percentiles

## In einem Satz

Ein Percentile (Perzentil) gibt an, unter welchem Wert ein bestimmter Anteil aller Messungen liegt: Beim 95. Perzentil (p95) der Response Time sind 95 von 100 Anfragen schneller und 5 langsamer.

## Warum das wichtig ist

Antwortzeiten streuen stark und sind rechtsschief: viele schnelle, wenige sehr langsame Anfragen. Der Mittelwert sagt dann wenig über die typische Erfahrung und nichts über die schlechteste. Wer Leistung vereinbart oder überwacht, braucht eine Kennzahl, die Ausreißer sichtbar macht.

## Wie es funktioniert

Alle Messwerte werden aufsteigend sortiert:

- **Median (p50):** Die Hälfte der Anfragen ist schneller. Gutes Maß für die typische Wartezeit.
- **p95, p99, p999:** hohe Perzentile, zusammen *Tail Latency* genannt. Sie zeigen, wie schlimm die Ausreißer sind.
- **Mittelwert:** taugt zur Abschätzung des Throughput, nicht als typische Antwortzeit.

Das Diagramm zeigt Balken für hundert Anfragen. Die meisten sind kurz, einige ragen weit heraus. Der Mittelwert liegt über dem Median; p95 und p99 liegen deutlich höher.

Hohe Perzentile zählen aus zwei Gründen. Die langsamsten Anfragen gehören oft zu den Kundinnen mit den meisten Daten, also den wertvollsten. Und wenn eine Seite mehrere Dienste aufruft, genügt ein langsamer Aufruf, um die ganze Seite zu bremsen (*Tail Latency Amplification*).

Hier ruft eine Webanwendung sieben Backends parallel auf. Sechs antworten rasch, eines braucht ein Vielfaches; die Nutzerin wartet auf das langsamste.

Rechenregel: Perzentile verschiedener Maschinen oder Zeitfenster darf man nicht mitteln. Man führt die Messwerte oder ihre Histogramme zusammen und bestimmt das Perzentil neu.

## Am Modehändler

Rechenbeispiel mit angenommenen Werten: Die Bestandsanzeige liefert 20 gemessene Antwortzeiten in Millisekunden, sortiert: 18 Werte zwischen 40 und 120, dann 400 und 1.900. Der Median liegt zwischen dem 10. und 11. Wert, also um 80. Das p95 ist der 19. Wert: 400. Der Mittelwert wird vom Ausreißer 1.900 auf rund 190 gezogen und beschreibt weder die typische noch die schlechte Erfahrung.

Für die Prognose gibt es je Nacht nur eine Laufzeit; Perzentile sind dort erst über viele Nächte sinnvoll.

## Trade-offs und Entscheidungsregel

- Typische Erfahrung: Median. Ausreißer: p95 oder p99. Kapazitätsrechnung: Mittelwert.
- Je höher das Perzentil, desto teurer die Optimierung. Irgendwann übersteigen die Kosten den Nutzen.
- Ziele in Perzentilen formulieren, siehe SLO und SLA.

## Typische Fehlvorstellungen

- „Der Durchschnitt ist die typische Antwortzeit.“ Bei schiefen Verteilungen nicht.
- „p99 betrifft nur ein Prozent, also egal.“ Bei vielen Aufrufen je Seite trifft es einen großen Teil der Seitenaufrufe.
- „Das p95 des Tages ist der Mittelwert der stündlichen p95.“ Rechnerisch sinnlos.

## Selbsttest

1. 100 Anfragen, p99 beträgt 2 Sekunden. Wie viele Anfragen dauerten länger?
2. Warum ist der Median robuster als der Mittelwert?
3. Eine Seite ruft zehn Dienste auf, jeder ist in einem von hundert Fällen langsam. Ist die Seite auch nur in einem von hundert Fällen langsam?

<details><summary>Lösung</summary>

1. Eine.
2. Einzelne extreme Werte verschieben ihn nicht.
3. Nein, deutlich öfter: Die Wahrscheinlichkeit, dass alle zehn schnell sind, ist 0,99 hoch 10, also rund 90 Prozent; etwa jeder zehnte Seitenaufruf ist langsam.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Percentiles anhand der Seite `percentiles.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Gib mir eine Liste von 20 Antwortzeiten und lass mich Median, p95 und Mittelwert bestimmen. Prüfe meinen Rechenweg Schritt für Schritt.*
- *Stelle mir nacheinander drei Fragen zu Percentiles, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Response Time](response-time.md)
- SLO und SLA
- Throughput
- [Selbsttest Kapitel 1 und 2](fragen-kap-01-02.md)

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40
- DDIA 2e, Kap. 2 „Use of Response Time Metrics“ S. 41
