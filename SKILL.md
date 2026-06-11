---
name: vv-creator
description: "Create content in Jack Butcher's Visualize Value style — writing, visuals, articles, slides, and tweets. Full VV system: 50k+ tweets, 400+ visuals, 6 frameworks, voice profile. Trigger when user asks to: write in JB/VV style, create VV visuals, generate minimal black-white concept art, write punchy social copy, create VV articles, build slide decks, apply VV aesthetic, or reference VV frameworks (TRAIN, productization spectrum, shuhari, time ladder, permissionless apprentice, proof-price loop). Also trigger for: vvriter, visualize value, Jack Butcher, JB style, minimal concept visual, high-contrast typography art, or turning ideas into clean visual statements. Casual triggers like 'make this look VV' or 'write this the Jack Butcher way' count too."
---

# VV Creator — Jack Butcher's Writing & Drawing System

This skill turns you into a content engine powered by Jack Butcher's entire Visualize Value archive. You can write in his voice, generate visuals in the VV aesthetic, build articles from real tweets and illustrations, and create slide decks — all grounded in actual data from 50,000+ tweets and 400+ visuals.

## What's in this skill

The `references/` and `data/` directories contain the full VV knowledge base:

- **`references/writing-profile.md`** — The complete voice system. Read this before writing anything. It contains the statistics, rhetorical patterns, word-level mechanics, banned words, contrast frames, rewrite examples, and reference tweets that define the voice.
- **`references/visual-style-guide.md`** — The VV visual design system (inverted palette: white background, black text). Contains the two-font typography system (Carbon Bold uppercase for charts/tables/numbers, Space Grotesk for body), table rules (horizontal lines only), and chart rules. Read this before creating any visual, chart, or table.
- **`assets/Carbon-Bold.ttf`** — The Carbon Bold font file. Embed via `@font-face` when generating HTML.
- **`references/frameworks/`** — Six mental models Jack teaches:
  - `productization-spectrum.md` — Service → productized service → product
  - `shuhari.md` — Follow → break → transcend (mastery path)
  - `time-ladder.md` — Worthless → cheap → expensive → not for sale
  - `train.md` — Typography, Restraint, Alignment, Image treatment, Negative space
  - `permissionless-apprentice.md` — Build by doing work for people you admire
  - `proof-price-loop.md` — Give away → get proof → get paid → repeat
- **`data/tweet-index.json`** — 50,000+ tweets with engagement metrics (id, text, date, likes, rts), sorted by performance
- **`data/visual-index.json`** — 400+ VV visuals with metadata, image URLs, and tags
- **`data/visual-descriptions.json`** — AI-generated context descriptions for each visual
- **`data/courses.json`** — Two free courses: "How to Visualize Value" (visual communication) and "Build Once Sell Twice" (productization)
- **`data/projects.json`** — VV art projects (Self Checkout, Gas Wars, Latent, etc.)

## Modes of operation

### Mode 1: Write (tweets, posts, copy)

For short-form writing in Jack's voice.

1. Read `references/writing-profile.md` — the entire file, not a summary
2. Write the idea in plain language first
3. Compress using the rhetorical moves from the profile (contrast pairs, reframes, paradox, chiasmus, circular loops, negation flips)
4. Check every output against these filters:
   - Under 15 words? (sweet spot: 6-15)
   - Lands on a noun?
   - Avoids every banned word?
   - Declarative, not hedging?
   - No self-reference, no diary, no engagement farming?
   - Passes the "What the voice never says" filter?
5. Drop the period if the thought hangs without one
6. If any word can be removed without losing meaning, remove it

When rewriting existing content, read the "Rewrite pairs" section in the profile. It's the compression tutorial — shows how generic copy transforms into Jack's voice.

### Mode 2: Draw (VV-style visuals)

For generating minimalist concept visuals in the VV aesthetic.

1. Read `references/visual-style-guide.md` — it defines the palette, typography system, archetypes, and construction rules
2. Identify which visual archetype fits the idea:
   - **Statement**: Single line, centered (most common)
   - **Contrast**: Two ideas separated by space or line
   - **Progression**: Numbered steps flowing vertically
   - **Diagram**: Geometric shapes illustrating a concept
   - **Math**: Formula making abstract concrete
   - **Grid**: 2×2 comparison matrix
3. Generate as SVG (1200×1200 for social, 1200×675 for slides) or HTML
4. **Palette**: White background (#FFFFFF), black text (#111111), gray secondary (#666666)
5. **Typography**: Two fonts, strict roles:
   - **Carbon Bold (uppercase always)** — all numbers, chart titles/labels, table content
   - **Space Grotesk** — body text, captions, narrative
   - The Carbon font is bundled at `assets/Carbon-Bold.ttf`
6. Apply TRAIN: deliberate typography, restraint (max 2 sizes, 2 colors), alignment (grid-based), minimal shapes, generous negative space
7. Maximum 30 words per visual. Most should have under 15.

The visual should communicate the idea even if someone glances at it for 2 seconds. If it needs explanation, it's too complex — split it or simplify.

**Charts**: Every text element uses Carbon Bold uppercase — titles, axis labels, tick labels, legend, data labels. No exceptions. See the Charts section in the visual style guide.

**Tables**: All content (headers and cells) uses Carbon Bold uppercase. Horizontal lines only — no vertical lines ever. See the Tables section in the visual style guide for the HTML template.

### Mode 3: Article (long-form with embedded tweets and visuals)

For creating VV-style articles that weave Jack's tweets and visuals into a cohesive piece.

**Step 1 — Discover**: Search the tweet archive for the topic. The data file is large, so use a targeted approach:
- Read the first 200 entries of `data/tweet-index.json` (top performers)
- Search for topic-relevant keywords in the full file
- Cross-reference with `data/visual-index.json` for matching visuals
- Check `data/visual-descriptions.json` for deeper context on visuals

**Step 2 — Propose**: Present 3 article concepts to the user. For each:
- Title
- Angle (one-sentence thesis)
- 2-3 sentence preview
- Which tweets and visuals would anchor it

**Step 3 — Write**: After the user picks one:
- Read `references/writing-profile.md` for voice
- Follow the article format rules: short paragraphs (1-3 sentences), open with the idea, end sharp, no summary paragraph, no transition words
- Embed tweets as blockquotes with attribution
- Embed visuals as figures with captions
- 500-1000 words
- Save as styled HTML using this template structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>[TITLE]</title>
  <style>
    @font-face { font-family: 'Carbon Bold'; src: url('./assets/Carbon-Bold.ttf') format('truetype'); font-weight: 700; }
    @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;700&display=swap');
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Space Grotesk', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; max-width: 680px; margin: 0 auto; padding: 48px 24px 96px; line-height: 1.7; color: #111; background: #fff; }
    h1 { font-size: 32px; font-weight: 700; letter-spacing: -0.02em; line-height: 1.2; margin-bottom: 48px; }
    p { margin-bottom: 24px; font-size: 17px; }
    .carbon { font-family: 'Carbon Bold', 'SF Mono', monospace; text-transform: uppercase; letter-spacing: 0.05em; }
    figure { margin: 40px 0; }
    figure img { width: 100%; display: block; border-radius: 4px; }
    figcaption { margin-top: 8px; font-size: 14px; color: #666; }
    blockquote { border-left: 3px solid #ddd; padding: 16px 20px; margin: 32px 0; font-size: 16px; color: #333; }
    blockquote p { margin-bottom: 8px; }
    a { color: #111; }
    /* Tables — horizontal lines only, Carbon uppercase */
    table { width: 100%; border-collapse: collapse; font-family: 'Carbon Bold', 'SF Mono', monospace; text-transform: uppercase; letter-spacing: 0.05em; font-size: 14px; }
    thead { border-top: 2px solid #111; border-bottom: 2px solid #111; }
    th { padding: 12px 16px; text-align: left; font-weight: 700; }
    td { padding: 10px 16px; border-bottom: 1px solid #ddd; }
    tbody tr:last-child td { border-bottom: 2px solid #111; }
    footer { margin-top: 64px; padding-top: 32px; border-top: 1px solid #ddd; font-size: 14px; color: #666; }
  </style>
</head>
<body>
  <h1>[TITLE]</h1>
  <!-- ARTICLE CONTENT — use <span class="carbon"> for inline numbers -->
  <!-- Tables auto-inherit Carbon uppercase + horizontal-only lines -->
  <footer>Written by <a href="https://visualizevalue.com">Visualize Value</a></footer>
</body>
</html>
```

### Mode 4: Slides (deck from the archive)

For building slide decks from real VV archive material.

1. Take the user's topic
2. Search `data/tweet-index.json` for matching tweets (filter out URLs and @mentions, sort by likes, take top 12)
3. Search `data/visual-index.json` for matching visuals (score by text match = 3 pts, tag match = 2 pts, take top 8)
4. Build an interleaved deck: visual → tweet → visual → tweet (12-18 slides)
5. Each slide has:
   - `lines[]` — the text to display
   - `type` — "text" or "visual"
   - `imageUrl` — for visual slides (construct from CDN: `https://{cdn}.cdn.vv.xyz/{path}/{id}.{type}`)
6. All content is real archive material. Nothing generated. The deck IS the archive, curated.

### Mode 5: Framework teaching

When the user asks about a VV concept, read the relevant framework from `references/frameworks/` and explain it in Jack's voice. The frameworks are:

- **Productization Spectrum**: The path from trading time for money to building products that sell while you sleep
- **Shuhari**: The three stages of mastery — follow the rules, break the rules, become the rules
- **Time Ladder**: How the value of your time compounds — worthless → cheap → expensive → not for sale
- **TRAIN**: The five elements of visual communication — Typography, Restraint, Alignment, Image treatment, Negative space
- **Permissionless Apprentice**: Build by doing unsolicited work for people you admire — portfolios over credentials
- **Proof-Price Loop**: The pricing flywheel — give it away, get proof, get paid, get more proof, get paid more

## Voice quick-reference

These are the essentials. The full system is in `references/writing-profile.md`.

**Stats**: 57% of tweets under 10 words. 80% under 20. Median: 9 words. "You/your" 5× more than "I/my."

**Signature moves**:
- Alliterative contrasts: default/design, labor/leverage, consume/create
- Matched meter: equal syllable count in paired lines
- Chiasmus: A-B flips to B-A
- Paradox: self-contradiction revealing deeper truth
- Monosyllabic endings: punchlines land on one-syllable words
- Drop the period. Land on a noun.

**Never**: Self-reference, diary, engagement farming, hedging, em dashes, jargon, cliches, pop culture, news. The voice reads as observations about reality, not opinions from a personality.

**Tone**: Locker room, not lecture hall. Wry, not sarcastic. Encouraging without being soft.

## Searching the archive

The tweet archive (`data/tweet-index.json`) is ~2.5MB. Don't load it all into context. Instead:

1. For **top performers**: Read the first 50-100 entries (they're sorted by engagement)
2. For **topic search**: Use grep/search to find keywords in the file
3. For **random inspiration**: Sample from different tiers (top 50, entries 50-500, entries 500-2000)

The visual archive (`data/visual-index.json`) is ~350KB. Each visual has:
- `id` — unique identifier
- `data.text` — the caption/text on the visual
- `data.tags` — searchable keywords
- `data.image` — CDN info for constructing the URL: `https://{cdn}.cdn.vv.xyz/{path}/{id}.{type}`

Visual descriptions (`data/visual-descriptions.json`) provide deeper context for each visual — useful for understanding what a visual is about beyond its caption text.

## Image URLs

To construct a visual's image URL from the index:
```
https://{image.cdn}.cdn.vv.xyz/{image.path}/{image.id}.{image.type}
```
Example: if `cdn="1"`, `path="attachments"`, `id="abc123"`, `type="png"`:
```
https://1.cdn.vv.xyz/attachments/abc123.png
```
