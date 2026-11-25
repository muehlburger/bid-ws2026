---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Operational vs. Analytical Systems (OLTP vs. OLAP)
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 1 „Operational Versus Analytical Systems“ S. 3", "DDIA 2e, Kap. 1 „Characterizing Transaction Processing and Analytics“ S. 5"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/vergleiche/operational-vs-analytical-systems.md:c32b1ee9e6c0]
stand: 2026-11-25
version: 1
---
<!-- Auszug aus dem BID-Wiki (vergleiche/operational-vs-analytical-systems.md), erzeugt am 2026-11-25 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Operational vs. Analytical Systems (OLTP vs. OLAP)

## In einem Satz

Operative Systeme (OLTP, Online Transaction Processing) erfassen und ändern einzelne Datensätze im Tagesgeschäft; analytische Systeme (OLAP, Online Analytical Processing) werten sehr viele Datensätze gemeinsam aus, um Entscheidungen zu unterstützen.

## Warum das wichtig ist

Die beiden Arbeitsweisen stellen gegensätzliche Anforderungen an Datenmodell, Speicherung und Betrieb. Wer sie in einem System vermischt, bekommt entweder langsame Kassen oder langsame Berichte. Fast jede Architekturentscheidung in diesem Wiki beginnt deshalb mit der Frage: Ist das ein operativer oder ein analytischer Zugriff?

## Wie es funktioniert

| Merkmal | Operativ (OLTP) | Analytisch (OLAP) |
|---|---|---|
| Lesen | wenige Datensätze über einen Schlüssel (Point Query) | Aggregation über sehr viele Datensätze |
| Schreiben | einzelne Datensätze anlegen, ändern, löschen | gesammeltes Laden oder Ereignisstrom |
| Nutzerinnen | Kundinnen, Verkaufspersonal über eine Anwendung | Analystinnen, Controlling, Data Scientists |
| Abfragen | fest im Programmcode | frei formuliert, explorativ |
| Datenstand | aktueller Zustand | Verlauf über die Zeit |
| Datenmenge | Gigabyte bis Terabyte | Terabyte bis Petabyte |
| Speicherung | zeilenorientiert, Index | [spaltenorientiert](column-oriented-storage.md) |

Die Größenangaben sind typische Bereiche, keine festen Grenzen. Zwischen beiden Welten vermittelt ETL in ein Data Warehouse.

## Am Modehändler

- Operativ: Eine Kasse bucht einen Bon; der Shop fragt den Bestand eines Artikels in Graz ab.
- Analytisch: Das Controlling summiert den Absatz je Filiale und Woche über alle rund 50 Mio. Umsatzzeilen; die nächtliche Prognose lernt aus derselben Historie.

Die Bestandsanzeige „noch 2 Stück in Graz“ ist operativ, obwohl sie aus einem Ereignisstrom gespeist wird: Gelesen wird ein einzelner Wert über einen Schlüssel.

## Trade-offs und Entscheidungsregel

- Wenige Datensätze je Zugriff, viele gleichzeitige Nutzerinnen, kurze [Response Time](response-time.md): operatives Design.
- Viele Zeilen, wenige Spalten, Aggregation, wenige Abfragen: analytisches Design.
- Beides auf frischen Daten in einer Anwendung, etwa Betrugserkennung an der Kasse: hybride Systeme (HTAP) prüfen.
- Preis der Trennung: zwei Systeme, eine Datenstrecke dazwischen und analytische Daten, die dem Betrieb hinterherhinken.

## Typische Fehlvorstellungen

- „OLTP braucht immer Transaktionen mit vollen Garantien.“ Der Begriff meint hier vor allem schnelle, kleine Lese- und Schreibzugriffe.
- „Analytik heißt Big Data.“ Viele analytische Aufgaben passen auf einen einzelnen Rechner, siehe [Verteilt vs. Single-Node](distributed-vs-single-node.md).
- „Echtzeit ist operativ, Batch ist analytisch.“ Auch Analytik kann laufend rechnen, und operative Systeme haben Batch-Läufe.

## Selbsttest

1. Ordne zu: (a) Preis eines Artikels an der Kasse nachschlagen, (b) Umsatz je Warengruppe über drei Jahre, (c) Retoure buchen.
2. Richtig oder falsch: In operativen Systemen formulieren Endnutzerinnen ihre Abfragen frei.
3. Welche Speicherform passt zu welchem Systemtyp?

<details><summary>Lösung</summary>

1. (a) operativ, (b) analytisch, (c) operativ.
2. Falsch. Die Abfragen sind im Anwendungscode festgelegt.
3. Zeilenorientiert mit Indizes für operative, spaltenorientiert für analytische Systeme.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Operational vs. Analytical Systems (OLTP vs. OLAP) anhand der Seite `operational-vs-analytical-systems.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich nenne dir acht Zugriffe aus meinem Unternehmen. Lass mich jeden als operativ oder analytisch einordnen und prüfe meine Begründung an den Merkmalen der Tabelle.*
- *Stelle mir nacheinander drei Fragen zu Operational vs. Analytical Systems (OLTP vs. OLAP), warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- Data Warehouse
- Row vs. Column Storage
- [System of Record](system-of-record.md)
- Wegweiser Kapitel 1

## Quelle und Weiterlesen

- DDIA 2e, Kap. 1 „Operational Versus Analytical Systems“ S. 3
- DDIA 2e, Kap. 1 „Characterizing Transaction Processing and Analytics“ S. 5
