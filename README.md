# DITO — Drop In The Ocean 🌊

### ▶️ **[Launch the live app →](https://umairjmanj.github.io/DITO/)**

No install, no sign-up — runs free in your browser on any device (phone or desktop).

---

DITO is a playful, minimalist, **offline-first** mobile web application and SDK. It evaluates your technical innovation entirely on-device, and can *optionally* call a **free, keyless public AI** for a richer second opinion when you're online.

DITO evaluates technical innovations (up to 400 words) completely offline and locally on the device, measuring their contribution toward the ultimate benchmark: *humanity controlling the entire universe* — guided by **Manj**, the app's caveman-engineer mascot.

---

## 🎨 Design Philosophy
- **Hand-Drawn Style:** Uses organic, asymmetric sketch-borders (`border-radius: 255px 15px...`) and hand-drawn outline drops.
- **Typography:** Uses Google Fonts' handwriting styles (`Caveat` and `Architects Daughter`) combined with `Share Tech Mono` for a fun "stone-age meets futuristic data" readout.
- **Ocean of Knowledge:** Submitting innovations triggers a physics-based animation of blue drops falling into a stone basin.
- **Manj's Cave Wisdom:** Instantly displays motivational caveman-voice feedback based on the technological impact of the submission.
- **Cave Carvings Log:** Caches past submissions in the browser's `localStorage` to keep a timeline of tools carved on the cave wall.

---

## 🧠 SDK Architecture (`sdk/cosmic-sdk.js`)
DITO runs a **real evaluation completely offline** on any mobile web browser or wrapped native shell — **no account, no API key, zero server-side computation, and nothing leaves the device.**

### The five-axis scoring engine (the "small smart engine")
Instead of naïvely counting keyword hits, the SDK scores **meaning and structure** across five interpretable axes (each 0–100%), then combines them:
- **Specificity** — density of genuinely technical, distinctive vocabulary (vague hand-waving scores low).
- **Depth** — how strongly the text engages its core field.
- **Breadth** — how many disciplines it *genuinely* spans (out of 10 divisions).
- **Novelty** — reach toward frontier / ambitious concepts.
- **Coherence** — an **anti-keyword-stuffing gate**: real prose (lexical variety + connective words) scores high; a buzzword-salad gets its score *squared down* no matter how many frontier terms it spams.

Keyword matching is **IDF-weighted** — rare, distinctive terms (e.g. *entanglement*, *perovskite*) count far more than generic ones (*system*, *studies*) — and phrase matching is **word-boundary safe** (so `"ion"` no longer matches inside *"station"*).

### Concept understanding (the local "small brain")
A compact, hand-curated **concept lexicon** lets the engine understand whole *ideas*, not just stray words. For example, *"a laptop that helps time travel"* is correctly read as **Physics** (spacetime / relativity), with Computing and Engineering as secondary disciplines — instead of the word "time" accidentally lighting up every *"Real-Time"* Computer-Science domain. Each concept maps to weighted disciplines and surfaces a clean, relevant domain tag. It's tiny to ship and runs entirely on-device.

### Multi-scale civilizational comparison
Rather than a single "vs the 1950s transistor" number, DITO places your idea on a curated timeline of **16 real milestones in human capability** — from the **first stone tools (~3.3M BCE)** through fire, language, agriculture, the wheel, writing, printing, steam, electricity, the transistor, spaceflight, the web, the smartphone and generative AI, out to **projected** futures (solar-system automation, a Dyson swarm). Your contribution is shown *between* two milestones and compared, at once, against the stone axe, the wheel, the transistor and today's AI.

> **Honesty note:** the capability `index` values are **illustrative** (a log-style heuristic), not measured physical constants. A single innovation almost always lands modestly on this scale — which is exactly the point of *Drop In The Ocean*.

### 🤖 Optional free AI boost (no keys, ever)
In **Settings → Free Online AI Boost**, you can let DITO send *only the text you type* to [Pollinations.ai](https://pollinations.ai) — a **free, keyless, open public AI** anyone can use with no sign-up. It adds a richer caveman-wisdom line and a plain-English critique (biggest strength + biggest gap). **No API keys are involved — not yours, and none belonging to the app author.** The honest offline numbers always run first and stay authoritative; if the service is slow or down, DITO silently falls back to the offline engine. With the toggle **off**, nothing ever leaves your device.

---

## 🚀 Running Locally
To launch DITO in your local browser:
1. Ensure you have **Node.js** installed.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the local server:
   ```bash
   npm start
   ```
4. Open the browser to [http://localhost:8080](http://localhost:8080).

---

## 📱 Packaging for Android & iOS (via Capacitor)
You can compile DITO into a native `.apk` (Android) or Xcode project (iOS) using Ionic's Capacitor wrapper:

1. **Initialize Capacitor:**
   ```bash
   npm run cap:init
   ```
   *Follow the CLI prompts to set App Name: `DITO`, App Package ID: `dito.ocean.app`, and web directory: `.`.*

2. **Add Android Target:**
   ```bash
   npm run cap:add-android
   ```

3. **Add iOS Target:**
   ```bash
   npm run cap:add-ios
   ```

4. **Sync Web Assets:**
   Every time you modify the HTML/CSS/JS, sync the changes to the native platforms:
   ```bash
   npm run cap:sync
   ```

5. **Open & Build in Android Studio:**
   ```bash
   npm run cap:open-android
   ```
   *This launches Android Studio pre-loaded with the native wrapper. You can build your debug or release APK directly from there!*

---

## 🛠️ Code Structure
- [`index.html`](index.html) — structural layout and SVG animated drop area.
- [`index.css`](index.css) — sketchy layout styling, handwritten fonts, and physics drop-falling keyframes.
- [`app.js`](app.js) — UI event binding, presets injector, falling-drop generation, the multi-scale/axes renderers, and the optional free-AI boost.
- [`sdk/cosmic-sdk.js`](sdk/cosmic-sdk.js) — the offline evaluation engine: the concept lexicon, IDF-weighted domain matching, the five scoring axes, and the multi-scale civilizational timeline. **Usable standalone** — see [`sdk/README.md`](sdk/README.md).
- [`generate_domains.js`](generate_domains.js) — script used to generate the knowledge-domain database in the SDK.
- [`package.json`](package.json) — build scripts and dependencies.
- [`capacitor.config.json`](capacitor.config.json) — Capacitor native-wrapper configuration.

---

## 📄 License
Released under the **MIT License** — see [`LICENSE`](LICENSE).
