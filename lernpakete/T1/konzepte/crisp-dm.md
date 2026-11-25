---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: CRISP-DM
lernziele: [L5]
wiki: []
quellen: ["Chapman, P. et al. (2000): CRISP-DM 1.0. Step-by-step data mining guide"]
klausurrelevant: true
status: Pflicht
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/crisp-dm.md:9c9889034924]
stand: 2026-11-25
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/crisp-dm.md), erzeugt am 2026-11-25 mit build_lernpaket.py. Nicht von Hand ändern. -->

# CRISP-DM

## In einem Satz

CRISP-DM (Cross-Industry Standard Process for Data Mining) ist ein Orientierungsrahmen für Datenprojekte mit sechs Phasen: Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, Deployment; Rücksprünge zwischen den Phasen sind normal.

## Warum das wichtig ist

Wer mit den Daten beginnt („Wir haben 50 Mio. Zeilen, was können wir vorhersagen?“), optimiert am Ende eine Kennzahl, die niemand bestellt hat. CRISP-DM stellt die Geschäftsfrage an den Anfang und die Inbetriebnahme ans Ende. Merksatz: Die Prognose ist nicht das Ziel, die Bestellung ist es.

## Wie es funktioniert

| Phase | Frage | Beim Modehändler |
|---|---|---|
| 1 Business Understanding | Welche Entscheidung soll besser werden, wer trifft sie, wie oft? | Bestellmenge je Filiale und Artikel, wöchentlich |
| 2 Data Understanding | Welche Daten gibt es, was steht in einer Zeile, wo sind die Lücken? | Umsatzzeilen je Tag, Filiale, Variante; Sonntage ohne Zeile |
| 3 Data Preparation | Fehler erkennen, Wahrheit und Ableitung trennen, Format wählen, Merkmale ableiten | Datenqualität, Kalenderfeatures |
| 4 Modeling | Ein Modell bauen, als wiederholbarer Schritt | nächtliche Pipeline, Vergleich mit einer einfachen Baseline |
| 5 Evaluation | Erreicht das Modell das Geschäftsziel, und wer verantwortet es? | weniger Stockouts, weniger Abverkauf; Testdaten; Recht und Ethik |
| 6 Deployment | Wie läuft es dauerhaft, auch wenn der Händler wächst? | nächtlicher Lauf; Echtzeit-Anzeige als eigene Architekturfrage |

Die übliche (kanonische) Abfolge ist 1 bis 6. In der Praxis springt man zurück: Zeigt die Evaluation ein falsches Ziel, geht es zu Business Understanding; zeigt Data Understanding fehlende Daten, braucht es eine neue Quelle. Evaluation prüft gegen das Geschäftsziel aus Phase 1, nicht nur gegen eine technische Metrik des Modeling.

```mermaid
flowchart LR
  B[Business Understanding] --> D[Data Understanding] --> P[Data Preparation] --> M[Modeling] --> E[Evaluation] --> X[Deployment]
  E -.-> B
  D -.-> B
```

Das Diagramm zeigt die sechs Phasen als Kette mit zwei gestrichelten Rücksprüngen: von Evaluation und von Data Understanding zurück zum Business Understanding.

## Am Modehändler

Aus der Entscheidung „Bestellmenge je Filiale und Artikel“ folgen Granularität (Tag, Filiale, Variante), Horizont (7 Tage), Zielgröße und Metrik. Deployment ist kein Anhang: Hier beginnt die Architekturfrage, ob ein nächtlicher Lauf reicht oder die Anzeige im Shop einen Stream braucht.

## Trade-offs und Entscheidungsregel

- Business Understanding zuerst, auch wenn die Daten schon da sind.
- Evaluation misst am Geschäftsziel, nicht an der schönsten Metrik.
- Preis: CRISP-DM sagt nichts über Architektur, Datenqualität oder Verantwortung im Detail; dafür gibt es die weiteren Konzepte des Wikis.

## Typische Fehlvorstellungen

- „CRISP-DM legt die Reihenfolge fest.“ Es ist ein Orientierungsrahmen; Schleifen sind der Normalfall.
- „Evaluation ist die technische Modellbewertung.“ Die gehört zum Modeling; Evaluation fragt nach dem Geschäftsziel.
- „Deployment ist der letzte Schritt und damit erledigt.“ Der Betrieb über Jahre ist der teuerste Teil.

## Selbsttest

1. Bringe in die übliche Abfolge: Modeling, Business Understanding, Deployment, Data Preparation, Evaluation, Data Understanding.
2. In welcher Phase wird geprüft, ob das Prognosemodell tatsächlich weniger Stockouts bringt?
3. In welcher Phase wird geklärt, welche Entscheidung besser werden soll?

<details><summary>Lösung</summary>

1. Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, Deployment.
2. Evaluation.
3. Business Understanding.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir CRISP-DM anhand der Seite `crisp-dm.md` im Lernpaket am Modehändler und frage mich danach zu drei Situationen, in welcher Phase wir stehen.*
- *Ich beschreibe dir ein Datenprojekt aus meinem Alltag ohne Firmennamen. Hilf mir, die sechs Phasen darauf abzubilden, und sag mir, wo das Projekt die Phase 1 übersprungen hat.*

## Verwandt

- [Entscheidungskette](entscheidungskette.md)
- [Derived Data](derived-data.md): ein trainiertes Modell ist abgeleitete Information
- Batch Processing: der nächtliche Lauf

## Quelle und Weiterlesen

- Chapman, P. et al. (2000): CRISP-DM 1.0. Step-by-step data mining guide. Ergänzungsquelle dieser Lehrveranstaltung; im Buch kommt CRISP-DM nicht vor.
