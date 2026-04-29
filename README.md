# Rampenrechner

Webbasiertes Tool zur Berechnung der **passenden Rampe für Rollstuhlfahrer und Mobilitätshilfen** — auf Basis der DIN 18040 und mit direktem Abgleich gegen das Rehasense-Produktsortiment.

🔗 **Live:** https://lukashoppenberg-rh.github.io/Rampenrechner/

---

## Funktionen

### Berechnung in drei Modi
- **Länge berechnen** — aus Höhe + zulässiger Steigung
- **Steigung berechnen** — aus Höhe + vorhandener Rampenlänge
- **Höhe berechnen** — aus Rampenlänge + Steigung

### Nutzergruppen nach Rehasense-Infoblatt (DIN 18040)
Sechs Personengruppen mit den jeweils empfohlenen Maximalsteigungen:

| Nutzergruppe                  | Max. Steigung |
|-------------------------------|---------------|
| Selbstfahrer                  | 3 %           |
| Selbstfahrer (Standard)       | 6 %           |
| Selbstfahrer mit Helfer       | 9 %           |
| Selbstfahrer mit E-Antrieb    | 12 %          |
| Elektrorollstuhl              | 15 %          |
| Elektro-Außenrollstuhl        | 18 %          |

Der öffentliche Bereich ist nach **DIN 18040-1** mit max. 6 % auszuführen — entspricht der Default-Auswahl „Selbstfahrer 6 %".

### Drei Rampentypen
- **PONDUS-Serie** — Teleskoprampen (S, F2, T2, T3, FT3)
- **DOORSTEP-Serie** — Türschwellenrampen (MICRO, MINI, VERSTELLBAR)
- **BROADBAND-Serie** — Flächenrampen (SPECTRUM, DEFRAG)

### Interaktives Ergebnis
- Visualisierung der Rampe als maßstabsgetreues SVG (skaliert mit Höhe und Länge)
- Live-Schieberegler zum Anpassen einzelner Werte ohne neu zu rechnen
- Status-Indikator (Grün/Gelb/Rot) je nach Übereinstimmung mit der Nutzergruppe
- Automatischer Abgleich mit dem Produktkatalog inkl. Hervorhebung passender Modelle, Artikelnummern und UVP

---

## Tech Stack

- **Vanilla HTML / CSS / JavaScript** — keine Frameworks, kein Build-Step
- **Schrift:** Montserrat (Google Fonts)
- **Hosting:** GitHub Pages

Alles ist in einer einzigen [`index.html`](./index.html) gebündelt — Styles, Logik und Produktkatalog inline. Damit lädt die Seite ohne zusätzliche Requests und ist trivial zu hosten.

---

## Lokal ausführen

Da rein statisch, reicht ein Doppelklick:

```bash
# einfach öffnen
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Oder mit beliebigem Static-Server:

```bash
npx serve .
```

---

## Projektstruktur

```
Rampenrechner/
├── index.html              # gesamte Anwendung (HTML, CSS, JS, Daten)
├── design-guidelines.md    # Design-System-Referenz
├── logo.png                # Rehasense-Logo (im Header)
└── README.md
```

---

## Design System

Der Rampenrechner ist die **visuelle Baseline für alle künftigen Rehasense-Projekte**. Die destillierten Design-Regeln (Farben, Typografie, Komponenten, Abstände, Interaktionen) sind dokumentiert in:

📐 [`design-guidelines.md`](./design-guidelines.md)

Diese Datei dient als Primärquelle für Look & Feel neuer Rehasense-Tools, damit eine konsistente Design-Sprache über alle Produkte hinweg entsteht.

---

## Standards & Hinweise

Berechnungen orientieren sich an der **DIN 18040** (barrierefreies Bauen). Die angegebenen maximalen Steigungen sind Empfehlungen — bei Steigungen über 6 % sind Sicherheitsgurt und Kippsicherung am Rollstuhl empfehlenswert.

Alle Angaben **ohne Gewähr**. Im Zweifel die jeweils gültigen DIN-Normen prüfen.

---

## Formeln

```
Länge   = Höhe × 100 / Steigung
Steigung = Höhe × 100 / Länge
Höhe    = Steigung × Länge / 100
```

---

© Rehasense
