---
lv: "Big Data (BID), FH CAMPUS 02, WS 2026/27"
termin: T1
datum: 2026-11-28
datei: konzept
titel: Maintainability
lernziele: [L1]
wiki: []
quellen: ["DDIA 2e, Kap. 2 „Maintainability“ S. 52", "DDIA 2e, Kap. 2 „Operability: Making Life Easy for Operations“ S. 53", "DDIA 2e, Kap. 2 „Evolvability: Making Change Easy“ S. 55"]
klausurrelevant: true
status: Kern
sprache: de-AT
erzeugt: true
erzeugt_aus: [wiki/konzepte/maintainability.md:3d7176c50343]
stand: 2026-11-25
version: 1
---
<!-- Auszug aus dem BID-Wiki (konzepte/maintainability.md), erzeugt am 2026-11-25 mit build_lernpaket.py. Nicht von Hand ändern. -->

# Maintainability

## In einem Satz

Maintainability (Wartbarkeit) beschreibt, wie leicht sich ein System über Jahre betreiben, verstehen und verändern lässt.

## Warum das wichtig ist

Software wird nicht einmal gebaut und ist dann fertig. Der größere Teil des Aufwands fällt nach der ersten Inbetriebnahme an: Fehler beheben, Betrieb sichern, an neue Anforderungen anpassen. Ein System, das niemand mehr anzufassen wagt, ist ein Geschäftsrisiko. Wartbarkeit ist die nichtfunktionale Anforderung, die am leichtesten vergessen wird, weil sie am ersten Tag nichts kostet.

## Wie es funktioniert

Wartbarkeit hat drei Seiten:

| Seite | Leitfrage | Was hilft |
|---|---|---|
| **Operability** (Betreibbarkeit) | Kann das Betriebsteam das System leicht am Laufen halten? | Überwachung und Einblick in das Laufzeitverhalten, keine Abhängigkeit von einzelnen Maschinen, gute Dokumentation, vorhersehbares Verhalten, sinnvolle Voreinstellungen |
| **[Simplicity](simplicity.md)** (Einfachheit) | Verstehen neue Leute das System? | bekannte Muster, gute Abstraktionen, keine unnötige Komplexität |
| **Evolvability** (Änderbarkeit) | Lässt sich das System an Unvorhergesehenes anpassen? | lose gekoppelte Teile, Schema Evolution, umkehrbare Schritte |

Zur Operability gehört eine Warnung: Automatisierung ist unverzichtbar, aber kein Selbstzweck. Was automatisch läuft, versteht irgendwann niemand mehr, und gerade die seltenen Sonderfälle bleiben am Menschen hängen.

Zur Evolvability nennt das Buch einen einfachen Prüfstein: Wie viele Entscheidungen lassen sich nicht rückgängig machen? Jede unumkehrbare Aktion macht Änderungen riskant. Das Buch dazu: „Minimizing irreversibility improves flexibility.“ (DDIA 2e, Kap. 2 „Evolvability: Making Change Easy“ S. 55)

## Am Modehändler

- Operability: Der Betrieb sieht auf einem Blick, ob alle 42 Filialen Buchungen liefern, und kann einen Server zur Wartung herausnehmen, ohne dass die Bestandsanzeige ausfällt.
- Simplicity: Die Absatzprognose läuft als ein nachvollziehbarer nächtlicher Lauf, nicht als Geflecht aus zwanzig Skripten.
- Evolvability: Ein neues Feld am Kassenbon, etwa ein Rabattcode, lässt sich einführen, ohne dass alle Kassen am selben Tag aktualisiert werden müssen, siehe Backward und Forward Compatibility. Die Umstellung der Kassendatenbank wird so geplant, dass ein Rückweg bleibt.

## Trade-offs und Entscheidungsregel

- Bei jeder Architekturentscheidung fragen: Wer betreibt das in fünf Jahren, und versteht diese Person es?
- Im Zweifel die einfachere Lösung wählen, auch wenn sie etwas langsamer ist.
- Unumkehrbare Schritte, etwa eine Datenmigration ohne Rückweg, als eigenes Risiko behandeln.
- Preis: Wartbarkeit kostet am Anfang Zeit für Dokumentation, Tests und saubere Schnittstellen; sie zahlt sich über die Lebensdauer aus.

## Typische Fehlvorstellungen

- „Wartbarkeit ist Sache der Entwicklung, nicht des Managements.“ Sie entscheidet über die laufenden Kosten.
- „Mehr Automatisierung ist immer besser.“ Nur so weit, wie das Team die Sonderfälle noch beherrscht.
- „Ein System, das läuft, ist wartbar.“ Ob es wartbar ist, zeigt sich erst bei der nächsten Änderung.

## Selbsttest

1. Nenne die drei Seiten der Maintainability.
2. Welche Eigenschaft von Entscheidungen erschwert Evolvability besonders?
3. Richtig oder falsch: Operability bedeutet, den Betrieb vollständig zu automatisieren.

<details><summary>Lösung</summary>

1. Operability, Simplicity, Evolvability.
2. Unumkehrbarkeit.
3. Falsch. Sie bedeutet, dem Betriebsteam die Arbeit leicht zu machen; Automatisierung ist ein Mittel mit Grenzen.

</details>

## Frag deinen AI-Agenten

- *Erkläre mir Maintainability anhand der Seite `maintainability.md` im Lernpaket: zuerst in drei Sätzen für eine Managerin, dann technisch für einen Engineer, jeweils am Modehändler.*
- *Ich beschreibe dir ein gewachsenes System in meiner Firma. Bewerte es mit mir entlang von Operability, Simplicity und Evolvability und nenne je Seite die erste Verbesserung.*
- *Stelle mir nacheinander drei Fragen zu Maintainability, warte jeweils auf meine Antwort und korrigiere sie nur anhand der Wiki-Seite; nenne die Stelle, auf die du dich stützt.*

## Verwandt

- [Simplicity](simplicity.md)
- Schema Evolution
- [Fault Tolerance](fault-tolerance.md)
- [Wegweiser Kapitel 2](kap-02.md)

## Quelle und Weiterlesen

- DDIA 2e, Kap. 2 „Maintainability“ S. 52
- DDIA 2e, Kap. 2 „Operability: Making Life Easy for Operations“ S. 53
- DDIA 2e, Kap. 2 „Evolvability: Making Change Easy“ S. 55
