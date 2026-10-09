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
- Hero visual: the one big animated thing in the center that embodies the subject (hashrate ring, orbit, terrain, waveform, seismograph, order-book canyon).
- Palette: one dominant phosphor hue, one cool secondary, one alert color, on a near-black ground tinted toward the dominant hue. Pick hues from the subject's world (amber for proof-of-work heat, green for growth, red-orange for volcanic), not by habit.
- Data map (data mode): every panel mapped to its exact API field and refresh interval.

## 3. Anatomy that makes it read as FUI

- Header strip: callsign plus plain name, a real UTC clock, a status pill (LIVE / STALE / SNAPSHOT), a full-screen button.
- Hero stage: the center 40 to 55 percent of the screen, drawn on a canvas element with requestAnimationFrame. Slow, continuous motion plus one punctuating event (MERKLE-21 fires a shockwave on each new block).
- Side rails: 3 to 5 instrument modules each. A module is a tiny uppercase label with a corner tick, one big tabular number, then dense label/value rows and a thin progress bar.
- Logs and queues: a timestamped stream or ledger (block log, event log) with status tags. This is where the world feels inhabited.
- Ticker: a scrolling footer line repeating the key figures.
- Density: many small, precise readouts with real units, sigma, P50/P99 and the domain's own abbreviations. Dense but aligned: tabular numbers, consistent label/value columns.
- Texture: faint grid, 1 to 3px scanlines, subtle glow only on the dominant hue.
- Copy written from inside the world: terse and specific. In fiction mode, let a few log lines carry story. In data mode every value is true, and anything decorative is labeled honestly (e.g. "PARTICLES - AMBIENT, NOT INDIVIDUAL TX").

## 4. Build rules

- One .html file with inline CSS and JS. No build step, no frameworks, no API keys. Only external loads: Google Fonts (with fallback stacks) and the data API.
- Fonts: one technical display face plus one mono for data (e.g. Chakra Petch + Share Tech Mono). Vary them per console.
- Colors as CSS custom properties on :root; a single dark look is fine (color-scheme: dark).
- Layout: CSS grid with minmax(0,1fr) rails. Under about 880px, stack to one column with the hero first. Never scroll sideways.
- Canvas: size with ResizeObserver and devicePixelRatio (cap at 2); derive every radius from the stage size so nothing overlaps the captions.
- Live data: one loader per endpoint with its own interval (fast feeds about 20s, history about 30 min). Pause while document.hidden, refresh on return. Always ship a baked-in snapshot so the page renders fully before or without the API, and flip the status pill SNAPSHOT to LIVE, then STALE after 2 minutes without a successful fetch.
- Respect prefers-reduced-motion (freeze rotation, stop the ticker). Request wake lock and fullscreen on the button click and tolerate failure.
- Credit the data source with a link. For financial data, add "Not financial advice."

## 5. Verify before handing it over

- Render at desktop (about 1400x820) and phone (about 400x860) widths, e.g. with Playwright. Check: no console errors, no overlap between hero and captions, no sideways scroll.
- Data mode: run once with mocked API responses (route the API host in Playwright) and confirm every panel updates and the pill reads LIVE. Then load it once against the real API.
- Read every number on screen once: right units, no NaN, no placeholder text.

## 6. Deliver

- The file runs anywhere: double-click to open locally, drop it into any static host, or serve it from a route in an existing app. If an app uses a template engine (Jinja, Nunjucks, Handlebars), serve the file raw, because the inline JS uses template-literal syntax.
- Where a hosted preview can't make outside network calls (some sandboxed previews), a data console shows its snapshot and the pill stays on SNAPSHOT. Say so rather than calling it broken.
