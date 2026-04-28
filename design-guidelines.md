# Rehasense Design Guidelines

Abgeleitet aus dem Rampenrechner-Projekt. Gilt als Basis für alle zukünftigen Rehasense-Tools.

---

## Farben

```css
--primary:        #1B3570   /* Hauptfarbe – Header, Überschriften, CTAs */
--primary-hover:  #253F88   /* Hover-State für primäre Elemente */
--secondary:      #5BB4D8   /* Akzent – aktive States, Borders, Slider */
--secondary-light:#C8E7F5   /* Sehr heller Akzent – Subtext im Header */
--bg:             #EEF3F8   /* Seitenhintergrund, interne Flächen in Cards */
--card:           #FFFFFF   /* Card-Hintergrund */
--text:           #1A2B3C   /* Fließtext */
--muted:          #6B7C93   /* Sekundärtext, Labels, Platzhalter */
--border:         #D0DCE8   /* Alle Rahmen und Trennlinien */

/* Statusfarben */
--ok:             #1D8348   /* Grün – alles in Ordnung */
--ok-bg:          #D4EDDA
--warn:           #7D6608   /* Gelb – Warnung */
--warn-bg:        #FFF3CD
--danger:         #922B21   /* Rot – kritisch */
--danger-bg:      #FADBD8
```

**Aktiv-State-Hintergrund:** `#EBF8FF` (helles Blau) – für ausgewählte Buttons und Info-Items.

---

## Typografie

**Schriftart:** Montserrat (Google Fonts) – einzige Schrift im gesamten Projekt.

| Verwendung              | Größe       | Gewicht |
|-------------------------|-------------|---------|
| Seitenüberschrift (H1)  | 1.35rem     | 700     |
| Card-Titel              | 1.15rem     | 700     |
| Ergebniswert (groß)     | 3.2rem      | 800     |
| Slider-Label            | 0.95rem     | 700     |
| Fließtext / Inputs      | 1rem        | 600     |
| Detail-Kachel-Wert      | 1.1rem      | 700     |
| Beschreibungstext       | 0.82rem     | 400–600 |
| Uppercase-Labels        | 0.72–0.8rem | 700     |
| Kleinste Hilfstexte     | 0.68–0.76rem| 500–600 |

**Uppercase-Labels** (z. B. Sektionsbezeichner, Tabellen-Header): immer `text-transform: uppercase` + `letter-spacing: 0.4–0.6px`.

**Monospace** wird ausschließlich für Artikelnummern verwendet (`'Courier New', monospace`).

---

## Layout

- **Max-Breite Content:** `860px`, zentriert mit `margin: 0 auto`
- **Padding Seite:** `32px 16px 48px` (oben/unten großzügig, Seiten minimal)
- **Vertikaler Abstand zwischen Sektionen:** `24px` (flexbox `gap`)

---

## Cards

Alle Hauptbereiche sind in Cards gekapselt:

```css
background: var(--card);       /* #FFFFFF */
border-radius: var(--radius);  /* 14px */
box-shadow: var(--shadow);     /* 0 4px 24px rgba(27,53,112,.10) */
padding: 28px 28px 32px;
```

Card-interne Trennflächen (Slider-Bereich, Ramp-Box) nutzen `var(--bg)` mit `border-radius: 10px`.

---

## Komponenten

### Buttons

**Primärer CTA (volle Breite):**
```css
background: var(--primary);
color: #fff;
border-radius: 9px;
padding: 15px;
font-weight: 700;
font-size: 1rem;
transition: background .18s, transform .1s;
/* :active → transform: scale(.99) */
```

**Toggle-Buttons (Rechteckig, z. B. Rampenart):**
```css
border: 2px solid var(--border);
border-radius: 10px;
padding: 12px 14px;
/* :hover → border-color: var(--secondary) */
/* .active → border-color + background: #EBF8FF */
```

**Toggle-Buttons (Pill-Form, z. B. Nutzergruppe):**
```css
border: 2px solid var(--border);
border-radius: 100px;
padding: 8px 14px;
/* .active → background + border: var(--secondary); color: #fff */
```

**Segment-Tabs (z. B. Berechnungsmodus):**
```css
border: 2px solid var(--border);
border-radius: 10px;          /* auf dem Container */
overflow: hidden;
/* .active → background: var(--primary); color: #fff */
/* Einzelne Tabs durch border-right: 2px solid var(--border) getrennt */
```

**Transition für alle interaktiven Elemente:** `all .18s` oder `border-color .18s, background .18s`.

---

### Inputs

```css
padding: 12px 46px 12px 14px;   /* rechts Platz für Einheit */
border: 2px solid var(--border);
border-radius: 9px;
font-size: 1rem;
font-weight: 600;
/* :focus → border-color: var(--secondary); outline: none */
/* :disabled → background: var(--bg); color: var(--muted) */
```

Einheiten (cm, m, %) werden als `position: absolute; right: 12px` im `font-weight: 700; color: var(--muted)` positioniert.

---

### Badges & Tags

Alle Badges nutzen `border-radius: 100px` (vollständig abgerundet):

| Badge-Typ         | Hintergrund          | Farbe     |
|-------------------|----------------------|-----------|
| Output-Badge      | `var(--secondary)`   | `#fff`    |
| HMV/Qty-Tag       | `var(--bg)`          | `var(--muted)` + Border |
| Match-Tag         | `#D4EDDA`            | `#1D8348` |
| Treffer-Count     | Dynamisch nach State | –         |

---

### Status-Indikatoren

Dreistufiges System mit Dot + Text:

```
s-ok   → background: var(--ok-bg);     color: var(--ok);     dot: var(--ok)
s-warn → background: var(--warn-bg);   color: var(--warn);   dot: #D4AC0D
s-bad  → background: var(--danger-bg); color: var(--danger); dot: #C0392B
```

Padding: `12px 16px`, Border-Radius: `9px`.

---

### Detail-Kacheln

Kleines Grid mit `border-left: 3px solid var(--secondary)` als farbiger Akzentstreifen:

```css
background: var(--bg);
border-radius: 9px;
padding: 14px 16px;
border-left: 3px solid var(--secondary);
```

Label: uppercase, muted. Wert: `1.1rem`, `font-weight: 700`, `var(--primary)`.

---

### Hinweis-Boxen (Notices)

Farbige Border-Left-Akzente für inhaltliche Hervorhebungen:

```css
/* Warnhinweis (gelb) */
background: #FFFBEB;
border: 1px solid #EDD56A;
border-left: 4px solid #D4AC0D;
border-radius: 9px;
padding: 14px 16px;
```

Icons in Hinweisboxen: `18×18px`, selbe Akzentfarbe wie `border-left`.

---

### Ergebnis-Display (Hero-Block)

Primäres Ergebnis-Element mit Gradient:

```css
background: linear-gradient(135deg, var(--primary) 0%, #253F88 100%);
border-radius: var(--radius);   /* 14px */
padding: 24px 28px;
color: #fff;
```

Ergebniswert: `3.2rem / 800`. Einheit daneben: `1.4rem / 400 / opacity .75`.

---

### Tabellen

```css
/* Header */
background: var(--bg);
font-size: .7rem; font-weight: 700; text-transform: uppercase; letter-spacing: .4px;
color: var(--muted);
border-bottom: 1px solid var(--border);

/* Zeilen-Divider */
border-bottom: 1px solid #EEF3F8;

/* Match-Zeile */
background: #E8F8EE;
border-left: 3px solid #27AE60;
```

---

## Border-Radius-System

| Wert   | Verwendung                                     |
|--------|------------------------------------------------|
| `14px` | Haupt-Cards, Ergebnis-Display (`--radius`)     |
| `10px` | Toggle-Buttons, Segment-Tabs, interne Flächen  |
| `9px`  | Inputs, Sekundäre Flächen, Status-Badges       |
| `8px`  | Kleinste Container (z. B. Produktbild)         |
| `100px`| Alle Pill-Formen (Badges, Tags, Nutzergruppen) |
| `50%`  | Runde Buttons (Slider +/−)                     |

---

## Schatten & Tiefe

Nur eine Schatten-Stufe:

```css
--shadow: 0 4px 24px rgba(27,53,112,.10)
```

Primär-Blau als Schattenfarbe (kein neutrales Schwarz) – gibt dem UI einen kohärenten Blaustich.

Header-Schatten: `0 2px 12px rgba(0,0,0,.25)` – etwas dunkler für die Trennung vom Content.

---

## Header

```css
background: var(--primary);
padding: 14px 28px;
/* Logo-Höhe: 52px */
/* Titel: 1.35rem / 700 / #fff */
/* Untertitel: .78rem / 400 / var(--secondary-light) */
```

---

## Interaktionsprinzipien

1. **Aktive States** sind immer durch `border-color: var(--secondary)` oder `background: var(--primary)` signalisiert – nie nur durch Farbe allein.
2. **Disabled-Felder** bekommen `var(--bg)` als Hintergrund und `cursor: not-allowed`.
3. **Output-Felder** (berechnete Werte) erhalten zusätzlich ein „Ergebnis"-Badge neben dem Label.
4. **Hover** ist immer `var(--secondary)` für Rahmen oder `var(--primary-hover)` für gefüllte Buttons.
5. **Transitions:** Einheitlich `0.18s` für alle Farbübergänge; `0.1s` für Transform-Effekte.

---

## Responsivität

Breakpoint: `max-width: 640px`

- Cards: Padding reduziert auf `20px 16px 24px`
- Mehrspaltige Grids → einspaltiger Stack
- Segment-Tabs: horizontal → vertikal (mit `border-bottom` statt `border-right`)
- Ergebnis-Display: `flex-direction: column`
- Slider-Grid: `1fr 1fr` → `1fr`

---

## Sonstiges

- **Produktbilder-Placeholder:** Dashed-Border (`1.5px dashed var(--border)`), `var(--bg)` Hintergrund, Bild-Icon in `var(--border)`.
- **SVG-Illustrationen** (z. B. Rampendiagramm) nutzen exklusiv die Brand-Farben `--primary`, `--secondary` sowie `#C0392B` (Rot) und `#1D8348` (Grün) für Maßlinien.
- **Schriftgröße Fußzeile:** `0.76rem`, `var(--muted)`, `line-height: 1.7`.
