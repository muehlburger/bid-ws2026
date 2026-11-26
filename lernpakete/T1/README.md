---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: readme
titel: "Lernpaket T1: Big Data als Architekturfrage, CRISP-DM, Datenexploration"
lernziele: [L1, L5, L8, L10]
wiki: [konzepte/entscheidungskette.md, konzepte/big-data-5v.md, konzepte/crisp-dm.md, konzepte/skalenniveau-und-kenngroessen.md]
quellen: ["DDIA 2e, Kap. 1 „Distributed Versus Single-Node Systems“ S. 19", "DDIA 2e, Kap. 2 „Defining Nonfunctional Requirements“ S. 33"]
klausurrelevant: true
sprache: de-AT
erzeugt: false
stand: 2026-11-26
version: 2
---

# Lernpaket T1: Big Data als Architekturfrage, CRISP-DM, Datenexploration

Termin 1 der Lehrveranstaltung Big Data (BID), Samstag, 28.11.2026, 10:30 bis 14:15, Raum RC403. Dieses Paket ist die Textfassung des Termins: Es enthält alles, was du für die Aufgaben, das Quiz Q1 und die Klausuritems zu T1 brauchst. Ein Buch brauchst du nicht; Verweise auf das Buch (Kleppmann/Riccomini, Designing Data-Intensive Applications, 2. Auflage) sind Lesehinweise.

## Was du nach T1 kannst

| Nr. | Du kannst … | Wo du es übst |
|---|---|---|
| L1 | eine Anforderung des Händlers einer der vier Qualitäten Performance, Reliability, Scalability, Maintainability zuordnen, die passende Messgröße wählen und Fault von Failure unterscheiden | Aufgabe 2, Items K1 und K2 |
| L5 | die sechs Phasen von CRISP-DM beschreiben und auf den Händler-Fall anwenden | Aufgabe 2, Items K3 und K4 |
| L8 | für einen Datensatz Skalenniveau, Kenngröße und Diagramm wählen, Median und Mittelwert berechnen und eine strukturelle 0 von einem fehlenden Wert unterscheiden | Übung Notebook, Items K5 und K6 |
| L10 | für ein Szenario Batch oder Stream und ein Rechner oder mehrere entscheiden, mit den vier Qualitäten begründen und die Bedingung nennen, unter der die andere Entscheidung richtig wäre | Aufgabe 1, Items K7 und K8 |

## Fahrplan des Termins

| Uhrzeit | Block | Inhalt | Lernziel | Agent |
|---|---|---|---|---|
| 10:30 | Start | Einstiegsfrage am Fall (Vorschlag um 6 Uhr, „noch 2 Stück in Graz“: wie alt dürfen die Daten sein?), Vorstellung, Arbeitsweise, Regeln, Gruppen bilden | – | – |
| 10:50 | Input 1 | Wann wird aus einem Datenproblem ein Architekturproblem? 5V, vier Qualitäten, Entscheidungskette, Batch oder Streaming | L1 | – |
| 11:07 | Aufgabe 1 | Vier Szenarien (S1 und S2 für alle, S3 und S4 Transfer), fünf Leitfragen, je Szenario ein Begründungssatz und eine Bedingung (Gruppe) | L10 | ohne |
| 11:32 | Musterlösung 1 | Auflösung entlang der Kette; Items K1 und K7 | L10 | – |
| 11:42 | Input 2 | CRISP-DM und das Case Canvas | L5 | – |
| 12:00 | Pause | Gruppenwahl in Moodle | – | – |
| 12:45 | Rückblick | Sechs Phasen ohne Unterlagen | L5 | ohne |
| 12:48 | Aufgabe 2 | Canvas-Felder 1 bis 3 für den Händler-Fall (Gruppe) | L1 | ohne |
| 13:10 | Musterlösung 2 | Musterbeispiel, häufige Fragen; Item K3 | L5 | – |
| 13:20 | Input 3 | Skalenniveau, Diagramm, Kenngröße; der Datensatz | L8 | – |
| 13:35 | Aufgabe 3 | Notebook NB1 Teil A, drei Fragen an den Datensatz (Paar) | L8 | ohne |
| 14:00 | Musterlösung 3 | Der Sonntag fehlt im Profil, Median gegen Mittelwert; Items K5 und K6 | L8 | – |
| 14:08 | Abschluss | Drei Sätze zur Einstiegsfrage, Quiz Q1, Gruppenwahl, Ausblick auf T2 | – | – |

Im Termin laufen alle drei Aufgaben ohne Agent, weil du zuerst die Arbeitsweise kennenlernst. Zu Hause gelten die drei Phasen aus [aufgaben.md](aufgaben.md): ohne Agent, mit Agent, ohne Agent.

## So lernst du mit diesem Paket

1. **Konzeptpfad lesen und Selbsttests machen.** [konzepte.md](konzepte.md) sagt dir, welche Seiten in `konzepte/` Pflicht sind und in welcher Reihenfolge. Jede Seite endet mit drei Selbsttestfragen.
2. **Aufgaben in drei Phasen bearbeiten.** [aufgaben.md](aufgaben.md) und [uebung-notebook.md](uebung-notebook.md): zuerst ohne Agent entscheiden oder rechnen, dann den Agenten prüfen lassen, dann ohne Agent etwas Neues wiedergeben. Die Selbstkontrolle steht am Ende jeder Datei.
3. **Zum Schluss ohne Agent:** [so-fragt-die-klausur.md](so-fragt-die-klausur.md). Erst lösen, dann mit den Lösungen vergleichen.

Richtwert für zu Hause: rund eine Stunde für dieses Paket, dazu Quiz Q1 in Moodle (10 bis 15 Minuten, beliebig wiederholbar, unbenotet). Der Gesamtaufwand des Selbststudiums liegt laut Beschreibung der Lehrveranstaltung bei rund fünf Stunden je Termin einschließlich Klausurvorbereitung.

## Dateien

| Datei | Inhalt |
|---|---|
| [konzepte.md](konzepte.md) | Konzeptpfad: welche Seite wann, Status Pflicht, Kern oder Ausblick |
| `konzepte/` | Konzeptseiten in eigenen Worten mit Beispiel am Modehändler und Selbsttest (erzeugt aus dem Wiki der Lehrveranstaltung) |
| [begriffe.md](begriffe.md) | Glossar: jeder Begriff in einem Satz (erzeugt) |
| [aufgaben.md](aufgaben.md) | Aufgabe 1 Szenarien und Aufgabe 2 Case Canvas mit Phasen, zwei Stufen und Selbstkontrolle |
| [uebung-notebook.md](uebung-notebook.md) | Aufgabe 3: praktische Übung mit dem Notebook, mit Papierfassung |
| [so-fragt-die-klausur.md](so-fragt-die-klausur.md) | die acht Beispielitems K1 bis K8 mit Lösungen |
| [prompts.md](prompts.md) | Rahmenprompt und Prompts für deinen Agenten |
| [T1_komplett.md](T1_komplett.md) | alles in einer Datei, zum Hochladen in deinen Agenten (erzeugt) |

Datensatz und Notebook liegen in diesem Repo unter `data/clean/` und `notebooks/`; der Einstieg steht in der [README des Repos](../../README.md).

## Regeln für den Agenten

Dein AI-Agent (Claude, ChatGPT oder ein anderer) ist Coach, nicht Ghostwriter: Er erklärt, prüft deine Begründung und fragt dich ab. In den Phasen „ohne Agent“ bleiben die Geräte zu, weil die Klausur ohne Agent läuft. Gib nie Daten deines Arbeitgebers in einen Agenten; der Modehändler und der synthetische Datensatz genügen für alles. Die ausführlichen Regeln stehen in der [AGENTS.md des Repos](../../AGENTS.md).
