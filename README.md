# Attention Signal (Uppmärksamhetssignal) — SVG Library

[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-blue)](https://oskthu2.github.io/uppmarksamhetssymbol/)

An SVG-based library for the Swedish **Attention Signal** (Uppmärksamhetssignalen / UMI) — a standardised medical care symbol with seven independent fields that can be toggled on and off dynamically.

🌐 **Live demo:** [oskthu2.github.io/uppmarksamhetssymbol](https://oskthu2.github.io/uppmarksamhetssymbol/)

---

## About the symbol

The Attention Signal (UMI — Uppmärksamhetssignal inom informationshantering) is a standardised Swedish medical symbol used in healthcare IT systems to flag important patient information such as severe allergies or infectious diseases. It consists of seven independent fields. Each field can be toggled on or off individually. The field number in the filename describes which fields are active.

**Further reading:**
- [Warning Information — international overview of the UMI symbol](https://sites.google.com/site/warninginformation/)
- [Socialstyrelsen — Uppmärksamhetssignal (Swedish National Board of Health and Welfare)](https://www.socialstyrelsen.se/regler-och-riktlinjer/foreskrifter-och-allmanna-rad/konsoliderade-foreskrifter/200814-om-informationshantering-och-journalforing-i-halso--och-sjukvarden/)

| Code | Field | Description |
|------|-------|-------------|
| `1`  | Top    | Upper part of the exclamation mark |
| `0`  | Stripes | Middle of the exclamation mark (four horizontal stripes) |
| `4`  | Dot    | Lower dot of the exclamation mark |
| `2`  | Northeast | Upper right pentagon |
| `3`  | Southeast | Lower right pentagon |
| `5`  | Southwest | Lower left pentagon |
| `6`  | Northwest | Upper left pentagon |

### Filename convention

Files are named according to which fields are active:

| Filename | Fields | Meaning |
|----------|--------|---------|
| `Signal` | none | Empty symbol |
| `Signal.014` | Top + Stripes + Dot | Exclamation mark — life-threatening hypersensitivity |
| `Signal.25` | NE + SE | Serious illness / infection |
| `Signal.0123456` | all | All fields active |

**Example:** `014` = top (1) + stripes (0) + dot (4) = the exclamation mark.

---

## Usage

### Interactive demo (recommended)

Open [`index.html`](index.html) in a browser or visit the [live demo](https://oskthu2.github.io/uppmarksamhetssymbol/) for:

- Live editor to toggle fields interactively
- Library of all 128 combinations
- Search and filter combinations
- Download individual SVG files
- **Language toggle** (SWE / ENG) in the upper corner

### Embed in HTML

```html
<!-- Inline the SVG code directly in your HTML -->
<svg viewBox="0 0 2010 1983" xmlns="http://www.w3.org/2000/svg">
  <!-- Symbol outline -->
  <path d="M 1627 991 L 2010 1204 L 1718 1733 ..." fill="#1a1a1a" fill-rule="evenodd"/>
  <!-- Field 1: Top -->
  <path data-field="1" d="M 736 60 L 1274 60 L 1274 740 L 736 740 Z" fill="#B60606"/>
  <!-- Field 0: Stripes -->
  <path data-field="0" d="M 736 820 L 1274 820 ..." fill="#B60606"/>
  <!-- Field 4: Dot -->
  <path data-field="4" d="M 740 1640 a 265 265 0 ..." fill="#FA7070"/>
</svg>
```

### Using the React component

The project includes a `<UmiSymbol>` React component (see `UMI.zip`):

```jsx
// Render with active fields as a string
<UmiSymbol active="014" size={120} />

// Render with active fields as an array
<UmiSymbol active={[0, 1, 4]} size={120} />

// Get the SVG code as a string (e.g. for download)
const svg = umiSvgString({ active: "25" });
document.body.innerHTML = svg;

// Custom colours per field
<UmiSymbol active="0123456" colors={{ "0": "#000", "4": "#FF6B6B" }} />
```

---

## Geometry

- **ViewBox:** `0 0 2010 1983`
- All path data is derived from the original source (PowerPoint vector graphics)
- The symbol outline uses `fill-rule="evenodd"`
- Fields are separate `<path>` elements with `data-field` attributes for easy CSS/JS control

---

## Files in this repo

| File | Description |
|------|-------------|
| `index.html` | Standalone interactive page — works offline, no server required |
| `UMI.zip` | Full source code project (React components, images, PowerPoint original) |

---

## Publishing on GitHub Pages

The repo is configured for automatic publishing via GitHub Actions.

**Manual activation:**
1. Go to **Settings → Pages** in the repo
2. Under *Source*, select **GitHub Actions**
3. The page is published automatically on every push to `main`

---

## Licence

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

This work is licensed under **CC0 1.0 Universal** — free to use without restrictions.  
More information: <https://creativecommons.org/publicdomain/zero/1.0/>
