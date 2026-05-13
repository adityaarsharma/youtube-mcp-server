---
name: youtube-thumbnail
description: >
  Generates 3 A/B thumbnail briefs with full design specs, title-thumbnail synergy check,
  and CTR improvement recommendations. Brand-aware: @posimyth uses product brand colors
  from Golden Circle; @adityaarsharma uses face+code formula. Based on Focus Digital
  CTR benchmarks and vidIQ data.
---

# /youtube thumbnail

## Brand Detection — Run First

Before generating any briefs, identify the brand:

| Signal | Brand | Rules to apply |
|--------|-------|---------------|
| @posimyth / TPAE / Nexter / WDesignKit / UiChemy | **POSIMYTH** | Product-first, GC brand colors, no face required |
| @adityaarsharma / Pickle / Jyotisha / YouTube MCP / RunCloud | **Personal** | Face-first, code/terminal as product, developer niche |

Pass `--brand posimyth` or `--brand personal` to skip detection.

---

## POSIMYTH Brand — @posimyth

### Research Foundation
- **Focus Digital, Dec 2025**: Tutorial channel avg CTR 4–8%. Dark backgrounds convert higher
- **vidIQ**: Face in thumbnail → +38% CTR avg (less critical for product-demo channels)
- **Channel benchmark**: Organic Video → conversion = **16.5%** (GA4, Feb–May 2026)
- **Top video pattern**: Dark bg + result showcase + minimal text + product UI visible

### Brand Colors Per Product (from Golden Circle PRODUCT-QUICKREF.md)
Always read `context/PRODUCT-QUICKREF.md` for the current source of truth. Quick reference:

| Product | Background | Accent | Logo rule |
|---------|-----------|--------|-----------|
| TPAE | Blue-purple gradient `#6d68fe`→`#b446ff` | White / yellow | "+" mark or Plus wordmark |
| NexterWP | Dark navy / teal | Teal/green | Nexter wordmark, legible |
| WDesignKit | Hot pink/magenta `#E91E8C` | White | Square "W" logo bottom-right — MANDATORY |
| UiChemy | Figma purple `#A259FF` left → WP blue right | White | Figma "F" + WP logo as ecosystem icons |

### Winning Formula (POSIMYTH)

| Element | Winning Pattern | What to Avoid |
|---------|----------------|---------------|
| Background | Dark + product brand color zone | White, light gray, generic |
| Main visual | Finished result in ACTIVE state | Elementor backend, building state |
| Text | 3–5 words MAX, large, high contrast | 6+ words, sentence case |
| Text color | White or brand accent (yellow/magenta) | Gray, muted colors |
| Face | Optional — product UI often outperforms face here | Neutral expression with no product shown |
| Arrows | One directional arrow max | Multiple arrows pointing everywhere |

### POSIMYTH — 3 A/B Variants

**VARIANT A — Result Showcase (recommended default)**
```
CONCEPT: Show the finished output in its most impressive state
BACKGROUND: Product brand color zone (left 40%) + dark (right 60%)
MAIN VISUAL: The final result — widget/page in active/open state, not building state
TEXT OVERLAY: 3-5 power words describing the outcome
TEXT POSITION: Left third, vertically centered
FONT: Montserrat ExtraBold or Bebas Neue, 90–120px
ACCENT COLOR: Product brand color for 1 key word or underline
LOGO: Product logo bottom-right, 80–100px
FACE: Optional — if used, left 30% with clear emotion
```

**VARIANT B — Before/After Split**
```
CONCEPT: Left = problem/plain/Elementor, Right = solution/polished/Gutenberg
BACKGROUND: Dark left panel, slightly lighter right panel
DIVIDER: Vertical line, product brand color
LEFT VISUAL: Plain/default/competitor state
RIGHT VISUAL: The polished POSIMYTH output
TEXT: "BEFORE"/"AFTER" labels small above panels + 3-word headline at top
ECOSYSTEM ICONS: Relevant platform icons (Elementor E, Gutenberg W, Figma F)
```

**VARIANT C — Bold Claim / Power Word**
```
CONCEPT: The claim drives the click — visual supports
BACKGROUND: Dark + brand color accent strip
MAIN VISUAL: Product result as secondary element (40% of frame)
TEXT (large, center): "FREE" / "1 CLICK" / "NO CODE" / "REPLACED 50+"
TEXT (smaller): The specific outcome
LOGO: Product logo clearly visible
Note: Use when the method or scale IS the hook (free, 1-click, installs)
```

---

## Personal Brand — @adityaarsharma

### Research Foundation
- Developer/maker audience: responds to competence signals and real work shown
- Face + code outperforms code-only for personal brand recall
- "How I..." hooks outperform "How to..." in this niche
- Open source / free / GitHub stars are high-CTR signals for this audience

### Brand Colors Per Product

| Product | Background | Accent | Face? |
|---------|-----------|--------|-------|
| Pickle | Dark (`#0d0d0d`) | Claude purple `#7B61FF` | Yes — recommended |
| Jyotisha | Deep dark `#1a0a2e` | Gold `#D4AF37` | Yes — spiritual credibility |
| YouTube MCP | Dark (`#111`) | YouTube red `#FF0000` | Yes — with terminal |
| RunCloud MCP | Dark server aesthetic | Teal/green `#00B894` | Optional |

### Winning Formula (Personal Brand)

| Element | Winning Pattern | What to Avoid |
|---------|----------------|---------------|
| Background | Dark — almost black | White, stock photo backgrounds |
| Main visual | Terminal output / Claude Code interface / build result | Generic laptop stock photo |
| Text | 3–5 words, first-person energy ("I BUILT", "IN 20 MIN") | Passive/generic phrasing |
| Face | Left 35% of frame, clear expression (curiosity, "look at this") | No face at all (missed brand recall) |
| Accent | Product-matched color for 1 power word | Too many colors |

### Personal Brand — 3 A/B Variants

**VARIANT A — Face + Result (recommended default)**
```
CONCEPT: Aditya's face reacts to / points at the result
BACKGROUND: Near-black with product accent color strip on right
LEFT (35%): Face — clear expression, looking toward result
RIGHT (55%): Terminal output, Claude Code interface, or product demo screenshot
TEXT: 3–5 word hook at top or bottom — bold, white, product accent highlight on 1 word
FONT: Montserrat ExtraBold, 80–100px
FACE RULE: Genuine expression — curiosity, "you won't believe this", "here it is"
```

**VARIANT B — Code/Terminal Showcase**
```
CONCEPT: The build result is the hero — output speaks for itself
BACKGROUND: Dark with subtle grid or terminal aesthetic
MAIN VISUAL: Claude Code terminal output or product interface — full width
TEXT OVERLAY (left strip or top): "I BUILT THIS" / "IN 20 MIN" / "WITH CLAUDE"
SMALL FACE: Bottom-left corner, 100–120px — credit signal without dominating
ACCENT: Product color on key metric or output text
```

**VARIANT C — Claim + Social Proof**
```
CONCEPT: Bold open-source/free claim + proof (GitHub stars, npm installs, downloads)
BACKGROUND: Dark
TEXT (large): "FREE" / "OPEN SOURCE" / "1,000 STARS"
TEXT (smaller): What it does in 5 words
FACE: Optional — small, bottom corner
ACCENT: GitHub green or npm red for social proof element
Note: Use for launch announcements or milestone videos
```

---

## Topic Clarity Check (Both Brands)

Run this for every brief generated — brand-agnostic:

| Check | Pass / Fail |
|-------|------------|
| Thumbnail readable without the title | |
| Tool/product doing the action is identifiable | |
| Outcome scope is clear (1 page? full site? 20 min build?) | |
| Pain signal or urgency present | |
| UI content inside mockups matches the video topic | |
| Readable at 120px width (mobile) | |

**Rule**: If the first two checks fail → revise the variant before delivering. A thumbnail that needs the title to explain it is a weak thumbnail.

## Output Format

```
## THUMBNAIL BRIEFS FOR: [Video Title]
**Brand:** @posimyth / @adityaarsharma
**Product:** [product name]

### 🎨 VARIANT A — [Name]
Concept: [1 sentence — what the viewer sees and feels]
Background: [color code or description]
Main visual: [what to show, specific state — not vague]
Text overlay: [exact words, max 5]
Text position: [placement]
Font: Montserrat ExtraBold / Bebas Neue, [size]px
Accent color: [hex]
Face: Yes (left 35%, [emotion]) / No
Logo: [product logo, position, size]
Ecosystem icons: [Elementor / Gutenberg / Figma / GitHub — if relevant]
Design notes: [any specific instructions]

### 🎨 VARIANT B — [Name]
[Same format]

### 🎨 VARIANT C — [Name]
[Same format]

---
## TOPIC CLARITY CHECK
[Table results — flag any fails]

## RECOMMENDED TEST ORDER
Start with Variant A. If CTR <4% after 500 impressions, switch to Variant B.

## TITLE-THUMBNAIL SYNERGY
[Any mismatch — does thumbnail + title complement or repeat each other?]
```
