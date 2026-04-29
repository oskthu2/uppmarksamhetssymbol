# Uppmärksamhetssignal — SVG-bibliotek

[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-blue)](https://oskthu2.github.io/uppmarksamhetssymbol/)

Ett SVG-baserat bibliotek för den svenska **Uppmärksamhetssignalen** — ett standardiserat medicinskt vårdsymbol med sju oberoende fält som kan tändas och släckas dynamiskt.

🌐 **Live-demo:** [oskthu2.github.io/uppmarksamhetssymbol](https://oskthu2.github.io/uppmarksamhetssymbol/)

---

## Om symbolen

Uppmärksamhetssignalen består av sju oberoende fält. Varje fält kan tändas eller släckas individuellt. Fältnumret i filnamnet beskriver vilka fält som lyser.

| Kod | Fält | Beskrivning |
|-----|------|-------------|
| `1` | Topp | Övre delen av utropstecknet |
| `0` | Ränder | Mitten av utropstecknet (fyra horisontella ränder) |
| `4` | Punkt | Nedre punkt av utropstecknet |
| `2` | Nordost | Övre höger pentagon |
| `3` | Sydost | Nedre höger pentagon |
| `5` | Sydväst | Nedre vänster pentagon |
| `6` | Nordväst | Övre vänster pentagon |

### Filnamnskonvention

Filer namnges enligt vilka fält som är tända:

| Filnamn | Fält | Betydelse |
|---------|------|-----------|
| `Signal` | inga | Tom symbol |
| `Signal.014` | Topp + Ränder + Punkt | Utropstecknet — livshotande överkänslighet |
| `Signal.25` | NE + SE | Allvarlig sjukdom / smitta |
| `Signal.0123456` | alla | Alla fält tända |

**Exempel:** `014` = topp (1) + ränder (0) + punkt (4) = utropstecknet.

---

## Användning

### Interaktiv demo (rekommenderas)

Öppna [`index.html`](index.html) i webbläsaren eller besök [live-demon](https://oskthu2.github.io/uppmarksamhetssymbol/) för:

- Live-editor där du tänder/släcker fält interaktivt
- Bibliotek med alla 128 kombinationer
- Sök och filtrera kombinationer
- Ladda ner enskilda SVG-filer

### Bädda in i HTML

```html
<!-- Lägg in SVG-koden direkt i din HTML -->
<svg viewBox="0 0 2010 1983" xmlns="http://www.w3.org/2000/svg">
  <!-- Symbolens kontur -->
  <path d="M 1627 991 L 2010 1204 L 1718 1733 ..." fill="#1a1a1a" fill-rule="evenodd"/>
  <!-- Fält 1: Topp -->
  <path data-field="1" d="M 736 60 L 1274 60 L 1274 740 L 736 740 Z" fill="#B60606"/>
  <!-- Fält 0: Ränder -->
  <path data-field="0" d="M 736 820 L 1274 820 ..." fill="#B60606"/>
  <!-- Fält 4: Punkt -->
  <path data-field="4" d="M 740 1640 a 265 265 0 ..." fill="#FA7070"/>
</svg>
```

### Använda React-komponenten

Projektet innehåller en `<UmiSymbol>` React-komponent (se `UMI.zip`):

```jsx
// Rendera med aktiva fält som sträng
<UmiSymbol active="014" size={120} />

// Rendera med aktiva fält som array
<UmiSymbol active={[0, 1, 4]} size={120} />

// Hämta SVG-koden som sträng (t.ex. för nedladdning)
const svg = umiSvgString({ active: "25" });
document.body.innerHTML = svg;

// Anpassade färger per fält
<UmiSymbol active="0123456" colors={{ "0": "#000", "4": "#FF6B6B" }} />
```

---

## Geometri

- **ViewBox:** `0 0 2010 1983`
- Alla path-data är härledda från originalkällan (PowerPoint-vektorgrafik)
- Symbolens kontur använder `fill-rule="evenodd"`
- Fälten är separata `<path>`-element med `data-field`-attribut för enkel CSS/JS-styrning

---

## Filer i repot

| Fil | Beskrivning |
|-----|-------------|
| `index.html` | Fristående interaktiv sida — fungerar offline, ingen server krävs |
| `UMI.zip` | Fullständigt källkodsprojekt (React-komponenter, bilder, PowerPoint-original) |

---

## Publicera på GitHub Pages

Repot är konfigurerat för automatisk publicering via GitHub Actions.

**Manuell aktivering:**
1. Gå till **Settings → Pages** i repot
2. Under *Source*, välj **GitHub Actions**
3. Sidan publiceras automatiskt vid varje push till `main`

---

## Licens

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/deed.sv)

Detta verk är licensierat under **CC0 1.0 Universell** — fri att använda utan begränsningar.  
Mer information: <https://creativecommons.org/publicdomain/zero/1.0/deed.sv>
