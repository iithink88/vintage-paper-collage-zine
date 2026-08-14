---
name: vintage-paper-collage-zine
description: Generate a vintage Chinese-Japanese editorial paper-collage print from a single photograph, using torn-paper windows, hand-drawn pencil botanical sketches, typewriter bilingual typography, and a vermilion seal stamp. Use when the user wants a 80s-90s Chinese travel-diary style poster, an old-book-collage art print, a hand-crafted journey page, or quotes a reference style featuring aged paper, torn openings, and pencil sketches emerging from a photograph.
---

# Vintage Paper-Collage Zine

Turn one user photo into one finished **2:3 vertical art print** that looks like a scanned page from a 1980s Chinese travel diary or a hand-crafted art book.

## What this skill produces

A single image that combines, on aged cream-yellow paper:

1. **One irregularly-torn paper window** revealing a restrained fragment of the source photo.
2. **Hand-drawn pencil botanical sketches** that grow around or from the window edge.
3. **Typewriter-style serif text** in Chinese and English — short title, microtext, optional short poetic lines.
4. **One small vermilion-red seal stamp** in a corner, with a few stray ink flecks.
5. **Aged paper texture** — fiber mottling, soft foxing spots, faint fold lines, scan noise.

The look is **quiet, literary, archival, nostalgic** — never commercial, never glossy, never modern UI.

## Visual Rules (verbatim)

These rules are non-negotiable. Each appears in the prompt.

### Canvas

- **Aspect:** vertical 2:3 (e.g. `1080x1620`).
- **Background:** aged cream-yellow paper `#F0E4C8` to `#E8D9B0`, full-frame, no border, no mockup, no shadows.
- **Texture:** subtle paper fiber, soft mottling, faint age stains near corners, occasional small foxing spots. Very faint horizontal/vertical fold lines.
- **View:** flat orthographic, like a scanned book page.

### Torn Paper Window

- **One** irregularly-torn opening in the paper.
- **Edges:** organic, ragged, with thin paper fibers visible along the perimeter — *exactly* like a real paper tear.
- **Position:** typically right-center, upper-right, or lower-right. Never edge-hugging.
- **Size:** about 30% of canvas width × 36% of canvas height.
- **Content:** a CLOSE-UP crop of the source photo. Pick **one** restrained fragment — never the whole image. Common choices: distant water + boat + horizon; dense leaves; building corner. Exclude busy foreground.
- **Treatment:** soft slightly desaturated colors, faint halftone dot grain, blends with surrounding paper.

### Hand-Drawn Pencil Sketches

- **Location:** opposite side of the canvas from the photo window (typical: left side, lower-left).
- **Subject:** botanical line-drawing of plants growing around the window — lotus stems, leaves, buds, branches, etc. — matching the source photo's subject.
- **Style:** single-weight graphite lines, light and confident, low contrast, subtle hatching only where needed. Not filled, not shaded, not illustrated.
- **Connection:** some stems should appear to grow from below the torn window, creating a visual bridge between sketch and photograph.
- **Coverage:** about 18% of canvas.

### Typography

- **Font:** small typewriter / serif, dark warm gray `#3A342C`.
- **Layout (typical):**
  - Top-left corner: large English title ALL CAPS on line 1, slightly smaller Chinese translation on line 2.
  - Below photo window (mid-right): two short bilingual poetic lines, each EN then ZH.
  - Bottom-left: tiny microtext `"<location> · <time>"`.
- **Length:** keep total text short. Image models distort long text.
- **No:** modern sans-serif, logos, watermarks, decorative borders.

### Red Seal Stamp

- **Position:** top-right corner, opposite the title.
- **Size:** about 3% of canvas.
- **Color:** vermilion `#B83A2C`.
- **Content:** one Chinese character as negative space (white inside the red square). Pick a character related to the subject.
- **Texture:** slight roughness at edges like a real ink stamp. A few tiny scattered red ink flecks nearby.

### Color Palette

| Element | Color | Coverage |
|---|---|---|
| Cream-yellow paper | `#F0E4C8`–`#E8D9B0` | ~70% |
| Photo fragment | muted blue, gray, soft green | ~22% |
| Vermilion seal + ink flecks | `#B83A2C` | ~2% |
| Pencil graphite lines | warm gray | ~3% |
| Text | dark warm gray `#3A342C` | ~3% |

**No other high-chroma colors.**

### Mood

Quiet, nostalgic, literary, personal, like a page from a 1980s Chinese travel diary or 1980s Japanese indie art book. All elements aged together, halftone grain in photo fragment.

### Hard Avoids

- Bright digital backgrounds.
- Sharp clean edges on the photo fragment (must be torn).
- Modern sans-serif fonts.
- Multiple competing colors.
- Cartoon illustration, 3D effects, shadows, paper gradients.
- Logos, watermarks, decorative borders.
- Full-bleed scene, full sky, full horizon.
- Dense flowers / foreground leaves in the photo fragment.

## Workflow

1. **Inspect the source photo.**
   - Identify: subject, environment, mood, narrative core.
   - Pick ONE fragment to keep in the window (e.g. distant water + boat, dense leaves, building corner). Exclude the rest.

2. **Pick variation recipe.**
   - **Window position:** right-center (default), upper-right, lower-right, lower-left.
   - **Sketch style:** botanical-stems (default), tree-branches, ink-splash, simple-architecture.
   - **Title source:** user-supplied, or invent a short 2-4 character Chinese title plus an English translation.
   - **Seal character:** chosen by the model based on subject (e.g. 泽 for water, 山 for mountain, 城 for city).

3. **Optional reference images.**
   - If the user provides style templates (e.g. 5 reference images of the same aesthetic), pick **2** that best match the visual language — one strong torn-edge example, one strong pencil-sketch example.
   - **ImageGen input limit is 3 images.** Use 1 source photo + up to 2 reference templates. Skip references if the user didn't supply any.

4. **Compile the prompt** using the standard prompt template in `references/prompt-template.md`. Fill in:
   - Subject fragment.
   - Window position & size.
   - Sketch subject.
   - Title text (Chinese + English).
   - Optional short poetic lines.
   - Microtext location · time.
   - Seal character.
   - 1-2 reference template paths (if any).

5. **Generate the image.**
   - Call `ImageGen` with `image=[source, ...refs]`, `quality="high"`, `size="1080x1620"`.
   - `input_fidelity` 0.30–0.40: high enough to keep the source photo's fragment recognizable, low enough to let the prompt govern style.
   - If first result misses the torn edge or seal, regenerate once with stronger wording.

6. **Return image + prompt + table** in the Standard Output Format below.

## Input Reference Images — Limit & Strategy

`ImageGen` accepts **at most 3** images. One slot is the source photo. Two slots remain for style templates.

**When user supplies 5 templates:** pick the 2 that best establish the visual language — usually one with the strongest torn-paper edge, one with the strongest pencil-sketch overlay. List the rest in the table as "additional style references (un-transmitted)" so the user knows what was considered.

**When user supplies 0 templates:** generate from prompt alone. The skill's prompt template is self-contained.

## Title & Seal Conventions

If the user does not specify text:

- **Title:** 2–4 Chinese characters, lowercase English translation. Examples:
  - `水一方` / *ACROSS THE WATER* (water + distant boat)
  - `泊` / *MOORED* (stopped boat)
  - `满池` / *STILL POND* (densely covered lotus)
  - `远山` / *DISTANT HILLS* (mountain horizon)
- **Poetic lines (optional):** 2 short lines, each with English then Chinese. Keep under 8 words / 8 characters each.
- **Microtext:** `<location> · <time>` separated by a middot. Time can be a date or a season.
- **Seal character:** one Chinese character that captures the subject. Common: 泽/水/山/城/树/舟/莲/故/忆/夏/秋/冬.

## Variation Engine

Pick one option from each axis. Rotate so outputs do not look identical.

### Window Position

- **right-center** (default) — classic; window opposite the left-bottom sketch
- **upper-right** — peeks above the title
- **lower-right** — sits below the seal
- **left-center** — mirror composition, sketch on the right
- **lower-left** — small window punched low

### Sketch Style

- **botanical-stems** (default) — stems, leaves, buds from photo subject
- **tree-branches** — single bare branch with a few leaves
- **mountain-ink-line** — light contour line of mountain silhouette
- **building-edge** — one corner of a roof or wall
- **single-anchor** — one bold object (a single leaf, a closed bud, a small stone)

### Title Tone

- **classical-poetic** — 诗经/古诗引子的标题 (`水一方`, `蒹葭`, `泊`)
- **concrete-observation** — 直白观察 (`一只船`, `花开时`)
- **mood-word** — 一个情绪字 (`静`, `忆`, `夏`)
- **english-only** — 全英文标题搭配中文微文

### Texture Intensity

- **mild** (default) — light mottling, mild foxing, faint fold lines
- **heavy** — more stains, deeper yellowing, very visible fold lines
- **fresh-but-aged** — almost white-yellow with only subtle fiber texture

## Standard Prompt Template

The full prompt template is in `references/prompt-template.md`. Use it as the starting point. Each field is a `{{placeholder}}` to fill.

## Output Format

````markdown
**生成图**

![vintage paper-collage zine print](<absolute-path>)

**最终 Prompt**

```text
<the exact prompt used for image generation>
```

**说明**

| 项目 | 内容 |
|------|------|
| **来源** | `<source photo path>` |
| **风格模板** | `<2 reference template paths transmitted>`, `<N additional style references un-transmitted>` |
| **版式** | `<window-position> / <sketch-style> / <title-tone> / <texture>` |
| **标题** | `<Chinese title>` / *<English title>* |
| **文字** | `<EN line 1>` / `<ZH line 1>` / `<EN line 2>` / `<ZH line 2>` |
| **微文** | `<location> · <time>` |
| **印章** | `<Chinese character>` |
| **局部提取** | `<source photo fragment kept (e.g. distant water + boat + horizon)>` |
| **情绪** | `<one short mood phrase>` |
````

## Quality Gate

Before returning, verify:

- [ ] Aspect is 2:3 vertical.
- [ ] Background is cream-yellow aged paper, not white or modern.
- [ ] Photo fragment has a true torn ragged edge with paper fibers.
- [ ] Pencil sketches are single-weight line drawings, not filled.
- [ ] Text is short, bilingual, typewriter-style.
- [ ] Red seal is in a corner, opposite the title.
- [ ] Color palette has only the cream + photo + vermilion + graphite.
- [ ] No modern UI, logo, watermark, border, 3D, shadow, or cartoon.
- [ ] Photo fragment does NOT include the full sky or full horizon.
- [ ] Image was actually generated (not just prompt text).

## Example Requests

- "用这个 skill 把我这张荷花照片做成老旅行日记风格"
- "照 5 张模板的样子，把这张街景做成撕纸海报"
- "做一张致敬 80 年代中国旅行手账的复古海报"
- "vintage-paper-collage-zine: 把这张湖景做成老旧书页的感觉"
