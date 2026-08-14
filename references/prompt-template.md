# Vintage Paper-Collage Zine — Prompt Template

This is the working prompt template. Copy it, fill in `{{placeholders}}`, and pass to `ImageGen`.

## Full Template

```text
A tall vertical 2:3 artistic paper-collage print in vintage Chinese-Japanese editorial zine style, like a scanned page from an old hand-crafted book. {{style_reference_note}}

CANVAS: aged warm cream-yellow paper background (#F0E4C8 to #E8D9B0), full-frame, no border, no mockup, no digital UI feel. Subtle paper fiber texture, soft mottling, faint age stains near corners, occasional small foxing spots. Flat orthographic view. Very faint horizontal and vertical fold lines like an old book page.

TORN PAPER WINDOW: a single irregularly-torn opening in the {{window_position}} area of the canvas. The torn edges are organic, ragged, with thin paper fibers visible along the perimeter, exactly like a real paper tear. Through this window reveal a CLOSE-UP photographic fragment from the source image: ONLY {{photo_fragment_description}} — NOT {{photo_exclusions}}. The photo fragment has soft slightly desaturated colors with a faint halftone dot grain, blending harmoniously with the surrounding paper. Window takes about {{window_width_pct}}% of canvas width and {{window_height_pct}}% of height.

HAND-DRAWN PENCIL SKETCHES: in the {{sketch_location}} area, delicate pencil line drawings of {{sketch_subject}}, in the spirit of botanical illustration. Single-weight graphite lines, light and confident, with subtle hatching only where needed. Some stems appear to grow from below the torn window, connecting the sketch layer with the photographic layer. Sketch area covers about 18% of canvas.

TYPOGRAPHY (small typewriter/serif font, dark warm gray #3A342C):
{{typography_block}}

RED SEAL STAMP: a small square vermilion-red seal (#B83A2C) in the {{seal_position}} corner, about 3% of canvas. Contains the Chinese character "{{seal_character}}" in cream/white inside (like the character is the negative space of the seal). Slight roughness at edges like a real ink stamp. A few tiny scattered red ink flecks nearby like stamp imperfections.

MOOD: quiet, nostalgic, literary, like a personal page from an old Chinese travel diary or 1980s art book. Some halftone grain in photo fragment, all elements aged together.

COLOR PALETTE:
- Cream-yellow paper ~70%
- Photo fragment (muted blue, gray, soft green) ~22%
- Vermilion red seal and ink flecks ~2%
- Pencil graphite lines ~3%
- Text in dark warm gray ~3%
No other high-chroma colors.

AVOID: bright digital backgrounds, sharp clean edges on photo fragment (MUST be torn), modern sans-serif fonts, multiple competing colors, cartoon illustration, 3D effects, shadows, gradients on paper, logos, watermarks, decorative borders, the full sky, dense flowers, foreground leaves in the photo fragment.
```

## Placeholder Reference

| Placeholder | Example Value |
|---|---|
| `{{style_reference_note}}` | "The reference images show the EXACT aesthetic language to follow: aged cream-yellow paper, a single irregularly-torn opening revealing a photograph, delicate pencil line-drawing sketches of plants growing around the window, typewriter-style serif Chinese-English bilingual text, and a small vermilion-red seal stamp." (Use only if you are passing reference templates.) |
| `{{window_position}}` | right-center / upper-right / lower-right / left-center / lower-left |
| `{{photo_fragment_description}}` | "the distant calm lake water surface, the small wooden boat with a single figure sitting quietly, and a sliver of sky reflection" |
| `{{photo_exclusions}}` | "the foreground lotus leaves, NOT the pink flowers, NOT the full sky, NOT the horizon" |
| `{{window_width_pct}}` | 30 |
| `{{window_height_pct}}` | 36 |
| `{{sketch_location}}` | left side and lower-left |
| `{{sketch_subject}}` | "lotus stems, several rounded leaves, and one closed lotus bud" |
| `{{typography_block}}` | see Typography Block below |
| `{{seal_position}}` | upper-right |
| `{{seal_character}}` | 泽 / 水 / 山 / 城 / 树 / 舟 / 莲 / 故 / 忆 / 夏 / 秋 / 冬 |

## Typography Block

Choose one of these forms and embed directly in the prompt.

### Form A — Top-left title + mid-right poetic lines (default)

```
Top-left corner:
Line 1: "{{title_en}}"
Line 2 (slightly smaller Chinese): "{{title_zh}}"
Mid-right area below the torn window, two short poetic lines stacked:
"{{poetic_en_1}}"
"{{poetic_zh_1}}"
"{{poetic_en_2}}"
"{{poetic_zh_2}}"
Bottom-left corner: tiny microtext "{{location}} · {{time}}"
```

### Form B — Centered title + scattered microtext

```
Center-left area: "{{title_en}}" in small serif, with "{{title_zh}}" stacked beneath in slightly smaller weight.
Bottom-right: tiny microtext "{{location}} · {{time}}".
Optional one short line above the photo fragment: "{{poetic_en_1}} / {{poetic_zh_1}}".
```

### Form C — Mood-word only (no English title)

```
Top-left: a single Chinese character "{{title_zh}}" in small elegant serif, deep warm gray.
Below it: one short italic English phrase "{{poetic_en_1}}".
Bottom-left microtext: "{{location}} · {{time}}".
```

## Concrete Example (filled)

```text
A tall vertical 2:3 artistic paper-collage print in vintage Chinese-Japanese editorial zine style, like a scanned page from an old hand-crafted book. The reference images show the EXACT aesthetic language to follow: aged cream-yellow paper, a single irregularly-torn opening revealing a photograph, delicate pencil line-drawing sketches of plants growing around the window, typewriter-style serif Chinese-English bilingual text, and a small vermilion-red seal stamp.

CANVAS: aged warm cream-yellow paper background (#F0E4C8 to #E8D9B0), full-frame, no border, no mockup, no digital UI feel. Subtle paper fiber texture, soft mottling, faint age stains near corners, occasional small foxing spots. Flat orthographic view. Very faint horizontal and vertical fold lines like an old book page.

TORN PAPER WINDOW: a single irregularly-torn opening in the right-center area of the canvas. The torn edges are organic, ragged, with thin paper fibers visible along the perimeter, exactly like a real paper tear. Through this window reveal a CLOSE-UP photographic fragment from the source image: ONLY the distant calm lake water surface, the small wooden boat with a single figure sitting quietly, and a sliver of sky reflection — NOT the foreground lotus leaves, NOT the pink lotus flowers, NOT the wide sky, NOT the full horizon. The photo fragment has soft slightly desaturated colors with a faint halftone dot grain, blending harmoniously with the surrounding paper. Window takes about 30% of canvas width and 36% of height.

HAND-DRAWN PENCIL SKETCHES: in the left side and lower-left area, delicate pencil line drawings of lotus stems, several rounded leaves, and one closed lotus bud, in the spirit of botanical illustration. Single-weight graphite lines, light and confident, with subtle hatching only where needed. Some stems appear to grow from below the torn window, connecting the sketch layer with the photographic layer. Sketch area covers about 18% of canvas.

TYPOGRAPHY (small typewriter/serif font, dark warm gray #3A342C):
Top-left corner:
Line 1: "ACROSS THE WATER"
Line 2 (slightly smaller Chinese): "水 一 方"
Mid-right area below the torn window, two short poetic lines stacked:
"Flowers open in the water."
"花在水中开。"
"The boat moves in the distance."
"船在远处走。"
Bottom-left corner: tiny microtext "白洋淀 · 七月"

RED SEAL STAMP: a small square vermilion-red seal (#B83A2C) in the upper-right corner, about 3% of canvas. Contains the Chinese character "泽" in cream/white inside (like the character is the negative space of the seal). Slight roughness at edges like a real ink stamp. A few tiny scattered red ink flecks nearby like stamp imperfections.

MOOD: quiet, nostalgic, literary, like a personal page from an old Chinese travel diary or 1980s art book. Some halftone grain in photo fragment, all elements aged together.

COLOR PALETTE:
- Cream-yellow paper ~70%
- Photo fragment (muted blue, gray, soft green) ~22%
- Vermilion red seal and ink flecks ~2%
- Pencil graphite lines ~3%
- Text in dark warm gray ~3%
No other high-chroma colors.

AVOID: bright digital backgrounds, sharp clean edges on photo fragment (MUST be torn), modern sans-serif fonts, multiple competing colors, cartoon illustration, 3D effects, shadows, gradients on paper, logos, watermarks, decorative borders, the full sky, dense flowers, foreground leaves in the photo fragment.
```

## ImageGen Call Pattern

```python
# source photo + up to 2 reference templates
result = ImageGen(
    image=[source_path, ref_template_1, ref_template_2],  # max 3
    input_fidelity=0.30,  # 0.30-0.40 recommended
    prompt=prompt_text,    # the filled template above
    quality="high",
    size="1080x1620"      # 2:3 vertical
)
```

## Tips

- **`input_fidelity` 0.30–0.40**: enough to keep the source photo's fragment recognizable, low enough to let the prompt govern style.
- **Photo fragment wording matters**: explicitly list what to EXCLUDE (`NOT the foreground leaves, NOT the full sky, NOT the wide horizon`). The model otherwise crops to the obvious center.
- **Tear language matters**: include "torn", "ragged", "paper fibers", "irregular". This is the visual anchor of the style.
- **Seal character**: pick one that fits the subject. For water/lake scenes → 泽 or 水. For mountains → 山. For cities → 城.
- **First-run failure mode**: model often forgets the seal or replaces torn edge with clean cut. Strengthen those words and regenerate once.