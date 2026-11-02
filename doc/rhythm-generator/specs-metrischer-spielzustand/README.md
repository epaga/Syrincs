# Rhythmische Information aus Änderungen eines metrischen Spielzustands

Stand: 2. November 2026. **Fachliche Arbeitsfassung, nicht zur Implementierung
freigegeben.** Grundlage ist der im Chat übergebene Spezifikationsentwurf
mit den Kennungen Z01–C04 und den Abschnitten 16–18. Dessen Kennungen bleiben
hier als Herkunftsverweise erhalten. Keine neuen Ticketanforderungen.

Präzisierung des Projektinhabers: Als musikalische Bildvorlagen gelten
ausschließlich `IMG_2214.JPEG` und `IMG_2215.JPEG`. Andere Bildentwürfe
dokumentieren einen verworfenen Modellpfad und begründen keine Anforderungen.
London-Fundstellen sind davon getrennte Literaturquellen, keine weiteren
musikalischen Sollbeispiele.

Diese Fassung ergänzt den Entwurf um Codeabgleich, Bildprüfung,
Ereignistabellen, Quellenbefunde und Entscheidungsvorschläge. Sie ersetzt
keine ausdrückliche Entscheidung des Projektinhabers. Die bisherige
[Spezifikation](../specs-informationsmass/README.md) beschreibt weiterhin
das vorhandene `description-v1`; deren Regeln und Zahlen sind keine
Defaults dieses neuen Modells.

| Dokument | Zweck |
| --- | --- |
| [Fachlicher Vertrag](01-fachlicher-vertrag.md) | Festlegungen, Vorschläge und noch fehlende Regeln. |
| [Bildprüfung und Ereignisabläufe](02-bildpruefung-und-ereignisablaeufe.md) | Herkunft der Beispielwerte, explizite Zeiten und Gegenproben. |
| [Literatur und Erkennung](03-literatur-und-erkennung.md) | Geprüfte Fundstellen, Übertragungsgrenzen und Toleranzvorschlag. |

**Festgelegt** bedeutet im übergebenen Entwurf als Entscheidung des
Projektinhabers ausgewiesen. **Folgerung** ist eine überprüfbare Ableitung.
**Vorschlag** ist noch nicht angenommen. **Offen** verlangt eine Entscheidung.
**Forschungsauftrag** verlangt Untersuchung, ohne ein gewünschtes Ergebnis
vorwegzunehmen. Ein am Foto gelesener Wert bleibt ein **fachlicher
Ausgangswert**. Im Konflikt hat die informationsgünstigste hörbar
gleichwertige Interpretation Vorrang. Pausengliederungen allein begründen
keine Teilungsanweisungen. Jeder Prüffall benennt seine Klangbedingung:
zunächst **I – kurzer Impulsklang** oder **G – gehaltener Klang mit hörbarer
Abschaltung**. Hörbare Tonenden bleiben erhalten; weitere Artikulationen
werden später behandelt.

Ausbleiben eines aufgrund des geltenden Zustands erwarteten Ereignisses
ist selbst relevante Evidenz und kann `11` oder `01` begründen, ausdrücklich
auch unter I. Ein hörbares Tonende ist für `11` nicht notwendig. Für
F05.6.I mit Einsätzen bei 0 und 1 ist deshalb `10 11` als Kandidat mit
4 Bit zu berücksichtigen: `11` wird durch den ausbleibenden erwarteten
Einsatz bei 2 begründet. Ein vollständiger Minimalitätsnachweis wird damit
nicht behauptet.

## Geprüfter Repository-Stand

Aktueller F05-Durchgang: Branch `docs/metrischer-spielzustand-spezifikation`,
HEAD `835655ee26c40f54b3c7934c5f9e6cf153b559a0`; gegenüber dem genannten
Ausgangspunkt keine neueren Commits und keine Änderungen an versionierten
Dateien zu Arbeitsbeginn. Die übrigen unversionierten Fotos und
`projektanalyse/` bleiben unverändert. Die folgende Codeinventur beschreibt
weiterhin den historischen Implementierungsstand, nicht neue Produktionslogik.

Gelesener HEAD: `5eed42c610a392bc9da03e82ba34176100392460`, Arbeitsbranch
`docs/metrischer-spielzustand-spezifikation`. Der vom Entwurf genannte
Referenzbranch `feat/PROJEKT-verbesserung-rhythmus` steht auf `653cbdb`.
Der aktuelle Dokumentationsbranch enthält bereits die darauf aufbauende
Implementierung von `description-v1` (55 geänderte Dateien gegenüber der
gemeinsamen Basis). Diese Vorarbeit ist die Basis dieser Dokumentation;
es wurde kein Branchwechsel vorgenommen.

| Gegenstand | Aktueller Beleg und Unterschied zum neuen Ziel |
| --- | --- |
| Legacy-Analyse | [`HuffmanRhythm`](../../../src/main/java/syrincs/a_domain/rhythm/HuffmanRhythm.java): Symbolanzahl; Playing über Beats fortgeführt; Quarter pro Beat neu gesetzt. |
| Wörterbuch | Legacy `joinOnce=00`, `splitOnce=01`, `emitRestOn=10`, `emitNoteOn=11`: alle vier Bezeichnungen stehen gegenüber dem neuen Wörterbuch anders. `joinOnce` wird im aktuellen Ablauf nicht verwendet. |
| Vergleichsfälle | [`HuffmanRhythmTest`](../../../src/test/java/syrincs/a_domain/rhythm/HuffmanRhythmTest.java): vier Viertel = 1 Symbol; Foto-1-Onsets = 7 bzw. 9 Symbole. Eine Verdopplung ergäbe 14/18 statt der notierten 8/12 Bit. |
| Neue vorhandene Analyse | [`ExactDescriptionAnalyzer`](../../../src/main/java/syrincs/a_domain/rhythm/information/ExactDescriptionAnalyzer.java): EMPTY/FULL/LITERAL/REPEAT/CONCAT/PATCH. [`RhythmInformationAnalyzer`](../../../src/main/java/syrincs/a_domain/rhythm/information/RhythmInformationAnalyzer.java): globale, isolierte und kausale Blockbeschreibungen; kein hier spezifizierter Spielzustand. |
| Generator | [`GenerateRhythmsByInformationUseCase`](../../../src/main/java/syrincs/b_application/rhythm/information/GenerateRhythmsByInformationUseCase.java): binäre Masken bzw. Codewörter mit erneuter Analyse; kein Modell für hörbare Tonenden. |
| Eingaben | `Rhythm`/`OnsetSequence` bilden Onsets ab; RDL zusätzlich Voices und Gate. Kein MusicXML-/LilyPond-Import oder -Export unter `src/` bzw. in `pom.xml` gefunden. |
| MIDI | [`SequenceBuilder`](../../../src/main/java/syrincs/c_adapters/midi/SequenceBuilder.java): Note-Off aus einem Gate-Anteil je Rasterschritt; keine allgemeine Bindungs- und Dauersemantik einer Partitur. |
| OSC | [`SuperColliderOscOutputAdapter`](../../../src/main/java/syrincs/c_adapters/osc/SuperColliderOscOutputAdapter.java) bietet Noten-/Akkorddauer; Rhythmus-Playback läuft derzeit über MIDI. Transport ist noch kein gemeinsames Notationsmodell. |

Die Kernaussagen C02 stimmen am aktuellen Checkout. Zusätzlich existiert
die implementierte bitbasierte Analyse samt JSON-Verträgen. Beide bisherigen
Modelle müssen von einem neuen Modell unterscheidbar bleiben (C03 als
Vorschlag); bestehende CLI, Tabellen und Fixtures wurden hier nicht geändert.

Die Fotos und `projektanalyse/` lagen zu Arbeitsbeginn unversioniert vor.
Sie wurden nur gelesen. Dieser Auftrag hat keine konkrete Ticket-Kurz-ID;
historische Ticketverweise in gelesenen Dokumenten wurden nicht als neuer
Ticketauftrag behandelt. Kein Abruf oder Schreibzugriff auf Vikunja.

## Ergebnis und Freigabegrenze

Das neue Ziel ist **die Kostenfolge zeitlich erkannter Änderungen unter
einem etablierten metrischen Bezug**, mit Musikgenerierung als Produktziel.
Ein allgemeines Kompressionsminimum liefert dafür keine Ersatzdefinition.

Die 2-/3-Bit-Kosten und ihre Summe sind bestimmt, sobald eine Interpretation
feststeht. Noch nicht bestimmt sind insbesondere deren zeitliche Auswahl,
die gemeinsame Behandlung von Tonende und Ausbleiben sowie die Triolenerkennung.
Die Tabellen legen diese Lücken offen. Ein Implementierungsplan wäre vor
den noch offenen Entscheidungen D02–D06 des fachlichen Vertrags verfrüht.
D01 wurde präzisiert: Die Bildwerte sind Analysebeispiele. Beim Halbenbeispiel
wird `01` zu Beginn der zweiten Viertel aus dem ausbleibenden Offset erkannt;
der erste Einsatz hat bereits „Noten spielen“ bei bekanntem Viertelabstand gesetzt.

Weitere Bestätigungen: Im Punktierungsfall bleibt der erste Einsatz der
Zeitanker, auch nach `01` und `00 00`. Auf Foto 1 ist in beiden Beispielen
das erste `01` als Schreibfehler zu `00` korrigiert. Die korrigierten
Foto-Codefolgen lauten `10 00 00 01` (8 Bit) und `10 00 11 10 00 01` (12 Bit).
Diese Korrekturen sichern die Lesung, nicht die Optimalität der Beispielwerte
unter jeder Klangbedingung. Die Fallmatrix führt beide Klangbedingungen
und die daraus folgenden Äquivalenzprüfungen getrennt aus.

Die sieben einfachen F05-Figuren sind jetzt in
[Abschnitt 3 der Ereignisabläufe](02-bildpruefung-und-ereignisablaeufe.md#3-schrittweise-rechnung-f051f057-unter-i-und-g)
schrittweise unter I und G berechnet, einschließlich konkurrierender `11`-/
`01`-Pfade. Das dort benannte Rechenprofil K ist ausdrücklich unbestätigt.
Günstigste dargestellte Kosten vor einem zusätzlichen Abschluss: I/G
`2/2, 4/6, 6/6, 4/4, 6/6, 4/4, 4/4` für F05.1–F05.7, wenn eine
Anfangspause mit `11` initialisiert wird. Eine alternativ bis zum ersten
Ton uninitialisierte Analyse liegt bei F05.5/7 je 2 Bit darunter.
Dies sind keine nachgewiesenen Minima des noch unvollständigen Vertrags.

Der Durchgang zeigt außerdem einen fachlichen Konflikt: Im G-Vergleich
Halbe gegen Viertel plus hörbare Pause liefern `10 01` bzw. `10 11`
zunächst beide 4 Bit. Die ältere Forderung nach strikt höherem Wert
der Unterbrechung ist mit diesem Übergangsvorschlag nicht hergeleitet und
bleibt ausdrücklich zur Entscheidung offen. Anfangspause, dieser Konflikt
und Abschluss sind als drei priorisierte Rückfragen ausgearbeitet.

Geprüft wurden Dokumente, Produktionscode, einschlägige Testquellen,
beide Fotos und ausgewählte London-Originalscreenshots sowie ergänzende
Primärquellen. Kein neuer Softwaretestlauf und keine Audio-/DB-Abnahme:
Dieser Durchgang ändert ausschließlich fachliche Dokumente. Zusätzlich
wurden mit einer temporären Rechenhilfe 25 dargestellte K-Kandidaten
gegen die notierten Onsets, G-Tonenden und Befehlsummen sowie 21 explizite
Kostenformeln geprüft. Das prüft die angegebenen Pfade unter K, weder die
psychologische Gültigkeit der Zusatzannahmen noch vollständige Minimalität.
Markdown, lokale Linkziele und `git diff --check` wurden geprüft.
