# Big Data (BID) – FH CAMPUS 02, WS 2026/27

Begleitmaterial zur Lehrveranstaltung **Big Data** (Master IT & Wirtschaftsinformatik, FH CAMPUS 02, Lektor Herbert Mühlburger): ein **vollständig synthetischer** Einzelhandels-Datensatz und die Übungsnotebooks zum Öffnen in Google Colab.

## Notebooks

| Notebook | Termin | Colab |
|---|---|---|
| `notebooks/BID_NB1_TeilA.ipynb` – Datenexploration | T1 | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/muehlburger/bid-ws2026/blob/main/notebooks/BID_NB1_TeilA.ipynb) |

Weitere Notebooks (NB1 Teil B, NB2, NB3) kommen vor dem jeweiligen Termin dazu.

## Datensatz (`data/clean/`)

Synthetischer Warenwirtschafts-Export eines Modehändlers: 12 Filialen (Filiale 1 = Onlineshop), 800 Artikelvarianten, 1.7.2024–30.6.2026, 399.994 Zeilen. **Eine Zeile = Tagesumsatz einer Variante in einer Filiale.** Sonntage haben keine Zeile (Filialen geschlossen).

| Datei | Inhalt |
|---|---|
| `variantenumsatz.parquet`, `Variantenumsatz.csv.gz` | Faktentabelle (Umsatzzeilen); CSV mit `;` und Dezimalkomma |
| `Variante.csv`, `Filiale.csv`, `Warengruppe.csv`, `Hauptwarengruppe.csv`, `Abteilung.csv`, `Marke.csv`, `Saison.csv` | Stammdaten (Dimensionen) |

Wichtigste Spalten: `date_bestand_ums` (Buchungstag), `variantennummer8`, `filialnummer3`, `verkaufspreis_ifw` (regulärer Listenpreis), `umsatz_menge_mk9` (Stück, negativ = Retoure), `umsatz_wert_ifw` (Umsatz = Menge × regulärer Preis − Reduktionen), `kz_aktion` (A = Aktion, R = regulär).

Die Daten sind mit einem Generator erzeugt (Seed 42) und enthalten keine Kundendaten; Ähnlichkeiten mit realen Unternehmen sind zufällig.

## Lokal statt Colab

```bash
uv run --with pandas,pyarrow,matplotlib,jupyterlab jupyter lab
```
Notebook und die Dateien aus `data/clean/` nebeneinander ablegen – Zelle 1 findet die Dateien zuerst lokal, sonst lädt sie sie von hier.

© 2026 Herbert Mühlburger. Material für die Lehrveranstaltung; Fragen bitte über das Moodle-Forum der LV.
