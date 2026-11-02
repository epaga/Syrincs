# Bildprüfung und Ereignisabläufe

Status: [Rahmen](README.md), Regeln und Entscheidungskennungen:
[fachlicher Vertrag](01-fachlicher-vertrag.md). Zeiten sind Viertelpositionen
ab 0, Taktfenster zunächst `[0,4)`, Ausgangsabstand Δ=1. Keine Millisekunden-
oder Wahrnehmungsschwelle wird damit festgelegt. `N`/`P` bezeichnen Noten/
Pausen spielen, `U` den vorgeschlagenen uninitialisierten Zustand.

## 1. Prüfung der beiden Fotos

Originale: [IMG_2214.JPEG](<../Rhythmus Codierung Huffman Mitschrift/IMG_2214.JPEG>)
und [IMG_2215.JPEG](<../Rhythmus Codierung Huffman Mitschrift/IMG_2215.JPEG>).
Beide wurden am Bild betrachtet. Datum auf Foto 1 lesbar als 17. Okt. 25;
der durchgestrichene obere Wörterbuchentwurf wird nicht verwendet.
Das untere Wörterbuch passt zur bestätigten Fassung im Entwurf, trotz
überschriebener Zeichen bei den Spielbefehlen.

| Quelle | Lesung / Status |
| --- | --- |
| Foto 1, Rhythmus 1 | Notengruppen und ergänzende Onsets `xooo xoxo xoxx xxxo` passen. Sichtbar `10 01 00 01`, 8 Bit. Vom Projektinhaber ausdrücklich korrigiert: `10 00 00 01`. |
| Foto 1, Rhythmus 2 | Viertel, Achtelpause/Achtel, danach gleiche Gruppen; `xooo ooxo xoxx xxxo`. Sichtbar `10 01 11 10 00 01`, 12 Bit. Vom Projektinhaber ebenfalls ausdrücklich korrigiert: `10 00 11 10 00 01`. |
| Foto 2, sieben einfache Fälle | Codefolgen und Werte stimmen mit der übergebenen Tabelle überein. Die darunter wiederholte Notation unterstützt die Lesung der teils uneindeutigen Köpfe. |
| Foto 2, oben rechts | 22 Bit erkennbar; Bögen, überschriebenes Material und Zuordnung der Codes bleiben unsicher. Kein exakter Testfall. |

**Präzisierung des Projektinhabers:** Nur diese beiden Fotos sind musikalische
Referenzen; andere Bildentwürfe dokumentieren einen verworfenen Pfad. Die
notierten Werte sind vorrangig Analysebeispiele. Eine davorstehende Codegruppe
belegt nicht, dass die Höranalyse die Notendauer schon am Onset kennt.
Insbesondere wird die Halbe zu Beginn der zweiten Viertel am ausbleibenden
Offset erkannt. Die frühere Einordnung der Fotos als bloße Erzeugungswerte
wird zurückgenommen.

## 2. Sieben einfache Analysebeispiele: Notation und Foto-Code

Bei gehaltenem Klang sind neben den Einsätzen die Tonenden zu erhalten;
ein Übergang zu einem neuen Ton kann mit Ende des vorherigen zusammenfallen.
Bei Impulsklang sind die genannten Notenenden nicht automatisch Abschaltungen.
Der gemeinsame Endpunkt 4 wird hier separat als Rahmenende geführt.
Notation `a:b` bedeutet Einsatz bei a, notierte Dauer b.

| Fall | Noten / ausdrückliche Pause | Gelesene Codefolge auf dem Foto, ohne zugewiesene Erkennungszeiten | Notierter Analysewert |
| --- | --- | --- | ---: |
| F05.1 Vier Viertel | `0:1, 1:1, 2:1, 3:1` | `10` | 2 Bit |
| F05.2 Halbe, halbe Pause | `0:2`; Pause `[2,4)` | `01 10 11` | 6 Bit |
| F05.3 Halbe, zwei Viertel | `0:2, 2:1, 3:1` | `01 10 00` | 6 Bit |
| F05.4 Zwei Viertel, Halbe | `0:1, 1:1, 2:2` | `10 01` | 4 Bit |
| F05.5 Halbe Pause, Halbe | Pause `[0,2)`; `2:2` | `01 11 10` | 6 Bit |
| F05.6 Zwei Viertel, halbe Pause | `0:1, 1:1`; Pause `[2,4)` | `10 01 11` | 6 Bit |
| F05.7 Halbe Pause, zwei Viertel | Pause `[0,2)`; `2:1, 3:1` | `01 11 00 10` | 8 Bit |

Die Summe ist jeweils die Anzahl gezeigter Codes mal 2. Der Erkenntnisverlauf
wird davon getrennt zeitlich erläutert. Die Anfangshalbe erfordert kein
Zukunftswissen: Nach `10` gilt Viertelabstand; bei ausbleibendem Offset zu
Beginn der zweiten Viertel folgt `01`.

## 3. Zeitliche Höranalyse: was schon ableitbar ist

Für diese Tabellen gilt nur bedingt V03: Anker A bleibt bei Vergröberung
auf dem letzten bestätigten Einsatz und bei anschließender Verfeinerung
unverändert. Keine Nachforderung für zurückliegende neue Rasterpunkte.
Nach regulärem Einsatz wird die nächste Erwartung aus der fortgesetzten
Phase bestimmt. `τ` steht für eine ausdrücklich gewählte Ausbleibefrist;
`r=e+τ`. Ereignistoleranz ist davon getrennt. Die bestätigte symbolische
Halben-Erkennung am erwarteten Offset wird unten unmittelbar bei 1
angesetzt; sie wird nicht durch diesen Fristvorschlag ersetzt.

### Vier Viertel

| Musikalische Zeit | Tatsächliches / erwartetes Ereignis | Erkennungszeit | Zustand vorher → nachher | Anweisung / Kosten | Summe |
| --- | --- | --- | --- | --- | ---: |
| 0 | Erster Einsatz | 0 | `(U,1)→(N,1)`, nächste Erwartung 1 | `10`, 2 Bit | 2 |
| 1 | Einsatz wie erwartet | 1 | `(N,1)→(N,1)`, nächste 2 | keine | 2 |
| 2 | Einsatz wie erwartet | 2 | `(N,1)→(N,1)`, nächste 3 | keine | 2 |
| 3 | Einsatz wie erwartet | 3 | `(N,1)→(N,1)`, nächste 4 | keine | 2 |
| 4 | Bekannte Fenstergrenze | Rahmenbedingung | Keine Erwartung außerhalb des Fensters prüfen (V06) | keine automatische Schlussanweisung | 2 |

Tonenden und Neuanschläge an derselben Stelle dürfen nicht ungeprüft je
`11 10` erzeugen, sonst wäre das bestätigte Viertelbeispiel verletzt.
Die Regel für nahtlose Reartikulation muss diese Invariante erfüllen (D04).

### Halbe, zwei Viertel: zeitliche Analyse

| Bezugspunkt | Evidenz / bisherige Erwartung | Erkennungszeit | Zustandsvorschlag | Änderungskosten |
| --- | --- | --- | --- | ---: |
| 0 | Erster Einsatz, Länge noch nicht bekannt | 0 | `(U,1)→(N,1)`, erwartet 1 | `10`: 2 |
| 1 | Erwartetes Offset am Viertelende bleibt aus: Ton klingt weiter | 1, Beginn der zweiten Viertel | `(N,1)→(N,2)`, A=0, erwartet 2 | `01`: 2 |
| 2 | Einsatz wie erwartet | 2 | `(N,2)`, nächste Erwartung 4 | 0 |
| 3 | Offset des bei 2 begonnenen Tons und neuer Einsatz vor dem bisherigen Halbenende | 3 | `(N,2)→(N,1)`, A=2, Ereignis bei 3 passt | `00`: 2 |

Der bestätigte Anfang ist `10` bei 0, dann `01` bei 1. Mit der noch
zu prüfenden Rückkehrregel bei 3 ergibt sich `10 01 00` = 6 Bit. Die
Lesung `01 10 00` auf dem Foto bleibt als Quellenanordnung erhalten;
sie wird nicht als zeitliche Vorwegnahme der Halben interpretiert. Der
notierte Wert ist das Analysebeispiel, an dem die vollständige Regel
zu prüfen ist. Tonende und Neuanschlag bei 3 dürfen nicht ungeprüft
zusätzliche Spielmoduswechsel erzeugen.

### Übrige einfache Fälle: sichere Ereignisse und fehlende Regeln

| Fall | Geordnete Evidenz und Erkenntnis | Was noch keinen eindeutigen Hörwert besitzt |
| --- | --- | --- |
| Halbe, halbe Pause | `0:10`; bei 1 fehlt das erwartete Offset, daher `01`; bei 2 hörbares Tonende (gehaltener Klang) und unter Vergröberung erwarteter Einsatz fehlt. | Reihenfolge bzw. Konkurrenz `11`/`01` bei 2; reicht das Tonende zur Pause, oder weitere Vergröberung? |
| Zwei Viertel, Halbe | `0:10`, reguläre Viertel 0/1; Einsatz 2, erwartetes Offset bei 3 bleibt aus, daher `01` bei 3. | Der festgelegte Halbenfall ergibt `10 01` = 4. Klangende am Analyseende bleibt separat zu regeln. |
| Halbe Pause, Halbe | Anfang bis 2 ohne Ton, Einsatz 2; bei 3 bleibt bei gehaltenem Klang das Viertel-Offset aus. | Welche Erwartung besteht vor dem ersten Ton? Wann `11`, wann `01`? Danach Beginn der Notenregel. |
| Zwei Viertel, halbe Pause | `0:10`, Einsatz 1; Tonende bei 2 (gehaltener Klang), kein Einsatz bei 2. | Kann `11` die Auslassung erklären? Sind `01` und `11` beide nötig und wann? |
| Halbe Pause, zwei Viertel | Anfang ohne Ton; erster Einsatz 2, weiterer 3. | Anfangspausenregel; wenn Δ bis 2 bereits vergröbert wurde, wird die Rückkehr erst bei 3 erkannt. |

Das sind abgegrenzte Ableitungslücken, keine zu ersetzenden Fotozahlen.
Auch eine reine Pause besitzt ohne Anfangs- und Erwartungsregel noch
keinen verbindlichen Wert.

## 4. Punktierte Viertel plus Achtel

Noten `0:3/2, 3/2:1/2`; bekannte weitere Fortsetzung hier **nicht** festgelegt.
Nur den Abschnitt bis zum zweiten Einsatz betrachten. Der folgende Ablauf
nimmt `0 ≤ τ < 1/2` an und ordnet den Einsatz bei 3/2 nicht dem verspäteten
Viertel bei 1 zu. Beide Bedingungen sind zu wählende Modellparameter.

| Musikalischer Bezugspunkt | Tatsächlich / erwartet | Erkennung | Vorher → nachher | Neue Erwartung / Phase | Code | Kosten / kumuliert |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | Erster Einsatz | 0 | `(U,1)→(N,1)` | A=0; nächster Einsatz 1 | `10` | 2 / 2 |
| 1 | Erwartetes Viertel-Offset bleibt aus (gehaltener Klang) | 1 gemäß Präzisierung; zuvor vorgeschlagen war `1+τ` für einen fehlenden Onset | `(N,1)→(N,2)` | A=0; nächster Einsatz 2 | `01` | 2 / 4 |
| 3/2 | Tatsächlicher Einsatz vor 2 | 3/2 | `(N,2)→(N,1)` | A=0; 3/2 passt noch nicht auf das Viertelraster | erstes `00` | 2 / 6 |
| 3/2 | Dieselbe Evidenz, zweite nötige Verstärkung | 3/2 | `(N,1)→(N,1/2)` | A=0; 3/2 passt, nächste Erwartung 2 | zweites `00` | 2 / 8 |

Die Übertragung auf kurz ausklingende Schläge und das Verhältnis von
Offset-Erkennung und Onset-Frist bleiben zu klären. Für den gehaltenen
Ton gilt die präzisierte Offset-Erkennung bei 1.

Die beiden `00` sind ein durch dasselbe Ereignis begründeter Änderungsblock;
kein erfundener Zeitraum zwischen ihnen. Es bleiben **6 Bit Änderung** plus
**2 Bit erster Einsatz**. Die 6 sind aus der Diskussion abgeleitet, nicht
auf dem Foto notiert. Die alte Viertelerwartung und ihr bezahltes `01`
bleiben erhalten. Verfeinerung erzeugt nicht nachträglich Auslassungen
bei 1/2 oder 1. Keine automatische Rücksetzung an einer Beatgrenze.

**Bestätigt:** Der erste Einsatz bleibt Anker; nach `01` wird ein Einsatz
bei 2 erwartet. Der Einsatz bei 3/2 führt durch `00 00` zum Achtelabstand,
ohne den Anker zu verschieben. Die entsprechende Ankerführung in der
Tabelle ist damit für diesen Fall festgelegt.

**Noch offen:** Zuordnungsfenster und allgemeine Festschreiberegel.
Bei einer stattdessen verwendeten Onset-Ausbleibepolitik mit `τ ≥ 1/2`
kommt der zweite Einsatz vor oder zugleich mit deren Ausbleibeentscheidung. Dann ist dieselbe Anweisungsfolge nicht herleitbar.
Sie darf nicht trotzdem als universeller Wert ausgegeben werden. Über
Kosten nach 3/2 sagt diese Tabelle nichts: Das Ende bei 2 oder eine
Fortsetzung benötigen einen separaten Auftrag.

## 5. Foto 1: erster Rhythmus

Nach korrigierter Lesung Einsätze bei
`0,1,3/2,2,5/2,11/4,3,13/4,7/2`.
Mögliche **Erzeugung**: `10` bei 0, `00` bei 1, `00` bei 5/2,
`01` bei 7/2. Dies ergibt notierte 8 Bit, benötigt aber die Dauersemantik
aus Abschnitt 2: Die neue Teilung kann vor dem nächsten hörbaren Beleg
eingerichtet werden.

Eine mögliche **Hörrechnung für Impulsklang** mit kleinen, passend
gewählten Zuordnungsfenstern und `τ < 1/4` lautet:

| Evidenz | Erkennung | Δ vorher → nachher | Erwartung / Erklärung | Kosten / Summe |
| --- | --- | --- | --- | --- |
| Erster Einsatz 0 | 0 | 1→1 | N aktivieren; erwartet 1 | `10`: 2 / 2 |
| Regulärer Einsatz 1 | 1 | 1→1 | erwartet 2 | 0 / 2 |
| Zusätzlicher Einsatz 3/2 | 3/2 | 1→1/2 | mit Anker 1 passend; erwartet 2 | `00`: 2 / 4 |
| Einsätze 2 und 5/2 | jeweils beim Auftreten | 1/2→1/2 | regulär; danach erwartet 3 | 0 / 4 |
| Zusätzlicher Einsatz 11/4 | 11/4 | 1/2→1/4 | Anker 5/2; danach erwartet 3 | `00`: 2 / 6 |
| Einsätze 3,13/4,7/2 | jeweils beim Auftreten | 1/4→1/4 | danach erwartet 15/4 | 0 / 6 |
| Erwarteter Einsatz 15/4 fehlt | `15/4+τ < 4` | 1/4→1/2 | Anker 7/2; nächster Einsatz 4 liegt außerhalb | `01`: 2 / 8 |

Die Übereinstimmung der Summe mit dem Foto gilt nur unter diesen
Zusatzannahmen. Ein Analyseende direkt nach 7/2 oder eine bis über 4
reichende Frist liefert nicht denselben abgeschlossenen Nachweis.

Beim zweiten Rhythmus kommt das hörbare/notationsabhängige Pausengeschehen
bei 1 hinzu. Die bestätigte Korrektur der notierten Analysefolge lautet
`10 00 11 10 00 01` = 12 Bit. Hörseitig sind die Konkurrenz zwischen
Ausbleiben und `11` sowie Zeitpunkt und Phase des Wiederbeginns bei 3/2
noch offen. Daher hier keine angeblich exakte 12-Bit-Hörrechnung.

## 6. Weitere notwendige Gegenproben

| Prüffall | Zu entscheidende bzw. zu bewahrende Eigenschaft |
| --- | --- |
| Längeres Ausbleiben | Mit A=0 und Start Δ=1 wären neue Erwartungen nach je einem `01` bei 2,4,8… denkbar, mit anderem Anker andere Zeiten. Nicht bei jedem ursprünglichen Viertelschlag automatisch `01` zählen. |
| Orgel: Halbe vs. Viertel plus Viertelpause | Gleiches Onset, hörbares Ende bei 1 statt 2; darf nicht äquivalent normalisiert werden. Qualitative Ungleichung festgelegt, genaue Kosten brauchen D04. |
| Kurzer Impulsklang, gleiche Schreibweisen | Bei gleicher tatsächlicher Realisierung gleiche Bewertung; keine allein grafisch begründete Pause. |
| Bindung über die Taktgrenze | Kein neuer Einsatz aus bloßem Taktstrich. Zustand nicht automatisch zurücksetzen. |
| Neue Taktgrenze kurz vor einer Ausbleibefrist | Abschluss und zeitliche Erkennung dürfen sich nicht widersprechen. |
| Triole bei 0,1/3,2/3 | Zeitpunkt der Erkennung offen; erster Einsatz allein belegt keine Dreiteilung. Aktivierungsanweisung und 3-Bit-Wert noch Vorschläge. |
| Fortgesetzte Triole im nächsten Takt | Wörterbuch soll wieder 2 Bit sein, Abstand kann noch ternär sein. Welche Operation ist dann verfügbar und wann erneut aktivieren? |

Keiner dieser offenen Fälle wird durch einen Sollwert aus `description-v1`
oder eine Multiplikation des alten Symbolmaßes geschlossen.
