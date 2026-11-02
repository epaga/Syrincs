# Bildprüfung und Ereignisabläufe

Status: [Rahmen](README.md), Regeln und Entscheidungskennungen:
[fachlicher Vertrag](01-fachlicher-vertrag.md). Zeiten sind Viertelpositionen
ab 0, Taktfenster zunächst `[0,4)`, Ausgangsabstand Δ=1. Keine Millisekunden-
oder Wahrnehmungsschwelle wird damit festgelegt. `N`/`P` bezeichnen Noten/
Pausen spielen, `U` den vorgeschlagenen uninitialisierten Zustand.

**Klangbedingungen:** I = idealisierter kurzer Impulsklang; G = idealisierter
gehaltener Klang mit hörbarer Abschaltung, gemäß
[Vertrag, Abschnitt 1](01-fachlicher-vertrag.md#1-ziel-und-bekannte-bedingungen).
Die Foto-Tabelle ist Quelleninventar, kein klangunabhängiger Zahlenvertrag.
Jede Quellenfigur wird in Abschnitt 7 als eigener I- und G-Prüffall geführt.
Keine Dämpfung, variable Hüllkurve oder weitere Artikulation wird unterstellt.

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
notierten Werte sind fachliche Ausgangsbeispiele der Analyse. Bei einem
Konflikt hat die informationsgünstigste hörbar gleichwertige Interpretation
Vorrang. Eine davorstehende Codegruppe
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

### Vier Viertel – Klangbedingungen I und G, getrennt zu prüfen

I besitzt hier die Onsets 0,1,2,3; G zusätzlich die hörbaren Tonenden
1,2,3,4. Die inneren Tonenden fallen mit den Neuanschlägen zusammen.
Das Randereignis bei 4 bleibt im Ereignisprotokoll; seine Kostenbehandlung
ist Teil der noch offenen Abschlussregel. Die folgende 2-Bit-Rechnung
bezeichnet den Verlauf vor einer möglichen Abschlussanweisung.

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

### Halbe, zwei Viertel: zeitliche Analyse unter G

Onsets 0,2,3; hörbare Tonenden 2,3,4. Für I folgt die gesonderte Prüfung
in Abschnitt 7; die Offset-Begründung dieser Tabelle gilt dort nicht.

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

### Übrige einfache Fälle unter G: sichere Ereignisse und fehlende Regeln

| Fall | Geordnete Evidenz und Erkenntnis | Was noch keinen eindeutigen Hörwert besitzt |
| --- | --- | --- |
| Halbe, halbe Pause | `0:10`; bei 1 fehlt das erwartete Offset, daher `01`; bei 2 hörbares Tonende (gehaltener Klang) und unter Vergröberung erwarteter Einsatz fehlt. | Reihenfolge bzw. Konkurrenz `11`/`01` bei 2; reicht das Tonende zur Pause, oder weitere Vergröberung? |
| Zwei Viertel, Halbe | `0:10`, reguläre Viertel 0/1; Einsatz 2, erwartetes Offset bei 3 bleibt aus, daher `01` bei 3. | Der festgelegte Halbenfall ergibt `10 01` = 4. Klangende am Analyseende bleibt separat zu regeln. |
| Halbe Pause, Halbe | Anfang bis 2 ohne Ton, Einsatz 2; bei 3 bleibt bei gehaltenem Klang das Viertel-Offset aus. | Welche Erwartung besteht vor dem ersten Ton? Wann `11`, wann `01`? Danach Beginn der Notenregel. |
| Zwei Viertel, halbe Pause | `0:10`, Einsatz 1; hörbares Tonende bei 2, kein Einsatz bei 2. | `11` ohne zusätzliche Teilung als günstigere Variante prüfen. `01` ist durch die notierte halbe Pause allein nicht begründet. |
| Halbe Pause, zwei Viertel | Anfang ohne Ton; erster Einsatz 2, weiterer 3. | Anfangspausenregel; wenn Δ bis 2 bereits vergröbert wurde, wird die Rückkehr erst bei 3 erkannt. |

Das sind abgegrenzte Ableitungslücken. Fotozahlen dürfen bei einem
nachgewiesenen günstigeren hörbar gleichwertigen Ablauf abweichen.
Auch eine reine Pause besitzt ohne Anfangs- und Erwartungsregel noch
keinen verbindlichen Wert.

## 4. Punktierte Viertel plus Achtel unter G

Noten `0:3/2, 3/2:1/2`, hörbares Tonende und Neuanschlag bei 3/2;
das Tonende bei 2 ist als Randereignis zu erhalten. Bekannte weitere
Fortsetzung hier **nicht** festgelegt.
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

## 5. Foto 1: erster Rhythmus unter I

Nach korrigierter Lesung Einsätze bei
`0,1,3/2,2,5/2,11/4,3,13/4,7/2`.
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
Die Rechnung zeigt einen Kandidatenpfad, noch keinen Nachweis seiner
Minimalität unter allen zulässigen Interpretationen.

Beim zweiten Rhythmus fehlt unter I der Einsatz bei 1; aus seiner notierten
Achtelpause folgt kein zusätzliches hörbares Tonende. Unter G kommt dagegen
das hörbare Ende der ersten Viertel bei 1 hinzu. Die bestätigte Foto-Codefolge
lautet `10 00 11 10 00 01` = 12 Bit. Beide Klangfälle sind separat zu
analysieren; insbesondere darf die Pausengliederung in I keinen `00`-Befehl
erzwingen. Die genaue günstigste Hörrechnung ist noch zu bestimmen.

## 6. Weitere notwendige Gegenproben

| Prüffall | Klangbedingung | Zu entscheidende bzw. zu bewahrende Eigenschaft |
| --- | --- | --- |
| Längeres Ausbleiben | I; in G als eigener Fall mit explizitem Tonende | Mit A=0 und Start Δ=1 wären neue Erwartungen nach je einem `01` bei 2,4,8… denkbar, mit anderem Anker andere Zeiten. Nicht bei jedem ursprünglichen Viertelschlag automatisch `01` zählen. |
| Halbe vs. Viertel plus Viertelpause | G | Gleiches Onset, hörbares Ende bei 1 statt 2; darf nicht äquivalent normalisiert werden. Qualitative Ungleichung festgelegt, genaue Kosten brauchen D04. |
| Halbe vs. Viertel plus Viertelpause | I | Bei gleichen Impulsen gleiche Bewertung; keine allein grafisch begründete Pause. |
| Bindung über die Taktgrenze | G | Klang hält über die Grenze; kein neuer Einsatz aus bloßem Taktstrich. Zustand nicht automatisch zurücksetzen. |
| Neue Taktgrenze kurz vor einer Ausbleibefrist | I | Abschluss und zeitliche Erkennung dürfen sich nicht widersprechen. |
| Triole bei 0,1/3,2/3 | I | Zeitpunkt der Erkennung offen; erster Einsatz allein belegt keine Dreiteilung. Aktivierungsanweisung und 3-Bit-Wert noch Vorschläge. |
| Fortgesetzte Triole im nächsten Takt | I | Wörterbuch soll wieder 2 Bit sein, Abstand kann noch ternär sein. Welche Operation ist dann verfügbar und wann erneut aktivieren? |

Keiner dieser offenen Fälle wird durch einen Sollwert aus `description-v1`
oder eine Multiplikation des alten Symbolmaßes geschlossen.

## 7. Verbindliche Klangzuordnung und Äquivalenzprüfung der Ausgangsfiguren

Jede Tabellenzeile steht für **zwei getrennte Prüffälle**, mit Suffix `.I`
und `.G`. Zeitangaben sind exakt idealisierte Notationszeiten. Unter I
haben alle Impulse dieselbe kurze natürliche Hüllkurve, unabhängig von
notierter Dauer/Pausenaufteilung. Unter G wird bis zum jeweiligen Ende
gehalten und dort hörbar abgeschaltet. Die Enden sind vollständig
aufzulisten, auch wenn sie mit einem neuen Onset oder der Fenstergrenze
zusammenfallen; daraus folgt noch keine zusätzliche Kostenanweisung.

| Fall | I: relevante Onsets | G: dieselben Onsets plus hörbare Enden | Ableitung / noch nötige Auswahl |
| --- | --- | --- | --- |
| F05.1 | 0,1,2,3 | 1,2,3,4 | Fortsetzung der Viertelregel; innere nahtlose Reartikulation begründet kein zusätzliches `11 10`. |
| F05.2 | 0 | 2 | I: keine aus der halben Pause abgeleitete Abschaltung. G: fehlendes Offset bei 1 begründet `01`; Ende bei 2 muss erhalten bleiben. Ein möglicher `11` ist mit diesem hörbaren Ende zu begründen. |
| F05.3 | 0,2,3 | 2,3,4 | G: Ablauf in Abschnitt 3. I: fehlender Onset bei 1, nicht fehlendes Offset, ist Gegenstand der Erkennungspolitik. |
| F05.4 | 0,1,2 | 1,2,4 | G: ausbleibendes Offset bei 3 begründet `01`. I: gleiche Onsets wie drei Viertel plus Viertelpause; beide Schreibweisen müssen gleich bewertet werden. |
| F05.5 | 2 | 4 | Anfangspause offen. In I gleiche hörbare Folge wie eine Viertel bei 2 mit anschließender Viertelpause; notierte Halbenlänge selbst keine hörbare Evidenz. G: Klang von 2 bis 4 erhalten. |
| F05.6 | 0,1 | 1,2 | In beiden Fällen keine Teilung allein aufgrund der halben Pause. G: Enden bei 1 und 2 erhalten, Ende bei 2 erklärt den Beginn der anschließenden Stille. |
| F05.7 | 2,3 | 3,4 | Die anfängliche halbe Pause erzeugt für sich kein `01`; folglich ist auch kein nur dadurch erforderliches `00` zu erzwingen. Anfangsmodus und anschließende Einsätze müssen erklärt werden. |
| F03, Foto 1 / 1 | 0,1,3/2,2,5/2,11/4,3,13/4,7/2 | 1,3/2,2,5/2,11/4,3,13/4,7/2,4 | I: Kandidatenrechnung in Abschnitt 5. G: dieselben Onsets, zusätzlich jedes notierte Ende erhalten; keine Übernahme eines I-Werts ohne Prüfung. |
| F04, Foto 1 / 2 | 0,3/2,2,5/2,11/4,3,13/4,7/2 | 1,2,5/2,11/4,3,13/4,7/2,4 | G: hörbare Lücke von 1 bis 3/2. I: notierte Achtelpause führt kein eigenes Abschaltereignis ein. 12 Bit sind Ausgangswert, nicht in beiden Fällen zu erzwingen. |
| P01, Punktierung | 0,3/2 | 3/2,2 | G: bestätigte Ankerführung und Offset-Ablauf aus Abschnitt 4. I: gleiche Ankerbedingung, aber eigener Nachweis der Onset-Ausbleibeerkennung nötig. |

**Pausengliederung als direkte Gegenprobe:** Zu F05.6.I und F05.6.G wird
je eine zweite Notation mit zwei Viertelpausen statt einer halben Pause
in `[2,4)` geprüft. Unter beiden Klangbedingungen bleiben die Ereignisse
identisch; Informationswert und zulässige günstigste Interpretation dürfen
sich allein dadurch nicht ändern. Entsprechend gilt dies für F05.7.I/G
mit zwei Viertelpausen statt der Anfangshalbpause.

**Konkreter Konflikt mit einem Foto-Ausgangswert:** Für F05.6.G ist der
Kandidatenpfad `10` bei 0, Fortsetzung bei 1, `11` bei 2 **ohne** `01`
zu prüfen. Seine Befehle kosten 4 statt der notierten 6 Bit. Wenn `11`
das hörbare Ende und die folgende Stille unter der beschlossenen
Übergangsregel vollständig erklärt, hat dieser günstigere Pfad Vorrang.
Das `01` lässt sich nicht mit „halbe Pause“ begründen. Dies ist eine
konkrete Minimalitätsprüfung, noch kein vorweggenommener Nachweis, dass
4 Bit unter allen noch offenen Übergangs- und Abschlussregeln das Minimum sind.

**Daueräquivalenz als direkte Gegenprobe:** In einem gemeinsamen Fenster
`[0,2)` werden `0:2` und `0:1` mit Pause `[1,2)` verglichen. Unter I ist
die Realisierung identisch, der Informationswert muss gleich sein. Unter G
endet der Klang einmal bei 2, einmal bei 1. Diese Enden dürfen nicht
gleichgesetzt werden; die früher festgelegte qualitative Mehrinformation
der tatsächlich hörbaren Unterbrechung bleibt zu erfüllen.

**Prüfstatus:** Ereignismengen und Äquivalenzanforderungen sind hier
ausgearbeitet. Wo Initialisierung, Zustandsübergang oder Abschluss noch
offen sind, wird der Zahlenwert nicht aus der Fotozahl ergänzt. Ein
billigerer Pfad muss alle relevanten hörbaren Ereignisse und den zulässigen
Erkenntnisverlauf erhalten. Eine feste Verpflichtung auf Fotozahlen wäre
ebenso falsch wie das Entfernen eines hörbaren Endes zur Kostenersparnis.
