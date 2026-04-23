# Jamall Coaching Portal — PWA

A mobile-first coaching dashboard with weight tracking, macros, training split and coach notes. Installs to your home screen like a real app.

## What's inside

- **Dashboard** — current weight (kg/lb toggle), 59-week trend chart, goal progress vs 118kg / 115kg / 110kg targets, this week's coach notes
- **Log** — add new weigh-ins (auto-calculates week number and change), full 59-week history
- **Diet** — training-day + rest-day macros, all 5 meals, full supplement stack
- **Training** — 4-day split (Full Body / Upper / Legs / Arms+Delts) with every exercise, sets, rep ranges, and last recorded loads

All your historical data from the coaching spreadsheet is pre-loaded (300.2 → 265.9 lb / 136.2 → 120.6 kg across 55 weeks of tracked check-ins). New weigh-ins save to the phone's local storage and persist between visits.

## How to install on your phone

### iPhone (Safari)
1. Open `index.html` via any of the hosting options below
2. Tap the Share icon (square with arrow)
3. Scroll down, tap **Add to Home Screen**
4. Tap **Add** — the JAMALL icon appears on your home screen
5. Open it — runs full-screen, no browser chrome

### Android (Chrome)
1. Open `index.html` in Chrome
2. You'll see an **Install app** banner at the top — tap **Install**
3. Or: tap the ⋮ menu → **Install app** / **Add to Home Screen**

## How to host it

You need a URL that serves these files. A few easy options:

**Option 1 — GitHub Pages (free, permanent)**
1. Create a new repo on github.com
2. Upload all 5 files to the root of the repo
3. Settings → Pages → deploy from `main` branch / root
4. You get `https://<you>.github.io/<repo>/` — open that on your phone

**Option 2 — Netlify Drop (free, instant)**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the whole folder in
3. You get a URL like `https://random-name.netlify.app` — open on phone

**Option 3 — Local test**
```bash
cd folder-with-these-files
python3 -m http.server 8000
```
Then go to `http://<your-computer-ip>:8000/index.html` from your phone on the same WiFi. Note: full PWA install only works over HTTPS, so this is preview-only.

## Files

| File | What it does |
|------|--------------|
| `index.html` | The whole app — HTML, CSS, JS, all your data |
| `manifest.json` | Tells the phone this is an installable app |
| `sw.js` | Service worker — caches for offline use |
| `icon-192.png` | App icon (home screen) |
| `icon-512.png` | App icon (splash screen) |

All in one folder, all stay together.

## Customising

Everything is in `index.html`. Open it in any text editor:

- **Weight goals** — search for `g1`, `g2`, `g3` in the `<script>` section; change target kg
- **Macros** — in the `view-diet` section, edit the numbers directly
- **Meals** — same section, add/remove food rows
- **Training** — find `const WORKOUTS =` in the script; add exercises, update loads after each session
- **Coach notes** — search for `CHECK-IN HIGHLIGHTS`; update the quote and bullets weekly

## Data

Your historical weigh-ins are hardcoded in `SEED_DATA` (top of the script). New entries you add via the Log screen go to browser local storage (`jamall.data`). They don't sync between devices — this is a single-phone app unless you wire it up to a backend.

If you want to wipe and start over: open the app, in your phone browser DevTools clear local storage for this site, or uninstall + reinstall.
