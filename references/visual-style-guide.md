# VV Visual Style Guide

## Core Aesthetic

Visualize Value visuals are minimal, high-contrast compositions that distill an idea into a single image. They communicate through reduction — stripping everything until only the essential remains.

**Palette (inverted from original):**
- Background: `#FFFFFF` (white)
- Primary text/elements: `#111111` (near-black)
- Secondary/muted: `#666666`
- Accent (rare, used sparingly): `#999999`

The original VV visuals used black backgrounds with white text. This skill inverts that: white background, black text. Same restraint, opposite polarity.

## Typography System — Two Fonts, Two Jobs

This skill uses two typefaces with strict separation of roles. The font file for Carbon Bold is bundled in `assets/Carbon-Bold.ttf`.

### Carbon Bold (Uppercase) — Data & Structure
Carbon is the display/data font. It is ALWAYS set in uppercase. Use it for:
- **Chart titles and axis labels** — every text element in a chart (title, subtitle, axis labels, tick labels, legend text, data labels)
- **All numbers everywhere** — percentages, counts, dollar amounts, dates rendered as numbers, KPIs, scores
- **Table content** — all cell values including text and numbers inside table bodies
- **Table headers** — column and row headers

Carbon uppercase gives data a mechanical, engineered feel — like instrument readouts or a factory floor display. It signals precision.

### Space Grotesk — Body & Narrative
Space Grotesk is the reading font. Use it for:
- **Body text** — paragraphs, descriptions, captions, footnotes
- **Article content** — all long-form writing
- **Labels and annotations** that are narrative (not data)

### Font Stack Declarations

For HTML/CSS:
```css
/* Carbon — load from bundled asset */
@font-face {
  font-family: 'Carbon Bold';
  src: url('./assets/Carbon-Bold.ttf') format('truetype');
  font-weight: 700;
  font-style: normal;
}

/* Carbon usage — always uppercase */
.carbon {
  font-family: 'Carbon Bold', 'SF Mono', 'Fira Code', 'Courier New', monospace;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

/* Space Grotesk — load from Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;700&display=swap');

.body-text {
  font-family: 'Space Grotesk', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
```

For SVG:
```xml
<!-- Carbon for data/numbers — always uppercase -->
<text font-family="Carbon Bold, SF Mono, Courier New, monospace"
      text-transform="uppercase" letter-spacing="0.05em">12,450</text>

<!-- Space Grotesk for narrative -->
<text font-family="Space Grotesk, -apple-system, sans-serif">the idea goes here</text>
```

### Case Rules — No Exceptions
- Carbon text is ALWAYS uppercase. If it's set in Carbon, it's uppercase. No lowercase Carbon ever.
- Space Grotesk follows standard sentence case (lowercase preferred for the VV voice, uppercase only for single-word labels)
- Numbers in body text still use Carbon uppercase inline (wrap in a `<span class="carbon">` or equivalent)

### R — Restraint
- Maximum 2 font sizes per visual
- Maximum 2 colors (black + one gray)
- One idea per visual. If you need two visuals, make two visuals
- No gradients. No shadows. No rounded corners (except circles)
- No decorative elements. Every mark means something

### A — Alignment
- Center-aligned is the default for standalone statements
- Left-aligned for lists, progressions, or multi-line comparisons
- Grid: Use a simple 2-column or 3-column grid for comparisons
- Vertical centering: Text sits in the optical center (slightly above mathematical center)

### I — Image Treatment
- Geometric primitives only: circles, lines, rectangles, arrows
- When using shapes, they are diagrammatic — they represent concepts, not decoration
- Arrows show direction/flow. Lines show connection or separation
- Circles contain or highlight. Rectangles frame or group

### N — Negative Space
- Generous padding: at least 15-20% of canvas on each edge
- Space between elements is deliberate — it creates rhythm
- Emptiness communicates as much as the marks do
- When in doubt, add more space, not more elements

## Visual Archetypes

VV visuals fall into recognizable patterns:

### 1. The Statement
Single line of text, centered. The idea is the entire visual.
```
Canvas: white
Text: "complexity happens by default"
Position: dead center, large type
```

### 2. The Contrast
Two ideas separated by space or a dividing line.
```
Top half: "renting"
Bottom half: "owning"
Divider: thin horizontal line or just vertical space
Sometimes: strikethrough on the "wrong" option
```

### 3. The Progression
Numbered steps or stages flowing top-to-bottom or left-to-right.
```
1. Worthless
2. Cheap
3. Expensive
4. Not for sale
Arrow or line connecting stages
```

### 4. The Diagram
Simple geometric shapes illustrating a concept.
```
Circle A → Arrow → Circle B
Labels beneath each shape
Sometimes: one element highlighted (filled vs outline)
```

### 5. The Math
A formula or equation that makes an abstract idea concrete.
```
"+2 vs. ×2"
or
"input → [process] → output"
```

### 6. The Grid
2x2 or comparison matrix.
```
         | Low X  | High X
High Y   |  ...   |  ...
Low Y    |  ...   |  ...
```

## SVG Construction Rules

When generating VV-style visuals as SVG:

1. **Canvas**: 1200×1200px (square, social-media ready) or 1200×675px (16:9 for slides)
2. **Background**: `fill="#FFFFFF"` with optional `stroke="#EEEEEE"` border
3. **Body text**: `font-family="Space Grotesk, -apple-system, sans-serif"`
4. **Data/numbers/chart labels**: `font-family="Carbon Bold, SF Mono, Courier New, monospace"` with `text-transform="uppercase"`
5. **Text anchor**: `text-anchor="middle"` for centered statements
6. **No filters, no effects, no clip-paths** — pure shapes and text
7. **Line strokes**: 2-3px, `stroke="#111111"`, `stroke-linecap="round"`
8. **Arrow heads**: Simple triangles, not complex markers

## HTML Visual Construction

When generating as HTML (for richer typography):

```html
<style>
  @font-face {
    font-family: 'Carbon Bold';
    src: url('./assets/Carbon-Bold.ttf') format('truetype');
    font-weight: 700;
  }
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;700&display=swap');
</style>
<div style="
  width: 1200px;
  height: 1200px;
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 120px;
  font-family: 'Space Grotesk', -apple-system, sans-serif;
">
  <p style="
    font-size: 48px;
    font-weight: 700;
    color: #111;
    text-align: center;
    letter-spacing: -0.02em;
    line-height: 1.2;
  ">the idea goes here</p>
  <!-- For any numbers or data points, use Carbon: -->
  <span style="
    font-family: 'Carbon Bold', 'SF Mono', monospace;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  ">2,847</span>
</div>
```

## Charts

Every text element in a chart uses Carbon Bold uppercase — no exceptions. This includes: chart title, subtitle, axis titles, axis tick labels, legend entries, data labels, annotations, and tooltip text. Numbers in charts are also Carbon uppercase.

Body font (Space Grotesk) only appears in surrounding descriptions or captions outside the chart frame.

```css
/* Chart text — all Carbon uppercase */
.chart-title, .chart-subtitle,
.axis-label, .tick-label,
.legend-text, .data-label {
  font-family: 'Carbon Bold', 'SF Mono', monospace;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #111;
}
```

For SVG charts (e.g. with D3 or Recharts), set these on all `<text>` elements inside the chart:
```xml
<text font-family="Carbon Bold, SF Mono, monospace"
      style="text-transform: uppercase; letter-spacing: 0.05em;"
      fill="#111111">REVENUE</text>
```

## Tables

Tables follow a strict visual system: horizontal lines only, no vertical lines. Content uses Carbon uppercase.

### Table Rules
1. **All cell content** (headers and body) uses Carbon Bold uppercase — text and numbers alike
2. **Horizontal rules only**: a top border on the header, a border below the header separating it from the body, and a bottom border closing the table. Optionally, light horizontal rules between body rows
3. **No vertical lines** — ever. Column separation comes from generous horizontal padding
4. **Alignment**: Numbers right-aligned, text left-aligned
5. **Row striping**: None. Differentiation comes from whitespace and horizontal lines

### HTML Table Template
```html
<style>
  .vv-table {
    width: 100%;
    border-collapse: collapse;
    font-family: 'Carbon Bold', 'SF Mono', monospace;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    font-size: 14px;
    color: #111;
  }
  .vv-table thead {
    border-top: 2px solid #111;
    border-bottom: 2px solid #111;
  }
  .vv-table th {
    padding: 12px 16px;
    text-align: left;
    font-weight: 700;
  }
  .vv-table td {
    padding: 10px 16px;
    border-bottom: 1px solid #ddd;
  }
  .vv-table td.num {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }
  .vv-table tbody tr:last-child td {
    border-bottom: 2px solid #111;
  }
  /* NO vertical borders anywhere */
</style>

<table class="vv-table">
  <thead>
    <tr>
      <th>ITEM</th>
      <th>QUANTITY</th>
      <th>VALUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>PRODUCT A</td>
      <td class="num">1,240</td>
      <td class="num">$84,500</td>
    </tr>
    <tr>
      <td>PRODUCT B</td>
      <td class="num">862</td>
      <td class="num">$52,100</td>
    </tr>
  </tbody>
</table>
```

## What NOT to Do

- No stock imagery or photos
- No icons from icon libraries (draw your own simple shapes)
- No color for color's sake
- No borders or frames around the whole canvas
- No watermarks or logos (unless the visual IS about branding)
- No textures or patterns
- Never more than 30 words in a single visual
- Never use clip-art or emoji
