# VV Design System

The **Visualize Value (Jack Butcher)** design + voice system, extracted as a reusable knowledge base. Feed this repo to Claude (or any model) to build, style, and critique designs in the VV aesthetic.

## What this is

This is the design-relevant subset of the `vv-creator` skill — everything needed to *produce* VV-style work, with the bulk research corpus stripped out.

| Path | Purpose |
|------|---------|
| `SKILL.md` | The full operating manual: modes, filters, construction rules. **Start here.** |
| `references/visual-style-guide.md` | The visual system — palette, typography (Carbon Bold + Space Grotesk), table/chart rules. Read before any visual. |
| `references/writing-profile.md` | The voice system — rhetorical patterns, banned words, contrast frames, rewrite examples. Read before any copy. |
| `references/frameworks/` | Six mental models: productization spectrum, shuhari, time ladder, TRAIN, permissionless apprentice, proof-price loop. |
| `assets/Carbon-Bold.ttf` | The Carbon Bold font. Embed via `@font-face` in generated HTML. |

## How to use with Claude

1. Point Claude at this repo.
2. Tell it: *"Read `SKILL.md` and `references/` in full, then [build / style / critique] X in the VV system."*
3. For visuals, it must read `references/visual-style-guide.md` and embed `assets/Carbon-Bold.ttf`.
4. For copy, it must read `references/writing-profile.md` end to end (not a summary).

## Intentionally omitted

The original skill's `data/` directory — `tweet-index.json` (50k+ tweets), `visual-index.json` (400+ visuals), `visual-descriptions.json`, `courses.json`, `projects.json` — is **not** included. Those are a research corpus for sourcing/quoting real VV content, not for building a design system. `SKILL.md` references them; ignore those references when using this repo as a design feed.

---

*Source: `vv-creator` skill (Visualize Value system). This repo is a personal design-system feed.*
