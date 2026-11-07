---
name: fui-console
description: Build an original cinematic sci-fi interface (FUI) console as one self-contained HTML page, on live public data or as pure fiction. Use for requests like "make a sci-fi dashboard for X", "FUI", "movie-style interface", or "a console like MERKLE-21".
---

# FUI Console

Makes a full-screen "fictional user interface": the dense, glowing kind of screen you'd see on a starship bridge or in a mission-control movie scene. Each console is one self-contained HTML file that people open, put in full screen, and leave running.

A complete working example is in `examples/merkle-21.html`: a Bitcoin proof-of-work observatory on live mempool.space data. Read it before building your first console; it shows every pattern below in practice.

Originality rule: study the genre, never copy a specific work. Don't reuse scene names, layouts, fictional worlds, copy, or code from existing FUI galleries, films, or games. Every console must be an original concept.

## 1. Pick the mode

- Data console: real public data rendered cinematically (crypto networks, earthquakes, weather, space weather, transit, flight traffic, markets). Accuracy matters; the fiction is only in the framing.
- Fiction scene: a pure story world (a terraforming station, a deep-sea sonar, a reactor in trouble). No real data; every number is invented but internally consistent.

For a data console, first find a free, keyless, CORS-enabled public API and confirm it answers from a browser (a fetch from a real page, not just curl). If none exists, say so and offer a fiction scene or a baked-in snapshot instead.

## 2. Write the concept before any code

Keep it as an HTML comment at the top of the file:
- Callsign: short code name, letters plus a number (MERKLE-21 style). Original.
- Plain name: what it is in normal words ("Bitcoin proof-of-work observatory"). Always shown next to the callsign so viewers know what they're looking at.
- Station: the imagined operator or institution, and why the screen exists.
- Metaphor and hero: the physical metaphor and hero archetype from section 3, and how each data rule maps onto it.
- Composition, palette family and fonts from section 3. Within the palette: one dominant hue, one cool secondary, one alert color. Pick hues from the subject's world (amber for proof-of-work heat, teal for water, red-orange for volcanic), not by habit.
- Data map (data mode): every panel mapped to its exact API field and refresh interval.

## 3. Vary the shape: no two consoles alike

The fastest way to make consoles feel samey is to reuse one layout: a round hero in the middle, a column of stacked modules on each side, one glow color on black, a ticker. Good FUI galleries almost never repeat a composition. Treat that layout as one option among many, never the default.

Start from a physical metaphor. Ask what real-world instrument or workplace would watch this data, and what the data's rules look like as physical things. The best heroes are ones where the rules map literally: a reserve-backed token as a seawall (market price is the sea level, NAV is the wall's crest, the buyback bid is a sluice gate, the reserves are strata behind the wall). If the metaphor needs a paragraph to explain, pick another.

Then choose one from each list, and write the choices into the concept comment.

Hero archetype:
- Radial instrument: ring, dial, orbit, clock. Good for cycles and rates. The most overused; justify it.
- Cross-section or cutaway: a side view through ground, water, a hull, a vessel. Good for levels, layers and thresholds.
- Top-down map or terrain: contours, a perimeter, a line that must hold. Good for spread, coverage, fronts.
- Isometric field of blocks: one block per item (epoch, sector, district), height and color as data. Good for many similar items over time.
- Waterfall or echogram: time scrolls one way, intensity paints a heatmap. Good for streams of events.
- Table as hero: a dense ledger or life table is the star, one live row highlighted, a staircase chart beside it. Good when history per row is the story.
- Horizon strip: one long timeline band across the full width, everything else below. Good for long histories with marked events.
- Network or fan-out: a central cause wired to the things it affects, each wire ending in a sparkline. Good for dependencies.
- Wireframe volume: nested 3D surfaces with structures called out. Good for limits and envelopes.
- Head-to-head board: two giant opposing figures with a split bar, results called like races. Good for any A-versus-B.

Composition:
- Hero across the full width on top, a row of mixed-size panels beneath.
- Hero off-center (top-left), a tall table on the right, small multiples along the bottom.
- Horizon band on top, four or five columns below.
- Table-dominant: the ledger fills most of the screen, a narrow chart rail beside it.
- Three columns with the hero centered: allowed, but not twice in a row.
Panels should vary in size. Equal rails on both sides read as a template.

Panel vocabulary (use at least three, and not only label/number/rows modules):
- Leader-line callouts pinned onto the hero itself, so the hero reads as an annotated diagram.
- A rules or constraints table with limit, actual and PASS / FAIL / WATCH tags.
- Small multiples: a strip of 6 to 8 tiny repeated charts (per epoch, per week, per station).
- Giant opposing figures across the top.
- Cumulative or envelope curves with the live point marked.
- Big countdown clocks (T-04:52:10) for the next scheduled event.
- A matrix heatmap, a film strip of states over time, a fan of wires.
- Logs with status tags, as before.

Palette family (vary it, and go beyond glow-on-black):
- Phosphor on near-black (amber, green, cyan): the classic.
- Amber on a pale paper or chart-table panel.
- Mainframe blue: blue ground, white and cyan type, highlighted column bars.
- Map red: dark red ground, hot red lines, one cool line that must hold.
- Two rival team colors (gold versus blue) for head-to-head subjects.
- Night harbor: blue-black ground, teal water, bone-white concrete, one signal orange.
Fonts change every time: pair a display face that fits the world (condensed signage, wide technical, typewriter) with a different mono.

Variety check before coding: compare the planned hero archetype, composition, palette family and fonts against the consoles already built (see the registry below, or list them first). Change at least three of the four from the most recent console, and never reuse a hero archetype used by the last two.

Keep a registry of the consoles you have built in a project (a table of hero archetype, composition, palette family and fonts) and update it each time, so the next one can be checked against it.

## 4. Anatomy that makes it read as FUI

- Header strip: callsign plus plain name, a real UTC clock, a status pill (LIVE / STALE / SNAPSHOT), a full-screen button.
- Hero stage: 40 to 60 percent of the screen, placed per the chosen composition, drawn on a canvas element with requestAnimationFrame. Slow, continuous motion plus one punctuating event tied to real data (a shockwave on each new block, a burst on each burn). Pin leader-line callouts to the parts of the hero they describe.
- Instrument modules: a tiny uppercase label with a corner tick, one big tabular number, then dense label/value rows and a thin progress bar. Mix them with the other panel types from section 3 rather than stacking only these.
- Logs and queues: a timestamped stream or ledger (block log, event log) with status tags. This is where the world feels inhabited.
- Ticker: optional. A scrolling footer line repeating the key figures, used when it suits the world.
- Density: many small, precise readouts with real units, sigma, P50/P99 and the domain's own abbreviations. Dense but aligned: tabular numbers, consistent label/value columns.
- Texture: faint grid, 1 to 3px scanlines or paper grain, subtle glow only on the dominant hue.
- Copy written from inside the world: terse and specific. In fiction mode, let a few log lines carry story. In data mode every value is true, and anything decorative is labeled honestly (e.g. "PARTICLES - AMBIENT, NOT INDIVIDUAL TX").

## 5. Build rules

- One .html file with inline CSS and JS. No build step, no frameworks, no API keys. Only external loads: Google Fonts (with fallback stacks) and the data API.
- Fonts: one display face plus one mono for data, a pairing not used by earlier consoles (see section 3).
- Colors as CSS custom properties on :root; a single dark look is fine (color-scheme: dark).
- Layout: CSS grid with minmax(0,1fr) tracks. Under about 880px, stack to one column with the hero first. Never scroll sideways. On phones, hide callouts that would collide rather than shrinking them to unreadable sizes.
- Canvas: size with ResizeObserver and devicePixelRatio (cap at 2); derive every radius from the stage size so nothing overlaps the captions.
- Live data: one loader per endpoint with its own interval (fast feeds about 20s, history about 30 min). Pause while document.hidden, refresh on return. Always ship a baked-in snapshot so the page renders fully before or without the API, and flip the status pill SNAPSHOT to LIVE, then STALE after 2 minutes without a successful fetch.
- Respect prefers-reduced-motion (freeze rotation, stop the ticker). Request wake lock and fullscreen on the button click and tolerate failure.
- Credit the data source with a link. For financial data, add "Not financial advice."

## 6. Verify before handing it over

- Render at desktop (about 1400x820) and phone (about 400x860) widths, e.g. with Playwright. Check: no console errors, no overlap between hero and captions, no sideways scroll.
- Data mode: run once with mocked API responses (route the API host in Playwright) and confirm every panel updates and the pill reads LIVE. Then load it once against the real API.
- Read every number on screen once: right units, no NaN, no placeholder text.
- Look at the desktop screenshot next to the previous console's. If they read as the same layout at a glance, go back to section 3.

## 7. Deliver

- The file runs anywhere: double-click to open locally, drop it into any static host, or serve it from a route in an existing app. If an app uses a template engine (Jinja, Nunjucks, Handlebars), serve the file raw, because the inline JS uses template-literal syntax.
- Where a hosted preview can't make outside network calls (some sandboxed previews), a data console shows its snapshot and the pill stays on SNAPSHOT. Say so rather than calling it broken.
