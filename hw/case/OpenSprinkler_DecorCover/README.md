# OpenSprinkler Design-Abdeckhaube

Eine dekorative, zweiteilige Haube, die von vorn über den **fertig an der Wand
montierten** OpenSprinkler gestülpt wird. Sie verdeckt Gehäuse, Klemmleisten,
Wand-Montagelaschen, Kabelbaum **und den Wanddurchbruch darunter** vollständig
und trägt mittig den erhabenen Schriftzug **„OpenSprinkler“**.

![Frontansicht](preview_front.png)
![Rückansicht](preview_back.png)

## Dateien

| Datei | Inhalt |
|---|---|
| `OpenSprinklerCover.FCMacro` | Parametrisches FreeCAD-Makro (erzeugt alles neu) |
| `OpenSprinklerCover.FCStd` | Fertiges FreeCAD-Dokument (Zusammenbau-Ansicht) |
| `CoverFrame.stl` | Rahmen/Haube – druckfertig orientiert |
| `FrontPlate.stl` | Frontplatte mit Relief – druckfertig orientiert |

## Vor dem Druck: vier Maße nachmessen

Die Haube wird über das **montierte Gerät samt Gehäuse und Rückplatte**
gestülpt – nicht über die nackte Platine. Deshalb bitte an der Wand messen und
die Werte oben im Makro (Block *MONTIERTE EINHEIT*) eintragen:

| Parameter | Bedeutung | Voreinstellung |
|---|---|---|
| `CASE_W` | größte Breite, über die Wand-Montagelaschen gemessen | 172 mm |
| `CASE_H` | Höhe des Gehäusekörpers, **ohne** die Klemmleisten | 100 mm |
| `CASE_D` | Wandoberfläche → Frontfläche des Gehäuses | 42 mm |
| `COVER_BELOW` | was unter der Gehäuseunterkante verdeckt werden soll: Klemmen + Kabelbogen + Wandöffnung | 40 mm |

**Faustregel:** im Zweifel großzügig aufrunden.

- `CASE_W` zu groß → Haube wird unauffällig breiter, passt aber sicher.
- `CASE_D` zu groß → Haube steht ein paar Millimeter weiter von der Wand ab.
  `CASE_D` zu **klein** ist der einzige echte Fehler: dann liegt der hintere
  Rand nicht an der Wand an und die Haube wackelt.
- `CASE_H` / `COVER_BELOW` sind unkritisch – sie bestimmen nur, wie weit die
  Schürze nach unten reicht.

## Konstruktion

- **Außenmaß mit den Voreinstellungen:** 188 × 162 × 48,5 mm (B × H × T),
  Wandstärke 3 mm, Kantenradius 8 mm, Frontfase 1,5 mm.
  Innenraum 182 × 152 mm, nutzbare Tiefe 42,5 mm.
- Die Haube **hängt über zwei lange Innenrippen auf der Gehäuseoberseite** –
  kein Werkzeug, keine zusätzlichen Löcher in der Wand. Die Rippen laufen fast
  über die gesamte Tiefe, damit sie das Gehäuse auch dann sicher treffen, wenn
  `CASE_D` großzügig geschätzt wurde. Der hintere Rand liegt an der Wand an und
  verhindert das Kippen.
- **5 mm seitliches Spiel** pro Seite: Damit passt die Haube auch über einen
  seitlich überstehenden Klemmverbinder (z. B. Wago) und über abgehende Kabel.
  Die hinteren Zentrierrippen sitzen bewusst nur im **oberen** Bereich, damit
  sie unten abgehende Leitungen nicht berühren.
- Die Schürze reicht mit den Voreinstellungen **50 mm unter die
  Gehäuseunterkante** (`COVER_BELOW` + 10 mm Reserve) und verdeckt damit
  Klemmleisten, Kabelbogen und die Wandöffnung.
- **Lüftungsschlitze** sitzen von vorn unsichtbar: unten vorn (Einlass) und
  oben nahe der Wand (Auslass) – natürliche Konvektion.
- Ein **150 mm breiter Kabelschlitz** unten hinten lässt bei Bedarf eine
  Leitung nach unten aus der Haube heraus (und lüftet zusätzlich).
- Die Frontplatte liegt in einem Falz **1,5 mm hinter der Rahmenkante**
  (Schattenfuge); das Relief steht 1,4 mm hervor und schließt knapp innerhalb
  der Frontebene ab.

## Druck

| | CoverFrame | FrontPlate |
|---|---|---|
| Ausrichtung | wie exportiert: Front nach unten, Öffnung nach oben | flach, Schrift nach oben |
| Stützen | **keine** (Falz ist 45° angefast) | keine |
| Schichthöhe | 0,2 mm | 0,15–0,2 mm |
| Perimeter / Infill | 3 Wände, 15 % | 3 Wände, 15–20 % |
| Material | PETG oder ASA (draußen), PLA (innen) | dito, gern Kontrastfarbe |

Benötigtes Druckbett: mind. **192 × 166 mm** (mit den Voreinstellungen).
Die große, flache Frontplatte gern mit Brim drucken – sie neigt sonst zum
Verziehen.

**Tipp:** Rahmen und Platte in zwei Farben drucken (z. B. Rahmen anthrazit,
Platte cremeweiß) – oder beim Plattendruck an der Reliefhöhe (z. B. bei 3,0 mm)
einen Filamentwechsel einlegen, dann erscheint der Schriftzug in einer
dritten Farbe.

## Montage

1. Frontplatte von hinten in den Falz des Rahmens legen (Relief zeigt nach
   vorn, durch die Öffnung).
2. An den vier Auflagestegen mit wenigen Tropfen Sekundenkleber oder
   PETG-tauglichem Kleber fixieren.
3. Haube von vorn über den montierten OpenSprinkler stülpen und nach unten
   absetzen, bis die beiden Innenrippen auf der Gehäuseoberseite aufliegen und
   der hintere Rand an der Wand anliegt. Sie hängt dann von selbst.
4. Optional mit zwei Streifen Klettband oder doppelseitigem Klebeband zwischen
   Haubenrand und Wand gegen Abheben sichern.

Zum Warten einfach nach vorn abziehen.

## Anpassen

Alle Maße stehen als Parameter am Anfang des Makros, u. a.:

- `CASE_W`, `CASE_H`, `CASE_D`, `COVER_BELOW` (siehe oben)
- `TEXT`, `TEXT_SIZE`, `TEXT_RELIEF`, `TEXT_STYLE` (`"raised"`/`"engraved"`),
  `TEXT_Y_OFF` (Schriftzug aus der Mitte verschieben),
  `FONT` (eigener .ttf-Pfad; Standard: Arial Rounded Bold)
- `CLEAR_SIDE`, `RIB_H`, `SKIRT_EXTRA` (Passung und Sitz)
- `VENT_SLOTS`, `CABLE_SLOT_W`
- `WALL`, `R_OUT`, `CHAMFER_F` (Optik)

Nach Änderungen das Makro einfach erneut ausführen (in FreeCAD oder per
`freecadcmd OpenSprinklerCover.FCMacro`) – FCStd und STLs werden neu erzeugt.
Am Ende gibt das Makro die resultierenden Außen-, Innen- und Bettmaße aus.
