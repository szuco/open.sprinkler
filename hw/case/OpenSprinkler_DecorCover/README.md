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

## Maßvorgaben

Die Größe wird über drei **Mindestmaße** gesteuert (Block *MINDESTMASSE* oben
im Makro). Sie beschreiben den Raum, den die Haube überdecken muss – nicht die
Haube selbst. Die Zugaben darunter werden aufgeschlagen, die geforderten Werte
sind also garantiert eingehalten.

| Parameter | Bedeutung | Vorgabe | Zugabe | Ergebnis |
|---|---|---|---|---|
| `CLEAR_W` | lichte Breite = Breite der montierten Einheit | **≥ 170 mm** | 5 mm je Seite | 180 mm |
| `CLEAR_DROP` | Abdeckung ab Oberkante Gerät nach unten | **≥ 160 mm** | 5 mm | 165 mm |
| `CLEAR_D` | lichte Tiefe: Wand → Frontfläche des Gerätes | **≥ 25 mm** | 7 mm | 32 mm |

Daraus ergibt sich die Haube mit **186 × 177 × 37 mm** außen.

**Faustregel:** im Zweifel großzügig aufrunden.

- `CLEAR_W` / `CLEAR_DROP` zu groß → Haube wird unauffällig größer, passt aber
  sicher.
- `CLEAR_D` zu groß → Haube steht ein paar Millimeter weiter von der Wand ab.
  `CLEAR_D` zu **klein** ist der einzige echte Fehler: dann liegt der hintere
  Rand nicht an der Wand an und die Haube wackelt.
- `CASE_H` (100 mm) ist rein informativ und wird nur für die Ausgabe „so viel
  liegt unterhalb der Geräteunterkante“ verwendet.

## Konstruktion

- **Außenmaß mit den Voreinstellungen:** 186 × 177 × 37 mm (B × H × T),
  Wandstärke 3 mm, Kantenradius 8 mm, Frontfase 1,5 mm.
  Lichter Innenraum 180 mm breit, 165 mm ab Geräteoberkante nach unten,
  32 mm tief.
- Die Haube **hängt über zwei lange Innenrippen auf der Gehäuseoberseite** –
  kein Werkzeug, keine zusätzlichen Löcher in der Wand. Die Rippen laufen fast
  über die gesamte Tiefe (7,5–33 mm), damit sie das Gehäuse auch dann sicher
  treffen, wenn `CLEAR_D` großzügig geschätzt wurde. Sie sitzen bei ±52 mm in
  den Stegen zwischen zwei Lüftungsschlitzen. Der hintere Rand liegt an der
  Wand an und verhindert das Kippen.
- **5 mm seitliches Spiel** pro Seite: Damit passt die Haube auch über einen
  seitlich überstehenden Klemmverbinder (z. B. Wago) und über abgehende Kabel.
  Die hinteren Zentrierrippen sitzen bewusst nur im **oberen** Bereich, damit
  sie unten abgehende Leitungen nicht berühren.
- Die Haube reicht **165 mm ab Geräteoberkante nach unten** – bei einem
  100 mm hohen Gehäuse also 65 mm unter dessen Unterkante. Das verdeckt
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

Benötigtes Druckbett: mind. **190 × 181 mm** (mit den Voreinstellungen).
Ein 180 × 180 mm großes Bett (z. B. Bambu A1 mini) reicht dafür **nicht**.
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

- `CLEAR_W`, `CLEAR_DROP`, `CLEAR_D` und die Zugaben `ADD_W`, `ADD_DROP`,
  `ADD_D` (siehe oben)
- `TEXT`, `TEXT_SIZE`, `TEXT_RELIEF`, `TEXT_STYLE` (`"raised"`/`"engraved"`),
  `TEXT_Y_OFF` (Schriftzug aus der Mitte verschieben),
  `FONT` (eigener .ttf-Pfad; Standard: Arial Rounded Bold)
- `RIB_H`, `RIB_X`, `RIB_W`, `CRIB_LEN` (Sitz und Führung)
- `VENT_SLOTS`, `VENT_L`, `VENT_PITCH_GAP`, `CABLE_SLOT_W`
- `WALL`, `R_OUT`, `CHAMFER_F` (Optik)

Nach Änderungen das Makro einfach erneut ausführen (in FreeCAD oder per
`freecadcmd OpenSprinklerCover.FCMacro`) – FCStd und STLs werden neu erzeugt.
Am Ende gibt das Makro die resultierenden Maße aus und stellt den geforderten
Mindestmaßen die tatsächlichen Werte gegenüber.
