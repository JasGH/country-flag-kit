# country-flags-svg

![license](https://img.shields.io/badge/license-MIT-blue)
![flags](https://img.shields.io/badge/flags-271-brightgreen)
![ratios](https://img.shields.io/badge/ratios-4%3A3%20%26%201%3A1-orange)

Clean, undistorted **country flags** as SVGs in **two ratios — 4:3 and 1:1** — with an
ISO‑3166 manifest. Built for phone‑number country pickers, locale selectors, and dropdowns.

- **271 flags**, named by lowercase ISO 3166‑1 alpha‑2 code (`kw`, `us`, `sa`, …).
- Based on [flag‑icons](https://github.com/lipis/flag-icons) — hand‑drawn natively at each
  ratio, so emblems are **never stretched or distorted**.

## Install

```bash
npm install country-flags-svg
# or clone
git clone https://github.com/YOUR_GITHUB_HANDLE/country-flags-svg.git
```

## Usage

```html
<!-- rectangular 4:3 -->
<img src="4x3/kw.svg" width="24" alt="Kuwait">
<!-- square 1:1 -->
<img src="1x1/kw.svg" width="20" alt="Kuwait">
```

Build a country dropdown from the manifest:

```js
import flags from "country-flags-svg";   // index.json

const square = false;
const countries = flags.filter(f => f.iso);          // 249 real countries
for (const c of countries) {
  const opt = document.createElement("option");
  opt.value = c.code;                                // "KW"
  opt.textContent = c.name;                          // "Kuwait"
  select.append(opt);
}
img.src = flags.find(f => f.code === code)[square ? "file_1x1" : "file_4x3"];
```

Round flags: in 1:1, add `border-radius:50%` in your CSS.

### `index.json`

```json
{ "code":"KW", "name":"Kuwait", "continent":"Asia", "iso":true,
  "file_4x3":"4x3/kw.svg", "file_1x1":"1x1/kw.svg" }
```

`iso:true` marks real ISO 3166‑1 entries (filter to exclude org/region flags like EU, UN).

## Demo

Open `index.html` for an interactive gallery — search, filters, **4:3 ⇄ 1:1 toggle**,
click‑to‑copy. Publish it free via **GitHub Pages** (Settings → Pages → deploy from branch).

## Structure

```
.
├── 4x3/            271 rectangular SVGs (4:3)
├── 1x1/            271 square SVGs (1:1)
├── index.json      ISO-3166 manifest
├── index.html      interactive gallery / demo
├── package.json    npm metadata
├── CHANGELOG.md
└── LICENSE         MIT (code) + flag-icons attribution
```

## Colors

Flags use flag‑icons' colors (Wikipedia‑sourced, the widely used standard). **Marshall
Islands** is recolored to its official deep blue (`#003087`) and orange (`#E57200`).

## License

MIT — see `LICENSE`. Flag artwork is from flag‑icons (MIT, © 2013 Panayiotis Lipiridis).

---

**Before you publish**, replace the placeholders: `YOUR_GITHUB_HANDLE` and `YOUR_NAME`
(in `package.json` and `LICENSE`), and confirm the npm name `country-flags-svg` is free —
if not, scope it as `@YOUR_HANDLE/country-flags`.
