# fui-console

A Claude skill for building original **cinematic sci-fi interfaces** (FUI): the dense, glowing screens from starship bridges and mission-control scenes. Each console is a single self-contained HTML file you can open full screen and leave running, either on **live public data** or as a **pure fiction scene**.

The included example, **MERKLE-21**, is a Bitcoin proof-of-work observatory running on live mempool.space data. See it live at [notfinancialfinancialadvice.com/consoles/btc](https://notfinancialfinancialadvice.com/consoles/btc).

## What the skill teaches Claude

- Writing a concept first: callsign, plain name, imagined station, hero visual, palette, data map
- The anatomy that makes a screen read as FUI: animated canvas hero, dense instrument rails, logs, ticker, status pill
- Build rules: one file, no build step, no API keys, snapshot fallback, live/stale states, reduced-motion support
- Testing at desktop and phone widths, with mocked data
- An originality rule: learn the genre, never copy a specific work

## Install

**Claude Code** (personal, all projects):

```bash
git clone https://github.com/eddieicecold3000/fui-console-skill.git
cp -r fui-console-skill/fui-console ~/.claude/skills/
```

For one project only, copy the `fui-console` folder into that project's `.claude/skills/` instead.

**Claude apps (claude.ai / desktop):** zip the `fui-console` folder and upload it under Settings → Capabilities → Skills.

## Use

Ask for something like:

- "Make a FUI console for live earthquake data"
- "Build a sci-fi fiction scene: a deep-space cargo tug's cockpit"
- "Make a console like MERKLE-21 for Ethereum gas prices"

## Files

```
fui-console/
├── SKILL.md                 # the skill
└── examples/
    └── merkle-21.html       # complete working example (live Bitcoin data)
```

## License

MIT. See [LICENSE](LICENSE).
