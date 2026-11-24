# Northview Spring Picker

Field tool for picking a replacement 2″ torsion spring pair from truck inventory, given door height, door weight and track type.

- **Live:** https://northviewdoorsystems.github.io/spring-picker/
- **Hosting:** GitHub Pages, deploy from branch `main`, folder `/ (root)`
- **iPhone:** open the live URL in Safari → Share → Add to Home Screen

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app: markup, styles, script, spring data, and the logo (embedded) |
| `apple-touch-icon.png` | 180×180 home-screen icon. Filename is referenced by `index.html`; keep it exact. |

No build step, no sign-in, no external data. Fonts load from Google Fonts and fall back to system fonts if offline.

## How it picks

Pair lift = (IPPT × 2) ÷ drum multiplier. The pick is the pair whose lift is closest to door weight.

- **IPPT, dimensions, cycle ratings:** Northview Torsion Spring Reference (Updated 11/2026). Mixed pairs use the average IPPT of the two springs, as on the chart.
- **Multipliers and turns:** Canimex/Action D400-96 standard-lift drum table (HMA 2.275″), 6′0″–8′2″, columns 12″ radius, 15″ radius, low headroom.
- **Low headroom** assumes front-mount double track on standard 4″ drums. Not valid for rear-mount or low-headroom drums.
- **Cycles** are the chart's 15″ ratings interpolated by turns (7′ = 7.9 turns, 8′ = 8.8 turns).

## Known data issues

- The printed chart's 8′ column uses a 0.2500 multiplier; the D400-96 15″ value is 0.2579. This tool uses 0.2579, so 8′ lifts read about 3% below the printed chart.
- Gold (High Cycle) is identical to standard Gold on the chart. Confirm before relying on it.

## Updating

- **Spring inventory changes:** edit the `S` array in `index.html` (name, colors, dimensions, IPPT per spring, cycles @ 7′, cycles @ 8′, high-cycle flag). Keep it in step with the printed reference chart.
- **Deploy:** upload the changed file to `main`. Pages republishes in about a minute. On the iPhone, close and reopen the home-screen app.
