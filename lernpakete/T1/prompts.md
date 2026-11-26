---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: prompts
titel: "Prompts für deinen Agenten zu T1"
lernziele: [L1, L5, L8, L10]
wiki: [konzepte/entscheidungskette.md]
quellen: []
klausurrelevant: false
sprache: de-AT
erzeugt: false
stand: 2026-11-25
version: 1
---

# Prompts für deinen Agenten zu T1

Alle Prompts sind für kostenlose Zugänge gedacht und funktionieren mit jedem Chat-Agenten. Gib dem Agenten zuerst die Datei [T1_komplett.md](T1_komplett.md) (Link zum Einfügen: https://raw.githubusercontent.com/muehlburger/bid-ws2026/main/lernpakete/T1/T1_komplett.md; hochladen, einfügen oder den Link nennen) und beginne mit dem Rahmenprompt. Platzhalter stehen in geschweiften Klammern. Du findest hier keine Prompts, die ein Ergebnis für dich erzeugen; schreiben, rechnen und entscheiden musst du selbst.

## Rahmenprompt

Einmal am Beginn jeder Sitzung:

> Du bist mein Lerncoach für die Lehrveranstaltung „Big Data“. Deine einzige Quelle ist die Datei `T1_komplett.md` aus dem Repo `muehlburger/bid-ws2026`, die ich dir gebe. Regeln: Erkläre kurz und am Beispiel des Modehändlers. Nenne zu jeder fachlichen Aussage die Datei oder Seite, auf die du dich stützt. Steht etwas nicht in der Quelle, sag „steht nicht im Lernpaket“. Sag mir keine Lösungen vor: Frag zuerst nach meinem eigenen Versuch. Lobe nichts, was falsch ist. Fachbegriffe bleiben Englisch, alles andere auf Deutsch. Ich schreibe am Ende eine Klausur ohne dich; hilf mir so, dass ich es dann allein kann.

## Erklären

| Nr. | Prompt |
|---|---|
| E1 | Erkläre mir {Begriff: Entscheidungskette, die vier Qualitäten, Fault und Failure, Batch und Stream, CRISP-DM, Median und Mittelwert} in fünf Sätzen am Beispiel des Modehändlers, ohne Fachjargon. Nenne die Seite, auf die du dich stützt. Stelle mir danach eine Frage, mit der ich zeige, ob ich es verstanden habe, und warte auf meine Antwort. |
| E2 | Erkläre mir {Begriff} zweimal: zuerst als Entscheidungsfrage für eine Geschäftsführerin (Was kostet es, was bringt es, wann nicht?), dann als Mechanismus für einen Entwickler (Was passiert Schritt für Schritt?). Je höchstens fünf Sätze. |
| E3 | Ich habe Velocity (Datenrate) und Timeliness (Aktualität) verwechselt. Stelle beide in einer Tabelle mit drei Zeilen gegenüber (Zweck, Preis, typischer Einsatz beim Modehändler) und nenne die häufigste Fehlvorstellung aus dem Lernpaket dazu. |
| E4 | Ich verstehe den Schritt {Schritt} in der Aufgabe {Aufgabe 1, 2 oder 3} nicht. Erkläre mir nur diesen Schritt an einem kleineren Beispiel mit anderen Zahlen. Rechne mein Beispiel nicht für mich. |

## Prüfen

| Nr. | Prompt |
|---|---|
| P1 | Hier ist meine Begründung für Szenario {S1, S2, S3 oder S4}: „{Text}“. Prüfe sie gegen die Entscheidungskette Anforderung, Datencharakteristik, Trade-off, Entscheidung. Sag mir, welcher Schritt fehlt oder nicht stimmt. Formuliere die verbesserte Begründung nicht für mich; ich schreibe sie selbst und zeige sie dir noch einmal. |
| P2 | Hier ist mein Rechenweg für Median und Mittelwert von {Zahlen}: {Rechenweg}. Sag mir nur, in welcher Zeile der erste Fehler steckt und welche Regel ich dort verletzt habe. Nenne das richtige Ergebnis nicht. |
| P3 | Ich erkläre dir jetzt {Begriff} in meinen eigenen Worten: „{Text}“. Bewerte in drei Punkten: Was stimmt, was fehlt, was ist falsch. Belege jeden Punkt mit der Seite aus dem Lernpaket. |
| P4 | Ich habe in Phase 1 der Übung geschätzt: „{Vorhersage}“. Das Notebook zeigt: {Ergebnis}. Hilf mir herauszufinden, warum meine Vorhersage abweicht, indem du mir zwei Fragen stellst. Erkläre erst, wenn ich beide beantwortet habe. |

## Abfragen

| Nr. | Prompt |
|---|---|
| A1 | Stelle mir fünf Fragen zu {Thema: Entscheidungskette, vier Qualitäten, Batch oder Stream, CRISP-DM, Skalenniveau} im Stil von `so-fragt-die-klausur.md`: Auswahl, Zuordnung, Reihung, Richtig/Falsch oder eine kleine Rechnung. Eine Frage nach der anderen, warte jeweils auf meine Antwort, löse dann auf und nenne die Seite. Verwende andere Zahlen und Szenarien als im Lernpaket. |
| A2 | Frag mich die Begriffe aus `begriffe.md` von T1 ab: Du nennst den Begriff, ich gebe die Definition in einem Satz, du sagst, ob der Kern stimmt. Begriffe, die ich nicht kann, kommen am Ende noch einmal. |
| A3 | Ich schreibe jetzt ohne nachzuschauen alles auf, was ich über {Thema} weiß. Vergleiche danach mit dem Lernpaket und nenne mir die drei wichtigsten Lücken, als Fragen formuliert, nicht als Antworten. |

## Gegenposition

| Nr. | Prompt |
|---|---|
| G1 | Ich habe entschieden: „{Entscheidung}“ für das Szenario {S1 bis S4}. Vertritt die Gegenposition, so überzeugend du kannst, mit Argumenten aus dem Lernpaket. Danach verteidige ich meine Entscheidung, und du sagst mir, welches Argument offen bleibt. |
| G2 | Nenne mir die Bedingung, unter der bei {Szenario} die andere Entscheidung richtig wäre. Ändere dazu genau eine Anforderung des Szenarios und frag mich, wie ich dann entscheide. |
| G3 | Unser Team will {Technologie: ein Cluster, Streaming, eine neue Plattform} einsetzen. Stell mir die Prüffrage der Lehrveranstaltung: Welches Problem zwingt uns zu dieser zusätzlichen Komplexität? Frag so lange nach, bis ich ein konkretes Problem nenne oder zugebe, dass es keines gibt. |

## Übertragen auf den Modehändler

| Nr. | Prompt |
|---|---|
| U1 | Gib mir eine neue Situation beim Modehändler (42 Filialen, Onlineshop, nächtliche Absatzprognose, Bestandsanzeige in Echtzeit), in der {Begriff} die entscheidende Rolle spielt. Beschreibe nur die Situation in vier Sätzen. Ich sage dir dann, was ich tun würde und warum. |
| U2 | Ich nenne dir ein Beispiel aus meinem Berufsalltag, ohne Firmennamen und ohne echte Daten: {Beispiel}. Hilf mir, es auf den Modehändler zu übersetzen: Was entspricht dort der nächtlichen Prognose, was der Bestandsanzeige? Welches Konzept aus T1 passt? |

## Regeln

- Agent erlaubt in den Phasen mit der Überschrift „mit Agent“. In den Phasen „ohne Agent“ sind Geräte zu.
- Deklaration auf jedem Blatt: „Agent verwendet: nein / ja, wofür: Erklären, Prüfen, Abfragen, Gegenposition, anderes.“ Unbenotet, ohne Folgen.
- Keine echten Firmendaten, Kundendaten, Personendaten oder Zugangsdaten in einen Agenten. Der synthetische Datensatz und der Modehändler genügen für alles.
- Quiz Q1: Versuch 1 ohne Agent und mit Zeitlimit, damit du siehst, wo du stehst. Weitere Versuche frei, mit Agent erlaubt, bitte deklarieren.
- Klausur und Probeklausur: ohne Agent.
