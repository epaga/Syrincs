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
Die sieben einfachen Quellenfiguren werden in Abschnitt 3 jeweils unter I
und G durchgerechnet; weitere Klangvergleiche stehen in Abschnitt 7.
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
wird davon getrennt zeitlich erläutert. Unter G erfordert die Anfangshalbe kein
Zukunftswissen: Nach `10` gilt Viertelabstand; bei ausbleibendem Offset zu
Beginn der zweiten Viertel folgt `01`. Unter I ist hingegen die
Onset-Ausbleibeerkennung zu prüfen.

## 3. Schrittweise Rechnung F05.1–F05.7 unter I und G

Bearbeitungsbasis dieses Durchgangs: `835655ee26c40f54b3c7934c5f9e6cf153b559a0`.
`IMG_2215.JPEG` wurde erneut am Bild geprüft. Die Quellenlesung in Abschnitt 2
bleibt erhalten; sie bestimmt weder Erkenntnisreihenfolge noch Minimum.

### 3.1 Gemeinsamer Rahmen und ausdrücklich unbestätigte Rechenannahmen

Alle vierzehn Fälle haben Beobachtungsfenster `[0,4)`, bekannten 4/4-Bezug,
Viertelabstand Δ=1 und keine mitgelieferte Vorgeschichte. I besitzt nur die
angegebenen Impulse als variable Evidenz. G besitzt zusätzlich alle genannten
hörbaren Abschaltungen. Keine menschlichen Timingabweichungen werden
hinzuerfunden. `r_e` bezeichnet die noch festzulegende Erkennung einer bei e
unerfüllten Erwartung; e und r_e sind verschiedene Angaben. Für die
hier dargestellten aufeinanderfolgenden Entscheidungen wird ausdrücklich
angenommen, dass r_e vor dem nächsten relevanten Ereignis liegt. Liegt die
Erkennung später, ist der jeweilige Pfad nur ein bedingtes Ergebnis.
Keine Millisekundenfrist wird festgelegt. Fehlende G-Offsets im bestätigten
Halbenfall werden gemäß Projektinhaber am musikalischen Viertelende erkannt.

**Rechenprofil K, Vorschlag und kein neuer verbindlicher Vertrag:**

- **K-A (Phase):** Für diese sieben rastergebundenen Rechnungen bleibt A=0.
  Neue Erwartungen liegen auf diesem Gitter; nach Änderungen werden nur
  gegenwärtige/künftige Positionen berücksichtigt. Die allgemeine Übernahme
  dieses Ankers ist unbestätigt. Eine Gegenrechnung mit einem anderen Anker
  steht bei F05.6; der bestätigte Punktierungsanker wird nicht verändert.
  Ein durch Ausbleiben begründetes `01` erzeugt keinen Einsatz am gerade
  unerfüllten Zeitpunkt, auch wenn dieser auf dem neuen Gitter liegt:
  Der Ausfall ist Anlass der Änderung und bereits bezahlt. Die nächste
  Onset-Erwartung liegt danach; beispielsweise bei F05.6.I nach dem
  Ausbleiben bei 2 und Δ=2 erst bei 4. Dies ist Teil von K-A, keine
  nachträgliche kostenlose Tilgung der Ausbleibeevidenz.
- **K-P (Pausenzustand):** P unterdrückt erwartete neue Töne, erhält aber Δ
  und A. Es gibt Pausenrasterpunkte, jedoch keinen Klang an ihnen und keine
  kostenpflichtige Wiederholung von `11`. Ein passender neuer Einsatz kann
  mit `10` auf demselben Gitter zurückkehren. Ohne diese Ergänzung wäre die
  geforderte Fortwirkung von P noch nicht ausführbar beschrieben.
- **K-G (Dauer):** In N ist bei G neben dem nächsten Einsatz ein Tonende
  nach Δ erwartet. Nahtloses Ende mit regulärem Neuanschlag ist Fortsetzung,
  kein `11 10`. Ein isoliertes hörbares Ende kann durch `11` erklärt werden.
  P bei weiter hörbar gehaltenem Ton ist unzulässig. Dieser konkrete
  Übergangsvorschlag ist zu bestätigen; er ergänzt die bereits festgelegte
  Erhaltung hörbarer Enden und Halben-Erkennung.
- **K-E (Ende):** Zahlen bezeichnen die Anweisungen für `[0,4)` vor einer
  eventuellen zusätzlichen Abschlussanweisung. Keine Auslassung bei 4 wird
  angenommen. Hörbare G-Enden bei 4 werden trotzdem im Randprotokoll erhalten.
  Sie werden weder gelöscht noch hier schon mit einer erfundenen
  Abschlussgebühr versehen. Fortsetzung ab 4 wäre ein weiterer Auftrag.
- **K-S (Beginn):** Für Anfangspausen werden zwei Varianten gerechnet:
  **S+** erklärt den Anfangszustand ausdrücklich mit `11` (2 Bit);
  **SU** belässt U bis zum ersten Einsatz ohne vorherige Spielerwartung.
  SU ist eine offene Initialisierungsalternative, kein stillschweigend
  kostenloser Pausenzustand und kein Zustandsreset. Der erste Einsatz
  kostet in beiden Varianten immer `10`. Vorschlag: S+, damit auch der
  Beginn als musikalischer Zustand ausdrücklich initialisiert wird.

Die Tabellen verwenden `M/Δ/A/e`. e ist bei N die nächste Onset-Erwartung,
bei G zugleich das erwartete nächste Tonende nach K-G. `P:3` bedeutet nur
Pausenrasterpunkt 3, **keinen erwarteten Onset oder erneuten Abschaltvorgang**.
`U/1/0/–` hat noch keine Spielerwartung. Bei G stehen gleichzeitige
Abschaltung und Neuanschlag zusammen in der Evidenzspalte. Alle Befehle
kosten hier 2 Bit. Zustand und Kosten werden pro Variante getrennt geführt;
keine Variante erbt die bereits bezahlten Befehle eines anderen Pfads.
Innerhalb eines Pfads bleiben erkannte Änderungen erhalten.

**Wertstatus:** Fotozahl = Ausgangswert; K = Kosten eines unter den
benannten Annahmen dargestellten Kandidaten; günstigster dargestellter
K-Wert = Vergleich dieser Pfade. Ein nachgewiesenes Minimum unter vollständig
festgelegtem Gesamtvertrag liegt noch nicht vor. Insbesondere sind K-A,
K-G, K-E, K-S und die allgemeine Festschreiberegel nicht bestätigt. Die
Ungleichung aus dem älteren Orgelvergleich wird in Abschnitt 8 ausdrücklich
gegen K-G geprüft, statt sie durch zusätzliche Befehle künstlich herzustellen.

### 3.2 F05.1 – vier Viertel (Foto: 2 Bit)

Notation `0:1, 1:1, 2:1, 3:1`. I: Onsets `{0,1,2,3}`. G: dieselben
Onsets, Tonenden `{1,2,3,4}`; das Ende 4 bleibt Randereignis.

| Fall / Pfad | Zeitpunkt | Verfügbare Evidenz | Erkennung | Vorher | Anweisung | Nachher Δ/Anker/Erwartung enthalten | Kosten / Summe |
| --- | --- | --- | --- | --- | --- | --- | --- |
| I/G | 0 | Erster Einsatz | 0 | U/1/0/– | `10` | N/1/0/1 | 2 / 2 |
| I/G | 1 | Einsatz; G zugleich reguläres Ende des vorherigen Tons | 1 | N/1/0/1 | keine | N/1/0/2 | 0 / 2 |
| I/G | 2 | Einsatz; G zugleich reguläres Ende | 2 | N/1/0/2 | keine | N/1/0/3 | 0 / 2 |
| I/G | 3 | Einsatz; G zugleich reguläres Ende | 3 | N/1/0/3 | keine | N/1/0/4 | 0 / 2 |

K: I=G=2. `11` an einem der inneren Punkte würde ohne gleichzeitiges `10`
den tatsächlichen Einsatz nicht erklären. Das Paar `11 10` kostet je 4 Bit
zusätzlich, obwohl reguläre Fortsetzung bereits alle dortigen Ereignisse
erhält: nach K-G unnötig, nicht informationsgünstiger. `01` ohne Evidenz
würde eine erfüllte Viertelerwartung verändern und ist keine durch Ausbleiben
begründete Alternative. Unter K wird die Untergrenze von einmal `10`
erreicht; das ist kein Nachweis für noch unbestimmte Abschlusskosten.

### 3.3 F05.2 – Halbe, halbe Pause (Foto: 6 Bit)

Notation `0:2`, Pause `[2,4)`. I: Onset `{0}`. G: Onset `{0}` und
hörbares Ende `{2}`. Die Halbenlänge ist unter I keine eigene Evidenz.

| Fall / Pfad | Zeitpunkt | Verfügbare Evidenz | Erkennung | Vorher | Anweisung | Nachher | Kosten / Summe |
| --- | --- | --- | --- | --- | --- | --- | --- |
| I-P / I-D / G-D | 0 | Erster Einsatz | 0 | U/1/0/– | `10` | N/1/0/1 | 2 / 2 |
| I-P | 1 | Erwarteter Einsatz fehlt | r_1 | N/1/0/1 | `11` | P/1/0/P:2 | 2 / 4 |
| I-P | 2 | Kein neuer Einsatz; P setzt sich fort | 2 | P/1/0/P:2 | keine | P/1/0/P:3 | 0 / 4 |
| I-P | 3 | Kein neuer Einsatz; P setzt sich fort | 3 | P/1/0/P:3 | keine | P/1/0/P:4 | 0 / 4 |
| I-D | 1 | Erwarteter Einsatz fehlt | r_1 | N/1/0/1 | `01` | N/2/0/2 | 2 / 4 |
| I-D | 2 | Auch dieser Einsatz fehlt | r_2 | N/2/0/2 | `01` | N/4/0/4 | 2 / 6 |
| G-D | 1 | Erwartetes Offset fehlt; Ton klingt weiter | 1 | N/1/0/1 | `01` | N/2/0/2 | 2 / 4 |
| G-D | 2 | Hörbares Ende, kein neuer Ton | 2 | N/2/0/2 | `11` | P/2/0/P:4 | 2 / 6 |

I: `10 11` kostet 4; `10 01 01` kostet 6. Ebenfalls darstellbar:
`10 01 11` mit P ab r_2, 6 Bit; der dritte Tabellenzweig zeigt genau den
bis 2 gemeinsamen N/2-Zustand. Für I gewinnt unter den dargestellten Pfaden
4 statt der Foto-6. In G ist `11` bei 1 unzulässig: Es würde den tatsächlich
weiterklingenden Ton von 1 bis 2 entfernen. `01` statt `11` bei 2 erhält
unter K-G fälschlich Klang über das hörbare Ende hinaus; ein zusätzliches
`11` könnte das berichtigen, kostet aber 8 statt 6. Keine Teilung aus der
Pausennotation wird benötigt. G-Kandidat: `10 01 11`, 6.

### 3.4 F05.3 – Halbe, zwei Viertel (Foto: 6 Bit)

Notation `0:2, 2:1, 3:1`. I: Onsets `{0,2,3}`. G: dieselben Onsets,
Tonenden `{2,3,4}`; Ende 4 am Rand.

| Fall / Pfad | Zeitpunkt | Verfügbare Evidenz | Erkennung | Vorher | Anweisung | Nachher | Kosten / Summe |
| --- | --- | --- | --- | --- | --- | --- | --- |
| I-D / I-P / G-D | 0 | Erster Einsatz | 0 | U/1/0/– | `10` | N/1/0/1 | 2 / 2 |
| I-D | 1 | Erwarteter Einsatz fehlt | r_1 < 2 | N/1/0/1 | `01` | N/2/0/2 | 2 / 4 |
| G-D | 1 | Erwartetes Ende fehlt, Ton hält | 1 | N/1/0/1 | `01` | N/2/0/2 | 2 / 4 |
| I-D / G-D | 2 | Einsatz, in G zugleich Ende der Halben | 2 | N/2/0/2 | keine | N/2/0/4 | 0 / 4 |
| I-D / G-D | 3 | Früherer Einsatz; G zugleich hörbares Ende des Tons ab 2 | 3 | N/2/0/4 | `00` | N/1/0/4 | 2 / 6 |
| I-P | 1 | Erwarteter Einsatz fehlt | r_1 < 2 | N/1/0/1 | `11` | P/1/0/P:2 | 2 / 4 |
| I-P | 2 | Einsatz auf dem erhaltenen Viertelgitter | 2 | P/1/0/P:2 | `10` | N/1/0/3 | 2 / 6 |
| I-P | 3 | Regulärer Einsatz | 3 | N/1/0/3 | keine | N/1/0/4 | 0 / 6 |

I: `10 01 00` und `10 11 10` kosten je 6 und sind unter K hörbar gleichwertig.
G: P bei 1 würde den gehaltenen Ton vor 2 entfernen und ist daher unzulässig;
`10 01 00` kostet 6. Eine Viertel-Verfeinerung schon bei 2 hätte noch keine
hörbare Begründung aus der künftig notierten Vierteldauer. Ohne `00` bei 3
blieben der zusätzliche Onset und unter G das frühe Tonende unerklärt.
Die räumliche Fotofolge `01 10 00` wird nicht zeitlich vor den ersten Ton
übernommen. Bei später r_1 ist die I-Rechnung neu zu prüfen, kein Betrag
wird allein aufgrund der Partitur vorzeitig festgeschrieben.

### 3.5 F05.4 – zwei Viertel, Halbe (Foto: 4 Bit)

Notation `0:1, 1:1, 2:2`. I: Onsets `{0,1,2}`. G: zusätzlich Enden
`{1,2,4}`; insbesondere **kein** Tonende bei 3.

| Fall / Pfad | Zeitpunkt | Verfügbare Evidenz | Erkennung | Vorher | Anweisung | Nachher | Kosten / Summe |
| --- | --- | --- | --- | --- | --- | --- | --- |
| I/G | 0 | Erster Einsatz | 0 | U/1/0/– | `10` | N/1/0/1 | 2 / 2 |
| I/G | 1 | Regulärer Einsatz; G auch Ende | 1 | N/1/0/1 | keine | N/1/0/2 | 0 / 2 |
| I/G | 2 | Regulärer Einsatz; G auch Ende | 2 | N/1/0/2 | keine | N/1/0/3 | 0 / 2 |
| I-P | 3 | Erwarteter Einsatz fehlt | r_3 < 4 | N/1/0/3 | `11` | P/1/0/P:4 | 2 / 4 |
| I-D | 3 | Erwarteter Einsatz fehlt | r_3 < 4 | N/1/0/3 | `01` | N/2/0/4 | 2 / 4 |
| G-D | 3 | Erwartetes Ende fehlt, Ton klingt weiter | 3 | N/1/0/3 | `01` | N/2/0/4 | 2 / 4 |

I: gleich teure Kandidaten `10 11` und `10 01`, je 4. Sie sind im Fenster
gleichwertig, aber besitzen verschiedene Endzustände für eine spätere
Fortsetzung. G: `10 01`, 4; `11` bei 3 würde hörbaren Klang von 3 bis 4
entfernen und ist unzulässig. I muss denselben Wert wie die Schreibweise
„drei Viertel, Viertelpause“ erhalten; G muss beide unterscheiden.

### 3.6 F05.5 – halbe Pause, Halbe (Foto: 6 Bit)

Notation Pause `[0,2)`, Note `2:2`. I: Onset `{2}`; G: zusätzlich hörbares
Ende `{4}`. Es gibt vor 2 weder einen Ton noch ein kontrolliertes Tonende.

| Fall / Pfad | Zeitpunkt | Verfügbare Evidenz | Erkennung | Vorher | Anweisung | Nachher | Kosten / Summe |
| --- | --- | --- | --- | --- | --- | --- | --- |
| I/G, S+ | 0 | Beobachteter Anfang ohne Einsatz; Annahme expliziter Initialisierung | r_0 < 2, Politik offen | U/1/0/– | `11` | P/1/0/P:1 | 2 / 2 |
| I/G, S+ | 1 | Stille setzt sich fort | 1 | P/1/0/P:1 | keine | P/1/0/P:2 | 0 / 2 |
| I/G, S+ | 2 | Erster Einsatz auf Viertelgitter | 2 | P/1/0/P:2 | `10` | N/1/0/3 | 2 / 4 |
| I-S+P | 3 | Erwarteter Einsatz fehlt | r_3 < 4 | N/1/0/3 | `11` | P/1/0/P:4 | 2 / 6 |
| I-S+D | 3 | Erwarteter Einsatz fehlt | r_3 < 4 | N/1/0/3 | `01` | N/2/0/4 | 2 / 6 |
| G-S+D | 3 | Erwartetes Ende fehlt, Klang hält | 3 | N/1/0/3 | `01` | N/2/0/4 | 2 / 6 |
| I/G, SU | 0,1 | Noch kein aktiver Spielmodus, keine Spielerwartung nach SU | jeweiliger Zeitpunkt | U/1/0/– | keine | U/1/0/– | 0 / 0 |
| I/G, SU | 2 | Erster Einsatz | 2 | U/1/0/– | `10` | N/1/0/3 | 2 / 2 |
| I-SUP / I-SUD | 3 | Erwarteter Einsatz fehlt | r_3 < 4 | N/1/0/3 | `11` / `01` | P/1/0/P:4 bzw. N/2/0/4 | 2 / 4 |
| G-SUD | 3 | Erwartetes Ende fehlt | 3 | N/1/0/3 | `01` | N/2/0/4 | 2 / 4 |

S+: I `11 10 11` oder `11 10 01`, je 6; G `11 10 01`, 6.
SU: I `10 11` oder `10 01`, je 4; G `10 01`, 4. SU ist **nicht bestätigt**.
G-`11` bei 3 wäre wegen des weiterklingenden Tons unzulässig. Ein `01` nur
zur Beschreibung der Anfangshalbpause ist nicht begründet: Die Stille bei 1
ist bereits eine erwartbare P-Fortsetzung, kein neuer Anlass. Mit Δ=1
kann der erste Ton bei 2 ohne Teilungswechsel eingeordnet werden. Die
Foto-Summe 6 ist unter S+ erreichbar, aber mit anderer Erkenntnisfolge
und anderer Begründung des Teilungswechsels. Kleinste Entscheidung:
Muss die beobachtete Anfangsstille initial mit `11` bezahlt werden?

### 3.7 F05.6 – zwei Viertel, halbe Pause (Foto: 6 Bit)

Notation `0:1, 1:1`, Pause `[2,4)`. I: Onsets `{0,1}`. G: zusätzlich
hörbare Enden `{1,2}`. `10 11` unter I ist seit `835655e` ausdrücklich
als Kandidat festgelegt; dies wird hier nicht erneut zur Grundsatzfrage.

| Fall / Pfad | Zeitpunkt | Verfügbare Evidenz | Erkennung | Vorher | Anweisung | Nachher | Kosten / Summe |
| --- | --- | --- | --- | --- | --- | --- | --- |
| I/G | 0 | Erster Einsatz | 0 | U/1/0/– | `10` | N/1/0/1 | 2 / 2 |
| I/G | 1 | Regulärer Einsatz; G zugleich Ende | 1 | N/1/0/1 | keine | N/1/0/2 | 0 / 2 |
| I-P | 2 | Erwarteter Einsatz fehlt | r_2 < 3 für die gezeigte Reihenfolge | N/1/0/2 | `11` | P/1/0/P:3 | 2 / 4 |
| I-P | 3 | Kein Einsatz, erwartbare P-Fortsetzung | 3 bzw. nach r_2 | P/1/0/P:3 | keine | P/1/0/P:4 | 0 / 4 |
| I-D | 2 | Erwarteter Einsatz fehlt | r_2 < 4 | N/1/0/2 | `01` | N/2/0/4 | 2 / 4 |
| G-P | 2 | Hörbares Ende ohne neuen Ton | 2 | N/1/0/2 | `11` | P/1/0/P:3 | 2 / 4 |
| G-P | 3 | Stille setzt sich fort | 3 | P/1/0/P:3 | keine | P/1/0/P:4 | 0 / 4 |

I: `10 11` und unter K-A auch `10 01` kosten 4. G: `10 11`, 4;
`01` allein bei 2 lässt unter K-G den Ton weiterklingen und verletzt das
hörbare Ende. `10 01 11` kostet 6; wenn beide Anweisungen am Ende bei 2
zugelassen werden, ist die Folge im Fenster darstellbar, unter K aber
teurer als die bereits vollständige Erklärung `10 11`. Die halbe Pause
liefert keine eigenständige Evidenz für das zusätzliche `01`.

**Ankervariante A-last, ausdrücklich unbestätigt:** Nach dem Einsatz bei 1
wird für den Änderungsversuch A=1 statt A=0 genommen. Nach `01` bei r_2 ist
der Zustand N/2/1/3, Kostenstand 4. Bei 3 fehlt erneut ein erwarteter Ton:
`11` ergibt P/2/1/P:5 (6 gesamt), oder `01` ergibt N/4/1/5 (6 gesamt).
Damit kostet der D-Pfad `10 01 11` bzw. `10 01 01` hier 6 statt 4.
Der P-Pfad `10 11` bleibt 4. Die Ankerregel beeinflusst also Alternativen,
auch wenn sie diesen günstigsten dargestellten Wert nicht ändert.
A-last darf nicht ohne gesonderte Bestätigung auf den Punktierungsfall
übertragen werden; dort ist A=0 bereits verbindlich.

### 3.8 F05.7 – halbe Pause, zwei Viertel (Foto: 8 Bit)

Notation Pause `[0,2)`, Noten `2:1, 3:1`. I: Onsets `{2,3}`.
G: zusätzlich hörbare Enden `{3,4}`; Ende 4 am Rand.

| Fall / Pfad | Zeitpunkt | Verfügbare Evidenz | Erkennung | Vorher | Anweisung | Nachher | Kosten / Summe |
| --- | --- | --- | --- | --- | --- | --- | --- |
| I/G, S+ | 0 | Anfang ohne Einsatz, explizite Initialisierung als Annahme | r_0 < 2, Politik offen | U/1/0/– | `11` | P/1/0/P:1 | 2 / 2 |
| I/G, S+ | 1 | Stille setzt sich fort | 1 | P/1/0/P:1 | keine | P/1/0/P:2 | 0 / 2 |
| I/G, S+ | 2 | Erster Einsatz auf erhaltenem Viertelgitter | 2 | P/1/0/P:2 | `10` | N/1/0/3 | 2 / 4 |
| I/G, S+ | 3 | Regulärer Einsatz; G auch Ende | 3 | N/1/0/3 | keine | N/1/0/4 | 0 / 4 |
| I/G, SU | 0,1 | Keine Spielerwartung vor erstem Ton laut SU | jeweiliger Zeitpunkt | U/1/0/– | keine | U/1/0/– | 0 / 0 |
| I/G, SU | 2 | Erster Einsatz | 2 | U/1/0/– | `10` | N/1/0/3 | 2 / 2 |
| I/G, SU | 3 | Regulärer Einsatz; G auch Ende | 3 | N/1/0/3 | keine | N/1/0/4 | 0 / 2 |

S+: I=G `11 10`, 4; SU: I=G `10`, 2. Die Fotofolge
`01 11 00 10` enthält zwei Teilungswechsel, deren bloße Begründung durch
die notierte Anfangshalbpause unzulässig ist. Eine tatsächlich beobachtete
zusätzliche Evidenz für diese Wechsel liegt hier nicht vor. Würde man
den Zustand zunächst aus anderem verbindlichem Kontext mit Δ=2 vorgeben,
müsste die Rückkehr bei 3 neu geprüft werden; ein solcher Kontext gehört
aber nicht zu diesem Auftrag. Weglassen von `10` bei 2 verletzt die feste
Zahlung des ersten Einsatzes; kostenlose Reaktivierung ist keine Alternative.

### 3.9 Kompakte Ergebnisse und Geltungsbereich

| Fall | Foto | Günstigste dargestellte I-Pfade unter K | Günstigster dargestellter G-Pfad unter K |
| --- | ---: | --- | --- |
| F05.1 | 2 | `10` = 2 | `10` = 2 |
| F05.2 | 6 | `10 11` = 4 | `10 01 11` = 6 |
| F05.3 | 6 | `10 01 00` / `10 11 10` = 6 | `10 01 00` = 6 |
| F05.4 | 4 | `10 11` / `10 01` = 4 | `10 01` = 4 |
| F05.5 | 6 | S+: `11 10 11` / `11 10 01` = 6; SU: `10 11` / `10 01` = 4 | S+: `11 10 01` = 6; SU: `10 01` = 4 |
| F05.6 | 6 | `10 11` / `10 01` = 4 (zweiter Pfad ankerabhängig) | `10 11` = 4 |
| F05.7 | 8 | S+: `11 10` = 4; SU: `10` = 2 | S+: `11 10` = 4; SU: `10` = 2 |

Alle Zahlen sind Kandidatenkosten bzw. günstigste Werte **im dargestellten
Pfadvergleich unter K**. Die Spalte „nachgewiesenes Minimum unter vollständig
festgelegten Regeln“ wäre bei allen sieben Figuren derzeit **offen**.
Nicht nur eine Menge von Bitkosten, sondern die zulässigen Erwartungen,
Erkennungsentscheidungen und Endbedingungen müssen dafür feststehen.

Fotoabweichungen: F05.2.I 4 statt 6, weil der Impuls keine gehaltene Halbe
vorschreibt; F05.6.I/G 4 statt 6 ohne notationsbedingtes `01`;
F05.7.I/G unter S+ 4 statt 8 ohne beide Pausenteilungswechsel. Bei SU
entfallen in F05.5 und F05.7 zusätzlich die initialen 2 Bit; das ist eine
**unbestätigte Variantenrechnung**, keine beschlossene Verbilligung.
Gleiche Summen wie auf dem Foto belegen keine gleiche Erkennungsreihenfolge.


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

## 7. Klangbezogene Gegenproben außerhalb der sieben Hauptrechnungen

Die Hauptfälle stehen jetzt vollständig in Abschnitt 3. Für Foto 1 bleiben
zusätzlich die folgenden Klangunterschiede zu erhalten:

| Fall | I: Onsets | G: dieselben Onsets plus Enden | Konsequenz |
| --- | --- | --- | --- |
| F03, Foto 1 / 1 | 0,1,3/2,2,5/2,11/4,3,13/4,7/2 | 1,3/2,2,5/2,11/4,3,13/4,7/2,4 | I-Kandidatenrechnung in Abschnitt 5; G-Enden zusätzlich erhalten. |
| F04, Foto 1 / 2 | 0,3/2,2,5/2,11/4,3,13/4,7/2 | 1,2,5/2,11/4,3,13/4,7/2,4 | G hat eine hörbare Lücke von 1 bis 3/2; I hat keine kontrollierte Abschaltung bei 1. |

### 7.1 Gleiche Stille, andere Pausenschreibweise

F05.6.I und F05.6.G werden je mit halber Pause bzw. zwei Viertelpausen in
`[2,4)` verglichen. Die Evidenz bei 0,1,2 ist gleich; keine neue Evidenz
entsteht durch die grafische Grenze bei 3. P setzt sich unverändert fort:
`10 11`, Kandidatenkosten 4 in beiden Schreibweisen. Gleiches gilt für
F05.7.I/G mit halber Pause bzw. zwei Viertelpausen in `[0,2)`: unter S+
`11 10`, 4; unter SU `10`, 2. Ein `01` und dessen spätere Rücknahme `00`
nur zur Darstellung der halben Pause sind hier ausgeschlossen.

### 7.2 Halbe gegen Viertel plus Viertelpause

Gemeinsames Fenster `[0,2)`; Variante H: `0:2`; Variante QP: `0:1`, dann
Pause `[1,2)`. Gleicher bekannter Viertelbezug, erster Einsatz bei 0.

- **I:** H und QP erzeugen denselben kurzen Impuls bei 0. Bei 1 fehlt in
  beiden Fällen der erwartete nächste Einsatz. Kandidaten `10 11` und
  `10 01` kosten je 4 vor möglichem Abschluss. Die Notation allein darf
  keinen anderen Wert erzeugen.
- **G-H:** Ton hält bis 2. Bei 1 fehlt das erwartete Offset, `01` ergibt
  `10 01` = 4. `11` bei 1 wäre wegen des klingenden Tons unzulässig.
- **G-QP:** Ton endet hörbar bei 1. `11` erklärt dies und die folgende Pause:
  `10 11` = 4. `01` allein würde das Ende nicht realisieren und ist unzulässig.

**Konflikt K-G gegen eine frühere Festlegung:** Der Vertrag enthält die
qualitative Forderung `I(G-QP) > I(G-H)`. K-G liefert dagegen vor Abschluss
4 und 4, trotz verschiedener Tonenden und unterschiedlicher Zustände.
Dies ist nicht bloß eine fehlende Minimalitätsprüfung: Zwei direkt
begründete gleich teure Pfade zeigen, dass diese Übergangsannahmen allein
keine strikte Ungleichung herleiten. Hörbar verschieden bedeutet notwendig
getrennte Ereignisrepräsentation, aber mathematisch nicht automatisch
verschiedene skalare Kosten.

**Unbestätigter Vorschlag:** Die beiden Ereignisverläufe und Erklärungen
müssen verschieden bleiben; ob auch ihre Summen strikt verschieden sein
müssen, ist ausdrücklich zu entscheiden. Die ältere Ungleichung wird hier
nicht aufgehoben. Falls sie beibehalten wird, muss eine fachliche
Erwartungs-/Übergangsregel den Unterschied tragen. Eine nur zur gewünschten
Rangfolge erfundene Gebühr oder ein unbegründetes zusätzliches `01` ist
keine Lösung. Bis zur Entscheidung sind die G-Kosten Ergebnisse des
benannten K-Vorschlags, keine vollständig abgenommenen Modellwerte.

### 7.3 Anker und kausale Vergangenheit

K-A behält bei der späteren Verfeinerung das Gitter bei. In F05.3 wird
bei 3 von Δ=2 auf Δ=1 verfeinert. Das neue Viertelgitter wird nicht
rückwirkend bei 1 geprüft; weder `11` noch ein neuer Auslassungsbetrag
wird dort nachgefordert. Die tatsächlich gewählte Information bei 1 bleibt
im jeweiligen Pfad erhalten. Es gibt keinen Wechsel zwischen bereits
bezahlten Pfaden, der frühere Kosten löscht.

F05.6 zeigt, dass A=0 und ein zuletzt artikulierter Anker A=1 die nächste
Erwartung nach `01` verschieden setzen (4 gegenüber 3). Vorschlag: Für
stabilen bekannten Bezug das erste Gitter beibehalten, statt seine Phase
unbemerkt zu optimieren. Das ist außerhalb des bestätigten Punktierungsfalls
noch keine Festlegung. Keine neue Ankerpolitik wird in den Bestandsalgorithmus
übertragen.

## 8. Gegenprüfung am bestätigten Punktierungsfall und am Analyseende

### 8.1 Punktierung: zulässige Konkurrenz und unzulässige Billigregeln

Klang G, Onsets 0 und 3/2, Tonende bei 3/2, Randende bei 2. Bestätigt ist
A=0, `10` bei 0, fehlendes erwartetes Offset bei 1 → `01`, danach Erwartung
2; bei 3/2 `00 00` bis Δ=1/2. Summe bis zum zweiten Einsatz: 8 Bit.

- K-A erhält A=0; kein Konflikt mit dem bestätigten Anker.
- K-G verbietet `11` bei 1, weil der Ton bis 3/2 weiterklingt. Eine neue
  Regel „bei Ausbleiben immer `11`“ würde hier die hörbare Fortdauer
  verletzen und ist daher abzulehnen. Dass `11` kein Tonende voraussetzt,
  erlaubt nicht die Entfernung eines tatsächlich gehaltenen Klangs.
- Für **I mit denselben Onsets** ist dagegen unter K-P eine Konkurrenz
  möglich: `10` bei 0, `11` bei r_1, bei 3/2 auf dem Viertelgitter A=0
  zunächst `00` (Δ=1/2), dann `10` zur Rückkehr zu N. Das kostet ebenfalls
  8 Bit. Ohne `00` wäre 3/2 kein Punkt des erhaltenen Viertelgitters.
  Die Gleichheit der Summen legt keinen gemeinsamen Erkenntnispfad fest.
  Der ausdrücklich bestätigte `01 00 00`-Pfad bleibt als Referenz erhalten;
  die alternative I-Auswahl wird nicht als neuer bestätigter Pfad ausgegeben.
- Bei `01` nach 1 ist das sofortige Zurückspringen von Δ=2 auf Δ=1/2 mit
  nur einem `00` unzulässig: Jede Operation halbiert genau einmal.
- Ein globaler Rückblick, der von Anfang an Δ=1/2 setzt und die Änderung
  bei 1 löscht, widerspricht dem festgelegten Viertelbeginn und der bereits
  entstandenen Information. V07 darf deshalb nicht nur das billigste
  rückblickend passende Gitter auswählen.

Damit besteht der K-Vorschlag die konkrete Anker-/Schrittprüfung. Eine
allgemeine kausale Auswahlregel ist dadurch noch nicht bewiesen.

### 8.2 Fenstergrenze als tatsächliche Zahlenvariante

K-E hält alle Randenden als Daten fest und gibt die Kosten vor einer
zusätzlichen Abschlussanweisung an. Die Alternative **E-P** wäre ein
**anderer, unbestätigter Auftrag**: Bei 4 muss auch der aktive N-Zustand
in P überführt und der betreffende `11`-Befehl mitgezählt werden; bereits
P bleibt ohne neuen Befehl P. Dies ist eine konkrete Operation, keine
pauschale Abschlussgebühr. E-P wird nicht stillschweigend vorausgesetzt.

| Fall | K-Wert I/G unter S+ | Falls E-P zusätzlich verlangt wird: I/G |
| --- | --- | --- |
| F05.1 | 2 / 2 | 4 / 4 |
| F05.2 | 4 / 6 | 4 / 6 (günstigster dargestellter Pfad endet bereits in P) |
| F05.3 | 6 / 6 | 8 / 8 |
| F05.4 | 4 / 4 | 4 / 6 (I-P gewinnt gegen den N-Endpfad) |
| F05.5 | 6 / 6 | 6 / 8 (I-P endet bereits in P) |
| F05.6 | 4 / 4 | 4 / 4 (P-Endpfade) |
| F05.7 | 4 / 4 | 6 / 6 |

Bei SU liegen F05.5 und F05.7 weiterhin je 2 Bit unter S+. E-P würde auch
das bestätigte Viertelbeispiel von 2 auf 4 für den erweiterten Gesamtauftrag
ändern. Vorschlag: Vorerst K-E, Randereignisse gesondert berichten und keinen
zusätzlichen Auftrag zum Pausenspielen am Taktende unterstellen. Die Auswahl
ändert den Endzustand nie kostenlos: K-E lässt ihn als Analysezustand stehen,
E-P weist seine Änderung und Kosten aus. Ein realer hörbarer Abschluss darf
in beiden Varianten nicht aus der musikalischen Ereignisliste verschwinden.

## 9. Drei priorisierte Entscheidungen

1. **Initialisierung der Anfangspause (F05.7):** S+ (`11 10`, 4 Bit) oder
   SU (U bis 2, dann `10`, 2 Bit)? Vorschlag S+: Anfangsstille als
   ausdrücklich gesetzten Spielzustand bezahlen, ohne ihre notierte
   Gliederung zu codieren. Auch F05.5 unterscheidet sich dadurch um 2 Bit.
2. **Gehaltener Ton und strikte Rangfolge (G-H/G-QP in Abschnitt 7.2):**
   Dürfen verschiedene hörbare Verläufe unterschiedliche Erklärungen,
   aber dieselbe Summe 4 haben? Vorschlag: ja, bei vollständig erhaltener
   Ereignisdarstellung. Falls die bisherige strikte Ungleichung verbindlich
   bleiben soll, fehlt eine begründete Übergangsregel; keine Zusatzkosten
   allein zum Erzwingen der Ungleichung einführen.
3. **Bezahlter Abschluss (F05.1):** Endet der Kostenauftrag vor einer
   zusätzlichen P-Anweisung (2 Bit unter K-E), oder soll `11` bei 4 zum
   Gesamtauftrag gehören (4 unter E-P)? Vorschlag K-E, mit erhaltenem
   Randende und separat ausgewiesenem Endzustand. Dies entscheidet auch,
   welche derzeit gleich teuren Pfade am Fensterende gleich günstig bleiben.

Die Vorschläge sind unbestätigt. Weitere technische Planung folgt hieraus
noch nicht. Die allgemeine Anker-/Erkennungs- und Festschreibepolitik bleibt
im Vertrag als eigene Modellarbeit sichtbar; sie wird nicht durch diese
sieben endlichen Rechnungen als erledigt erklärt.
