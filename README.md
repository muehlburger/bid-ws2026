# Big Data (BID): Datenintensive Systeme verstehen

Begleitmaterial zur Lehrveranstaltung **Big Data** (Master IT & Wirtschaftsinformatik, FH CAMPUS 02, WS 2026/27, Lektor Herbert Mühlburger). Alles hier ist dafür gebaut, dass du es allein oder mit deinem AI-Agenten (Claude, ChatGPT oder ein anderer) durcharbeiten kannst. Du brauchst kein Buch.

## Wofür das alles

Am Ende zählt die Klausur in Moodle, ohne Agent. Dein Agent ist hier Coach, nicht Ghostwriter: Er erklärt, prüft deine Begründung und fragt dich ab. Schreiben, rechnen und entscheiden musst du selbst, sonst merkst du es in der Klausur.

## So startest du

1. Öffne das Lernpaket des Termins: [`lernpakete/T1/README.md`](lernpakete/T1/README.md); T2 bis T5 kommen je eine Woche vor dem Termin dazu.
2. Mit Agent: Gib ihm die Datei `lernpakete/Tn/Tn_komplett.md` (hochladen, einfügen oder den Link nennen) und beginne mit dem Rahmenprompt aus `lernpakete/Tn/prompts.md`.
3. Ohne Agent: Lies den Konzeptpfad (`konzepte.md`), mach die Selbsttests auf den Konzeptseiten, bearbeite `aufgaben.md` und vergleiche mit der Selbstkontrolle am Ende der Datei.
4. Zum Schluss immer ohne Agent: `so-fragt-die-klausur.md`.

## Termine und Lernpakete

| Termin | Datum | Thema | Lernpaket | Werkzeug | Quiz |
|---|---|---|---|---|---|
| T1 | Sa 28.11.2026 | Big Data als Architekturfrage, CRISP-DM, Datenexploration | [`lernpakete/T1/`](lernpakete/T1/README.md) | Notebook NB1 Teil A | Q1 |
| T2 | Sa 12.12.2026 | Verlässliche und änderbare Daten: Datenqualität, System of Record, CSV oder Parquet | folgt | DuckDB und Parquet | Q2 |
| T3 | Sa 19.12.2026, online | Die Prognose und ihre Verantwortung: Machine Learning als Batch-Schritt, Recht und Ethik | folgt | C4-Modell im Browser | Q3 |
| T4 | Fr 08.01.2027 | Wachstum und Geschwindigkeit: verteiltes Dateisystem, MapReduce, Antwortzeiten | folgt | Pipeline als DAG | Q4 |
| T5 | Fr 15.01.2027 | Echtzeit und Architekturentscheidung: Stream Processing, Probeklausur | folgt | Kafka | Q5 |
| Klausur | Fr 22.01.2027 | Moodle-Test, 100 % der Beurteilung | – | – | – |

Die Lernziele L1 bis L10 der Lehrveranstaltung stehen in [`AGENTS.md`](AGENTS.md).

## Drei Prompts für den Anfang

- Erklären: „Lies `lernpakete/T1/T1_komplett.md`. Erkläre mir {Begriff} in fünf Sätzen am Beispiel des Modehändlers. Nenne die Seite, auf die du dich stützt. Stelle mir danach eine Frage, mit der ich zeige, dass ich es verstanden habe.“
- Prüfen: „Hier ist meine Begründung: {Text}. Prüfe sie gegen die Entscheidungskette Anforderung, Datencharakteristik, Trade-off, Entscheidung. Sag mir, welcher Schritt fehlt oder falsch ist, aber formuliere die Lösung nicht für mich.“
- Abfragen: „Stelle mir fünf Fragen zu {Thema} im Stil von `so-fragt-die-klausur.md`, eine nach der anderen. Warte jeweils auf meine Antwort, bevor du auflöst.“

Mehr Prompts stehen im Lernpaket jedes Termins.

## Regeln

- Agent erlaubt in den gekennzeichneten Phasen der Aufgaben und in den Quizzen; gib auf dem Blatt an, wofür du ihn verwendet hast. Das ist unbenotet.
- Klausur und Probeklausur: ohne Agent.
- Gib nie echte Firmendaten, Kundendaten oder Zugangsdaten in einen Agenten ein. Für alle Aufgaben genügt der synthetische Datensatz in `data/clean/`.

## Notebooks

| Notebook | Termin | Colab |
|---|---|---|
| `notebooks/BID_NB1_TeilA.ipynb` – Datenexploration | T1 | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/muehlburger/bid-ws2026/blob/main/notebooks/BID_NB1_TeilA.ipynb) |

Weitere Notebooks (NB1 Teil B, NB2, NB3) kommen vor dem jeweiligen Termin dazu.

## Datensatz (`data/clean/`)

Synthetischer Warenwirtschafts-Export eines Modehändlers: 12 Filialen (Filiale 1 = Onlineshop), 800 Artikelvarianten, 1.7.2024 bis 30.6.2026, 399.994 Zeilen. **Eine Zeile = Tagesumsatz einer Variante in einer Filiale.** Sonntage haben keine Zeile (Filialen geschlossen).

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
Notebook und die Dateien aus `data/clean/` nebeneinander ablegen; Zelle 1 findet die Dateien zuerst lokal, sonst lädt sie sie von hier.

## Quelle und Rechte

Die Konzepte folgen Martin Kleppmann und Chris Riccomini, Designing Data-Intensive Applications, 2. Auflage, O'Reilly 2026. Alle Texte hier sind eigene Erklärungen mit eigenen Beispielen; Verweise ins Buch sind Lesehinweise.

© 2026 Herbert Mühlburger, AI-Trust ZT GmbH.

- **Inhalte und Daten** (Texte, Lernmaterial, der synthetische Datensatz in `data/`): [Creative Commons Namensnennung, Weitergabe unter gleichen Bedingungen 4.0 International (CC BY-SA 4.0)](LICENSE-CONTENT). Namensnennung: „Herbert Mühlburger, Big Data (BID), FH CAMPUS 02, WS 2026/27“ mit Link auf dieses Repository.
- **Code** (Code-Zellen der Notebooks, Skripte): [Apache License 2.0](LICENSE).
- Nicht Teil der Lizenz: Logos und Marken sowie gekennzeichnete Zitate aus fremden Quellen.

Fragen zur Lehrveranstaltung bitte über das Moodle-Forum der LV.
