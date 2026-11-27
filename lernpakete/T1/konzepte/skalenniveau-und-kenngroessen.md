---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Skalenniveau und Kenngrößen
lernziele: [L8]
wiki: []
quellen: ["Fahrmeir, L. et al.: Statistik. Der Weg zur Datenanalyse, Kap. 2", "DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40"]
klausurrelevant: true
status: Pflicht
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/skalenniveau-und-kenngroessen.md:6a581567e769]
stand: 2026-11-27
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/skalenniveau-und-kenngroessen.md), erzeugt am 2026-11-27 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Skalenniveau und Kenngrößen

## In einem Satz

Das Skalenniveau eines Merkmals (nominal, ordinal, metrisch) bestimmt, welches Diagramm und welche Kenngröße sinnvoll sind; bei schiefen Verteilungen beschreibt der Median den typischen Fall, der Mittelwert das Gesamtvolumen.

## Warum das wichtig ist

Der Datentyp in einem Programm ist nicht das Skalenniveau: Eine Filialnummer ist eine Zahl, aber ein Name. Wer mit Filialnummern rechnet oder den Mittelwert eines schiefen Merkmals als „typisch“ berichtet, zieht falsche Schlüsse. Dieselbe Überlegung führt das Buch für Antwortzeiten: rechtsschief verteilt, deshalb Median und Perzentile statt Mittelwert ([Percentiles](percentiles.md)).

## Wie es funktioniert

| Skalenniveau | Beispiel im Übungsdatensatz | Diagramm | Kenngrößen |
|---|---|---|---|
| nominal (Namen, keine Reihenfolge) | Filialnummer, Aktionskennzeichen, Marke | Balken- oder Säulendiagramm, Kreisdiagramm bei wenigen Kategorien | Häufigkeiten, Modus |
| ordinal (Reihenfolge, keine gleichen Abstände) | Größen XS bis L, Preislage | Balken in der Reihenfolge | Median, Quantile |
| metrisch (Abstände oder Verhältnisse sinnvoll) | Verkaufspreis, verkaufte Stück, Datum (Differenzen sinnvoll) | Histogramm, Boxplot | Mittelwert, Median, Quantile |

Reihenfolge der Entscheidung: zuerst das Skalenniveau, dann das Diagramm, dann die Kenngröße.

Median gegen Mittelwert am Beispiel: Tagesmengen eines Artikels 1, 1, 2, 1, 5, 1, 3. Sortiert 1, 1, 1, 1, 2, 3, 5: Der Median ist der mittlere Wert, also 1. Der Mittelwert ist 14 geteilt durch 7, also 2. Der Ausreißer 5 verschiebt den Mittelwert, den Median nicht. Regel: erst die Verteilung ansehen, dann die Kenngröße wählen.

## Am Modehändler

Im Übungsdatensatz (12 Filialen, rund 400.000 Zeilen) hat die Tagesmenge je Variante und Filiale den Median 1 und den Mittelwert rund 1,6: Zwei Drittel der Verkaufstage bringen genau ein Stück, wenige Aktionstage bis 19 Stück. Der Median beschreibt den typischen Tag; der Mittelwert berücksichtigt das Gesamtvolumen und zählt für aggregierte Mengen. Als Planungszahl taugt er nicht: Eine echte Planung braucht Kalender-, Saison- und Aktionseffekte.

Besonderheit Sonntag: Im Rohdatensatz gibt es für Sonntage keine Zeile. Erst das Domänenwissen „Filialen geschlossen“ erlaubt, in einem vollständigen Kalender eine strukturelle 0 einzutragen. Das ist kein fehlender Wert und wird weder bereinigt noch durch Nachbarwerte ersetzt. Ein Kassenausfall an einem Dienstag sieht in den Daten gleich aus und ist ein fehlender Wert. Ob die 0 in eine Prognose eingeht, hängt davon ab, ob je Kalendertag oder je Öffnungstag prognostiziert wird.

## Trade-offs und Entscheidungsregel

- Typischer Fall: Median. Gesamtvolumen und Kapazität: Mittelwert. Ausreißer und Ziele: Perzentile.
- Nominale Merkmale nie als Zahlen behandeln, auch wenn sie als Zahl gespeichert sind.
- Vor jeder Kenngröße die Verteilung zeichnen; Schiefe sieht man im Histogramm sofort.

## Typische Fehlvorstellungen

- „int64 heißt metrisch.“ Die Filialnummer ist nominal.
- „Der Mittelwert ist die Planungssumme.“ Er berücksichtigt das Volumen, ersetzt aber keine Planung.
- „Keine Zeile heißt Wert 0.“ Ohne Domänenwissen ist der Wert unbekannt.

## Selbsttest

1. Welches Diagramm zeigt die Verteilung des Verkaufspreises angemessen: Kreisdiagramm, Histogramm, Liniendiagramm über die Artikelnummer oder Balkendiagramm der Filialen?
2. Tagesmengen 2, 1, 1, 6, 1, 2, 1: Median und Mittelwert?
3. Ein Händler prognostiziert je Öffnungstag. Wie behandelt er Sonntage in der Zielreihe?

<details><summary>Lösung</summary>

1. Histogramm; der Preis ist metrisch.
2. Sortiert 1, 1, 1, 1, 2, 2, 6: Median 1, Mittelwert 14 durch 7 gleich 2.
3. Ausschließen, wie Feiertage; bei einer Prognose je Kalendertag wäre die strukturelle 0 richtig.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Skalenniveau und Kenngrößen anhand der Seite `skalenniveau-und-kenngroessen.md` im Lernpaket und nenne mir dann vier Merkmale, die ich einordne; korrigiere nur, wo ich falsch liege.*
- *Gib mir sieben Tagesmengen mit einem Ausreißer. Ich bestimme Median und Mittelwert; du sagst mir nur, in welchem Schritt ein Fehler steckt.*

## Verwandt

- [Percentiles](percentiles.md)
- [Response Time](response-time.md)
- DataFrames
- [Star Schema](star-schema.md)

## Quelle und Weiterlesen

- Fahrmeir, L. et al.: Statistik. Der Weg zur Datenanalyse, Kap. 2 (deskriptive Statistik). Ergänzungsquelle dieser Lehrveranstaltung.
- DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40: dieselbe Argumentation für Antwortzeiten.
