---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: uebung
titel: "Übung zu T1: Datenexploration mit dem Notebook NB1 Teil A"
lernziele: [L8]
wiki: [konzepte/skalenniveau-und-kenngroessen.md, konzepte/percentiles.md]
quellen: ["DDIA 2e, Kap. 3 „DataFrames, Matrices, and Arrays“ S. 105", "DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40"]
klausurrelevant: true
sprache: de-AT
erzeugt: false
stand: 2026-11-26
version: 2
---

# Übung zu T1: Datenexploration mit dem Notebook NB1 Teil A

## Worum es geht

Aufgabe 3 des Termins: drei Fragen an den synthetischen Datensatz des Modehändlers, gestellt in einem Notebook. Buchthema: DataFrames als Werkzeug der Datenanalyse (DDIA 2e, Kap. 3 „DataFrames, Matrices, and Arrays“ S. 105) und die Frage, welche Kenngröße eine schiefe Verteilung beschreibt (DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40). Problem des Händlers: Bevor jemand eine Prognose rechnet, muss er wissen, was eine Zeile bedeutet, wie die Mengen verteilt sind und warum der Sonntag fehlt. Lernziel L8: Skalenniveau, Kenngröße und Diagramm wählen; Median und Mittelwert berechnen; eine strukturelle 0 von einem fehlenden Wert unterscheiden. Dauer: 25 Minuten im Termin in Paaren, zu Hause rund 35 Minuten einschließlich Reflexion. Bedienung und Syntax sind nicht klausurrelevant; die Befunde und ihre Deutung schon.

## Was du brauchst

Nur einen Browser und ein Google-Konto für Colab. Startlink: https://colab.research.google.com/github/muehlburger/bid-ws2026/blob/main/notebooks/BID_NB1_TeilA.ipynb (Notebook `notebooks/BID_NB1_TeilA.ipynb` in diesem Repo). Die Daten liegen in `data/clean/` dieses Repos und werden von der ersten Zelle automatisch geladen. Colab ist freiwillig; wer es nicht nutzen will oder kann, arbeitet mit der Papierfassung unten und hat davon keinen Nachteil. Firmenlaptops sperren Colab oft; ein privates Gerät ist einfacher.

Der Datensatz ist vollständig synthetisch (keine Kundendaten), aber im Schema eines typischen Warenwirtschafts-Exports: 12 Filialen (Filiale 1 ist der Onlineshop), 800 Artikelvarianten, 1.7.2024 bis 30.6.2026, 399.994 Zeilen. Eine Zeile ist der Tagesumsatz einer Variante in einer Filiale.

| Spalte | Bedeutung |
|---|---|
| `date_bestand_ums` | Buchungstag |
| `variantennummer8` | Artikelvariante (Artikel, Größe, Farbe) |
| `filialnummer3` | Filiale (1 = Onlineshop) |
| `verkaufspreis_ifw` | regulärer Listenpreis je Stück in Euro |
| `umsatz_menge_mk9` | verkaufte Stück, negativ = Retoure |
| `umsatz_wert_ifw` | Umsatz in Euro = Menge mal regulärer Preis minus Reduktionen |
| `kz_aktion` | A = Aktionsverkauf, R = regulär |

## Phase 1 (ohne Agent): Vorhersage

Schreibe vor dem Start drei Schätzungen auf Papier:

1. Welcher Wochentag hat beim Modehändler die meisten verkauften Stück, welcher die wenigsten?
2. Wie viele Stück einer Variante werden an einem typischen Verkaufstag in einer Filiale verkauft: 1, 5 oder 20? Liegt der Mittelwert darüber oder darunter?
3. Die Filialnummer ist im Datensatz als ganze Zahl gespeichert. Ist sie deshalb ein metrisches Merkmal?

## Phase 2 (mit Agent): Schritte

Der Agent darf Befehle und Fehlermeldungen erklären (Prompt E4 aus [prompts.md](prompts.md)); die Eingaben stehen vollständig hier, du musst keinen Code erfinden. Die Antworten auf F1 bis F3 schreibst du selbst.

**Schritt 1: Zellen 1 bis 3 ausführen** (Pfeil links neben der Zelle). Zelle 1 lädt den Datensatz:

```python
df = pd.read_parquet(fetch("variantenumsatz.parquet"))
print("Rows and columns:", df.shape)
```

Erwartete Ausgabe: `Rows and columns: (399994, 26)`. Zelle 2 zeigt Zeitraum und Größe: `Period: 2024-07-01 to 2026-06-30`, `Stores: 12 | Variants: 800 | Days with sales: 602`. Zelle 3 verbindet die Umsätze mit den Filialstammdaten und summiert die Stück je Filiale; der Onlineshop (Filiale 1) ist mit 83.339 Stück der stärkste Kanal, danach St. Pölten mit 68.811 und Salzburg Süd mit 62.636. Daran siehst du, dass eine Filialnummer nur ein Name ist, hinter dem Stammdaten stehen.

**Schritt 2: F1, Skalenniveau und Diagrammwahl.** Die Zelle zeigt Datentypen und Beispielwerte:

```python
columns = ["filialnummer3", "verkaufspreis_ifw", "kz_aktion", "date_bestand_ums"]
print(df[columns].dtypes)
df[columns].sample(5, random_state=1)
```

Erwartete Ausgabe: `filialnummer3 int64`, `verkaufspreis_ifw float64`, `kz_aktion` und `date_bestand_ums` als Text. Beantworte in der Textzelle: Skalenniveau der vier Merkmale und das passende Diagramm für (a) Absatzmenge je Wochentag, (b) Verteilung des Verkaufspreises, (c) Anteil Aktions- gegen Normalverkäufe. Der Datentyp ist nicht das Skalenniveau.

**Schritt 3: F2, Median gegen Mittelwert.** Ersetze die beiden `___` durch die Methoden `.median()` und `.mean()`:

```python
sales = df[df["umsatz_menge_mk9"] > 0]
daily_qty = sales.groupby(["variantennummer8", "filialnummer3", "date"])["umsatz_menge_mk9"].sum()
median = ___   # daily_qty.<Methode>()
mean = ___     # daily_qty.<Methode>()
```

Erwartete Ausgabe: `Median: 1.0` und `Mean: 1.57`, dazu ein Histogramm der Tagesmengen (Mengen ab 10 zusammengefasst). Solange ein `___` offen ist, meldet die Zelle `not filled in yet` statt eines Fehlers. Beantworte: Warum unterscheiden sich die beiden Kenngrößen, und welche berichtest du als „typischen Tagesabsatz“?

**Schritt 4: F3, Wochentagsprofil.** Sieh dir zuerst das Ergebnis der Gruppierung an und ersetze dann das `___` durch `profile.reindex(range(7), fill_value=0)`:

```python
df["weekday"] = df["date"].dt.dayofweek          # 0 = Montag, 6 = Sonntag
profile = df.groupby("weekday")["umsatz_menge_mk9"].sum()
print(profile)                                     # Welcher Tag fehlt hier? Warum?
profile_all = ___
```

Erwartete Ausgabe der Gruppierung (Stück): Montag 76.742, Dienstag 85.190, Mittwoch 92.084, Donnerstag 83.282, Freitag 102.635, Samstag 125.881; der Sonntag (6) fehlt. `reindex(range(7))` allein trägt für den Sonntag NaN ein; erst `fill_value=0` setzt die 0, und das ist eine fachliche Entscheidung, keine Rechenregel. Beantworte: stärkster Tag, zweitstärkster, Sonntag fehlt, weil …, und was das für eine Prognose bedeutet. Überlege, woher du weißt, dass 0 die richtige Füllung ist, und ob das auch für den Onlineshop (Filiale 1) gilt.

**Zusatz für schnelle Paare: Preisverteilung.** Die Zelle läuft ohne Änderung:

```python
prices = df["verkaufspreis_ifw"]
print("Median:", prices.median(), "| Mean:", round(prices.mean(), 2), "| Minimum:", prices.min(), "| Maximum:", prices.max())
```

Erwartete Ausgabe: `Median: 38.95 | Mean: 44.63 | Minimum: 8.99 | Maximum: 182.95`, dazu Histogramm und Boxplot; die häufigsten Preise enden auf 95 (24,95 Euro am häufigsten). Benenne Preislagen und entscheide, ob Median oder Mittelwert den typischen Preis besser beschreibt.

## Wenn es nicht läuft (Papierfassung)

Dieselben Fragen mit den vorbereiteten Ergebnissen; damit sind alle Reflexionsfragen gleichwertig beantwortbar.

**F1:** Datentypen `int64`, `float64`, Text, Text. Beispielzeile: Filiale 6, Preis 37,95, Aktion R, Datum 2025-03-14.

**F2:** Tagesmenge je Variante und Filiale (nur Verkäufe, 379.890 Verkaufstage):

| Tagesmenge in Stück | Anteil der Verkaufstage |
|---|---|
| 1 | 66 Prozent |
| 2 | rund 20 Prozent |
| 3 bis 5 | rund 11 Prozent |
| 6 bis 19 | rund 3 Prozent (Aktionstage) |

Median 1, Mittelwert 1,57, Maximum 19.

**F3:** Verkaufte Stück je Wochentag über zwei Jahre:

| Wochentag | Stück |
|---|---|
| Montag | 76.742 |
| Dienstag | 85.190 |
| Mittwoch | 92.084 |
| Donnerstag | 83.282 |
| Freitag | 102.635 |
| Samstag | 125.881 |
| Sonntag | keine Zeile im Rohdatensatz |

**Zusatz:** Verkaufspreis Median 38,95 Euro, Mittelwert 44,63 Euro, Minimum 8,99 Euro, Maximum 182,95 Euro; Häufungen bei Preisen auf 95, der häufigste ist 24,95 Euro.

## Phase 3 (ohne Agent): Reflexion

Drei Fragen auf Papier, je zwei Sätze:

1. Welches Problem aus dem Buch löst das Werkzeug? (Was kann ein DataFrame, das eine Tabellenkalkulation nicht kann?)
2. Welche Komplexität kauft es ein?
3. Wann würde ich es nicht einsetzen?

Dazu die Wiedergabe mit neuen Zahlen: Tagesmengen 2, 1, 1, 6, 1, 2, 1. Bestimme Median und Mittelwert und sag, welche Kenngröße den typischen Tag beschreibt.

## Musterreflexion

1. **Problem:** Eine Tabelle mit 400.000 Zeilen (in der Geschichte 50 Mio.) nach Variante, Filiale und Tag zu gruppieren, Kenngrößen zu berechnen und zu zeichnen, wiederholbar und nachvollziehbar. Das Buch beschreibt DataFrames als das Werkzeug dafür in der Datenanalyse (DDIA 2e, Kap. 3 „DataFrames, Matrices, and Arrays“ S. 105); die Argumentation Median statt Mittelwert bei schiefen Verteilungen führt es für Antwortzeiten (DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40).
2. **Komplexität:** Code statt Klicks, eine Laufzeitumgebung (Colab, Konto), Datentypen, die nicht das Skalenniveau sind, und die Versuchung, einen fehlenden Tag unbesehen mit 0 zu füllen.
3. **Nicht einsetzen:** Für 84 Zeilen Stammdaten einmal im Jahr reicht die Tabellenkalkulation; für Sekundenaktualität im Shop ist ein Notebook das falsche Werkzeug, dort braucht es einen laufenden Dienst.

**Befunde:** F1: Filialnummer nominal (Zahl als Name), Verkaufspreis metrisch, Aktionskennzeichen nominal, Datum metrisch (Differenzen sinnvoll). Diagramme: (a) Säulendiagramm je Wochentag, (b) Histogramm oder Boxplot, (c) Balken- oder Kreisdiagramm mit zwei Kategorien. F2 (über beobachtete Verkaufstage je Variante und Filiale, nur Verkäufe mit Menge größer 0): Median 1, Mittelwert 1,57; rechtsschief, zwei Drittel der Verkaufstage ein Stück, wenige Aktionstage bis 19 Stück. Der Median beschreibt den typischen Tag; der Mittelwert berücksichtigt das Gesamtvolumen und zählt für aggregierte Mengen, taugt aber nicht als Planungszahl. F3: Samstag stärkster Tag, Freitag zweitstärkster, Montag schwächster Werktag. Für Sonntage gibt es im Rohdatensatz keine Zeile; erst das Domänenwissen „Filialen geschlossen“ erlaubt, sie im vollständigen Kalender als strukturelle 0 zu kodieren. Das ist kein fehlender Wert und wird weder bereinigt noch durch Nachbarwerte ersetzt; ein Kassenausfall am Dienstag sieht gleich aus und ist ein fehlender Wert. Für den Onlineshop (Filiale 1) fehlt der Sonntag ebenfalls; „geschlossen“ erklärt das nicht, dort muss die Buchungslogik des Exports es bestätigen. Ob die 0 in die Zielreihe eingeht, hängt davon ab, ob je Kalendertag (dann 0; ob der Wochentag die Prognose gegenüber einer einfachen Baseline verbessert, wird geprüft, nicht behauptet) oder je Öffnungstag (dann Sonntage ausschließen wie Feiertage) prognostiziert wird. Zusatz: rechtsschief mit Häufungen an psychologischen Preisen; der Median beschreibt den typischen Preis besser. Wiedergabe: sortiert 1, 1, 1, 1, 2, 2, 6, Median 1, Mittelwert 14 durch 7 gleich 2; der Median.

## Optional: lokal installieren

Im Termin nicht unterstützt. Wer lokal arbeiten will: `uv` installieren, dann im Ordner mit dem Notebook und den Dateien aus `data/clean/`:

```bash
uv run --with pandas==3.0.5 --with pyarrow==26.0.1 --with matplotlib==3.11.2 --with jupyterlab jupyter lab
```

Zelle 1 findet die Dateien zuerst lokal, sonst lädt sie sie aus diesem Repo.

## Quelle

DDIA 2e, Kap. 3 „DataFrames, Matrices, and Arrays“ S. 105; DDIA 2e, Kap. 2 „Average, Median, and Percentiles“ S. 40. Konzeptseiten im Paket: [Skalenniveau und Kenngrößen](konzepte/skalenniveau-und-kenngroessen.md), [Percentiles](konzepte/percentiles.md). Alle Zahlen stammen aus einem Lauf des Notebooks auf dem Datensatz in `data/clean/` dieses Repos (Stand 25.11.2026).
