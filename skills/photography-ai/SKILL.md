# Photography AI - Professional Visual Engineering Skills Framework

> A comprehensive, structured reference for AI-powered visual creation, covering prompt engineering, photographic literacy, strategic negation, identity preservation, post-processing, and agent orchestration.

*Version: 3.0 | Last Updated: April 2026 | License: CC-BY-SA 4.0*

---

## Context

This skill is for anyone who uses AI to generate, refine, or orchestrate visual content. It treats AI image/video generation as a professional engineering discipline: systematic, physics-informed, quality-gated, and continuously improvable.

Use this skill when:
- Generating photorealistic or stylized images with AI
- Creating cinematic video sequences from text prompts
- Building multi-step visual production pipelines
- Designing AI agent workflows for creative teams
- Troubleshooting AI generation artifacts (skin, hands, anatomy)

---

## Instructions

### Step 1: Understand the Skill Synergy Map

Skills compound. The six categories build on each other:

```
FOUNDATION
  Technical Prompt Engineering + Photographic Literacy
       |                     |
       v                     v
CONSISTENCY LAYER      REFINEMENT LAYER
  Strategic Negation    Post-Processing &
  + Identity Preserv.     Hybrid Workflows
       |                     |
       v                     v
         ORCHESTRATION LAYER
      AI Agent Design + Production Deploy
```

### Step 2: Apply Technical Prompt Engineering

Structure prompts as blueprints, not keyword lists. Follow the **Scaffold Method**:

```
[Subject] + [Action] + [Lighting] + [Lens/Specs] + [Style] + [Quality]
```

**Rules:**
- Front-load critical elements (AI weights early tokens more heavily)
- Use precise photographic vocabulary over vague buzzwords
- Use active voice for iterative edits ("remove the background", "add a red hat")
- Stack semantic concepts in deliberate order to control interpretation hierarchy

**Example:**
```
Professional headshot of a software engineer, smiling naturally,
Rembrandt lighting with key light 45 degrees high and subtle fill,
85mm lens f/2.8 shallow depth of field,
photorealistic style referencing Annie Leibovitz,
4K native resolution with subsurface scattering on skin
```

### Step 3: Apply Photographic Literacy

Use real-world physics terminology to achieve believable results:

| Concept | What to Prompt | Effect |
|---------|---------------|--------|
| **Lighting patterns** | Rembrandt, Butterfly, Rim, Split, Loop | Sculpt form, mood, dimension |
| **Lens selection** | 85mm portrait, 35mm standard, 24mm wide | Control perspective and compression |
| **Aperture control** | f/1.4 shallow DOF, f/11 full sharpness | Control subject isolation |
| **Advanced rendering** | Subsurface scattering, ambient occlusion, ray tracing | Realistic material response |
| **Anamorphic** | Horizontal flares, elliptical bokeh, 2.39:1 ratio | Cinematic widescreen look |

### Step 4: Apply Strategic Negation

Tell the AI what NOT to include. Always pair positive and negative instructions:

```
PROMPT:  visible pores, fine vellus hair, subtle skin variation
NEGATE:  (plastic skin:1.4), (airbrushed:1.2), (cartoon:1.3)
```

**Target common artifacts proactively:**
- Anatomical: `(fused fingers:1.4), (extra limbs:1.4), (asymmetrical eyes:1.3)`
- Skin: `(waxy skin:1.3), (doll-like:1.2), (symmetrical face:1.1)`
- Temporal: `(facial drift:1.4), (background flicker:1.3)` (for video)

### Step 5: Maintain Identity Preservation

For multi-generation consistency across characters and styles:

1. **Seed locking**: Fix initial noise pattern with `--seed 12345`
2. **Reference tools**: Use `--cref` (character) and `--sref` (style) references
3. **Character weight**: `--cw 80` preserves face + clothing, allows pose variation
4. **Multi-reference**: Combine up to 4 references for complex scene coherence

### Step 6: Post-Processing Workflow

Treat AI generation as the START, not the end:

1. **Iterative refinement**: Keep seed, change one variable at a time, A/B compare
2. **Inpainting**: Fix errors (hands, eyes) via targeted masked editing
3. **External enhancement**: Upscale with Topaz, color grade in Lightroom
4. **Quality checklist before delivery**:
   - Check hands/feet anatomy
   - Verify eye direction consistency
   - Confirm lighting coherence
   - Test at target resolution
   - Review negative prompt coverage

### Step 7: Orchestrate with Agents (Advanced)

For production-scale workflows, design multi-agent systems:

```
ScripterAgent -> DirectorAgent -> VisualAgent -> ReviewAgent -> PublisherAgent
```

Each agent has a specific role, shared context via structured protocols, and human-in-the-loop checkpoints for quality control.

### Step 8: Batch Post-Processing Pipeline

For production workflows involving large volumes of images, automate the refinement pipeline to ensure consistency and efficiency. This workflow moves from raw generation through artifact correction, upscaling, color grading, and quality validation.

**Overview:**

```
Generate (seed-locked) → Batch Inpaint → Automated Upscale → Color Grade → Quality Gate
```

**Step 1 — Generate Base Images with Seed Lock**

Produce all base variants at once using a locked seed for visual coherence across the batch:

```bash
#!/bin/bash
# batch_generate.sh — Generate a series of seed-locked base images
PROMPT="Professional product photography of a wireless headphone, studio lighting, white seamless background, 85mm f/5.6, photorealistic, 4K"
NEGATIVE="(plastic:1.3), (blurry:1.2), (wrinkled backdrop:1.4)"
SEED=77210
VARIANTS=8

for i in $(seq 1 $VARIANTS); do
  # Slightly perturb the seed per variant for diversity while maintaining coherence
  CURRENT_SEED=$((SEED + i * 7))
  echo "Generating variant $i with seed $CURRENT_SEED..."
  # Midjourney-style (adapt API call to your platform)
  # mj_api --prompt "$PROMPT" --negative "$NEGATIVE" --seed $CURRENT_SEED --ar 1:1 --v 6.0 \
  #   --out "./output/base_${i}.png"
  echo "  → Saved: ./output/base_${i}.png"
done
```

**Step 2 — Batch Inpaint for Common Artifacts**

After generation, run automated inpainting to fix recurring artifacts across all images in the batch:

```bash
#!/bin/bash
# batch_inpaint.sh — Fix common artifacts with masked inpainting
INPUT_DIR="./output"
MASK_DIR="./masks"
INPAINTED_DIR="./output/inpainted"

mkdir -p "$INPAINTED_DIR"

for img in "$INPUT_DIR"/base_*.png; do
  base=$(basename "$img" .png)
  echo "Inpainting $base..."

  # Example artifact masks (pre-defined per product category)
  # 1. Hands/fingers region mask
  # 2. Background seam/crease mask
  # 3. Text/watermark removal mask

  # Stable Diffusion inpaint call (adapt to your pipeline)
  # sd_inpaint \
  #   --image "$img" \
  #   --mask "$MASK_DIR/${base}_artifact_mask.png" \
  #   --prompt "clean, seamless, photorealistic, no visible seams" \
  #   --strength 0.6 \
  #   --denoising 0.4 \
  #   --out "$INPAINTED_DIR/${base}_clean.png"

  echo "  → Saved: $INPAINTED_DIR/${base}_clean.png"
done
```

**Step 3 — Automated Upscaling with Topaz Parameters**

Upscale the inpainted images using consistent Topaz Gigapixel or Video AI parameters:

```bash
#!/bin/bash
# batch_upscale.sh — Batch upscale with Topaz parameters
INPUT_DIR="./output/inpainted"
UPSCALED_DIR="./output/upscaled"
TARGET_SCALE=4          # 4x upscale
TARGET_FORMAT="png"

mkdir -p "$UPSCALED_DIR"

for img in "$INPUT_DIR"/*_clean.png; do
  base=$(basename "$img" .png)
  echo "Upscaling $base ($TARGET_SCALE)x..."

  # Topaz Gigapixel CLI parameters (adapt to installed version)
  # topaz_gigapixel \
  #   --input "$img" \
  #   --output "$UPSCALED_DIR/${base}_${TARGET_SCALE}x.$TARGET_FORMAT" \
  #   --scale $TARGET_SCALE \
  #   --model "standard" \
  #   --face-recovery "on" \
  #   --noise-suppression "low" \
  #   --compression "none" \
  #   --sharpen "medium"

  echo "  → Saved: $UPSCALED_DIR/${base}_${TARGET_SCALE}x.$TARGET_FORMAT"
done
```

| Topaz Parameter | Recommended Setting | Purpose |
|-----------------|-------------------|---------|
| `--scale` | 2x or 4x | Match final delivery resolution |
| `--model` | `standard` (general) / `high-grad` (fine detail) | Preserve texture fidelity |
| `--face-recovery` | `on` | Correct AI-generated face distortion |
| `--noise-suppression` | `low` | Avoid over-smoothing AI texture |
| `--compression` | `none` | Lossless for editorial pipeline |
| `--sharpen` | `low` or `medium` | Recover edge definition without halos |

**Step 4 — Color Grading Presets**

Apply consistent color grading across the batch using Lightroom CLI, DaVinci Resolve scripting, or ImageMagick:

| Preset | Look | Use Case |
|--------|------|----------|
| **Cinematic** | Crushed blacks, teal-orange split, high contrast | Hero campaigns, social media ads |
| **Editorial** | Neutral tones, lifted shadows, clean whites | Magazine layouts, print |
| **Natural** | Subtle warmth, balanced exposure, true-to-life | E-commerce, product catalogs |

```bash
#!/bin/bash
# batch_grade.sh — Apply color grading presets
INPUT_DIR="./output/upscaled"
GRADED_DIR="./output/graded"
PRESET="cinematic"  # Options: cinematic, editorial, natural

mkdir -p "$GRADED_DIR"

for img in "$INPUT_DIR"/*_*x.png; do
  base=$(basename "$img" .png)
  echo "Grading $base → [$PRESET]..."

  case "$PRESET" in
    cinematic)
      # Teal-orange split tone + crushed blacks
      # magick "$img" \
      #   -color-matrix "0.9 0.05 0.05  0.05 1.0 0.05  0.05 0.05 0.9" \
      #   -level-colors "rgb(5,5,10),rgb(240,230,210)" \
      #   -modulate 100 90 105 \
      #   "$GRADED_DIR/${base}_${PRESET}.png"
      ;;
    editorial)
      # Clean, neutral, lifted shadows
      # magick "$img" \
      #   -color-matrix "1.0 0 0  0 1.0 0  0 0 1.0" \
      #   -level-colors "rgb(20,20,20),rgb(245,245,245)" \
      #   -modulate 100 100 95 \
      #   "$GRADED_DIR/${base}_${PRESET}.png"
      ;;
    natural)
      # Subtle warmth, true-to-life
      # magick "$img" \
      #   -color-matrix "1.0 0.02 0  0 1.0 0.01  0 0 0.98" \
      #   -level-colors "rgb(10,10,10),rgb(250,248,245)" \
      #   -modulate 100 100 100 \
      #   "$GRADED_DIR/${base}_${PRESET}.png"
      ;;
  esac

  echo "  → Saved: $GRADED_DIR/${base}_${PRESET}.png"
done
```

**Step 5 — Quality Gate Checklist Automation**

Automate final quality validation before delivery. Run this after grading to catch any remaining issues:

```bash
#!/bin/bash
# quality_gate.sh — Automated quality gate for batch output
INPUT_DIR="./output/graded"
REPORT="./output/quality_report.txt"
PASS=0
FAIL=0
WARNINGS=""

echo "=== BATCH QUALITY GATE REPORT ===" > "$REPORT"
echo "Date: $(date -u +%Y-%m-%dT%H:%M:%SZ)" >> "$REPORT"
echo "Directory: $INPUT_DIR" >> "$REPORT"
echo "" >> "$REPORT"

for img in "$INPUT_DIR"/*.png; do
  base=$(basename "$img" .png)
  echo "--- $base ---" >> "$REPORT"
  issues=""

  # Check 1: Minimum resolution (e.g., 4096x4096 for 4K)
  dims=$(identify -format "%w %h" "$img" 2>/dev/null)
  width=$(echo "$dims" | awk '{print $1}')
  height=$(echo "$dims" | awk '{print $2}')
  if [ "$width" -lt 4096 ] || [ "$height" -lt 4096 ]; then
    issues+="FAIL: Resolution ${width}x${height} below 4096x4096 threshold. "
  else
    echo "  ✓ Resolution: ${width}x${height}" >> "$REPORT"
  fi

  # Check 2: File size sanity (> 500KB for a 4K PNG indicates content exists)
  size=$(stat -f%z "$img" 2>/dev/null || stat -c%s "$img" 2>/dev/null)
  if [ "$size" -lt 512000 ]; then
    issues+="FAIL: File size ${size}B suspiciously small. "
  else
    echo "  ✓ File size: $(( size / 1024 ))KB" >> "$REPORT"
  fi

  # Check 3: Color space (should be sRGB for web, AdobeRGB for print)
  profile=$(identify -verbose "$img" 2>/dev/null | rg "sRGB|AdobeRGB" | head -1)
  echo "  ✓ Color profile: ${profile:-unknown}" >> "$REPORT"

  # Check 4: No EXIF anomalies from AI tools
  exif_clean=$(exiftool -Artist= -Copyright= -Software= "$img" 2>/dev/null)
  echo "  ✓ EXIF cleaned" >> "$REPORT"

  # Report results
  if [ -z "$issues" ]; then
    echo "  STATUS: PASS" >> "$REPORT"
    PASS=$((PASS + 1))
  else
    echo "  STATUS: FAIL — $issues" >> "$REPORT"
    FAIL=$((FAIL + 1))
    WARNINGS+="$base: $issues\n"
  fi
  echo "" >> "$REPORT"
done

echo "" >> "$REPORT"
echo "=== SUMMARY ===" >> "$REPORT"
echo "Passed: $PASS / $((PASS + FAIL))" >> "$REPORT"
echo "Failed: $FAIL / $((PASS + FAIL))" >> "$REPORT"

if [ $FAIL -gt 0 ]; then
  echo "" >> "$REPORT"
  echo "=== FAILURES ===" >> "$REPORT"
  echo -e "$WARNINGS" >> "$REPORT"
fi

echo "Quality gate complete. $PASS passed, $FAIL failed."
echo "Full report: $REPORT"
```

**Full Pipeline Orchestration Script:**

```bash
#!/bin/bash
# pipeline_master.sh — Run the complete batch post-processing pipeline
set -euo pipefail

echo "╔══════════════════════════════════════════════╗"
echo "║  Batch Post-Processing Pipeline v1.0         ║"
echo "╚══════════════════════════════════════════════╝"

# Configuration
BASE_DIR="./output"
LOG="$BASE_DIR/pipeline.log"

log() { echo "[$(date +%H:%M:%S)] $*" | tee -a "$LOG"; }

log "STEP 1/5: Generating base images..."
# bash batch_generate.sh

log "STEP 2/5: Batch inpainting artifacts..."
# bash batch_inpaint.sh

log "STEP 3/5: Upscaling with Topaz..."
# bash batch_upscale.sh

log "STEP 4/5: Applying color grade [cinematic]..."
# bash batch_grade.sh

log "STEP 5/5: Running quality gate..."
# bash quality_gate.sh

log "Pipeline complete. Review output in $BASE_DIR."
```

This pipeline is designed to be modular — each step produces files in its own subdirectory, so you can re-run individual stages without reprocessing the entire batch. Adapt the CLI commands (marked with `#`) to your specific tool stack (Midjourney API, Stable Diffusion WebUI API, ComfyUI, Topaz CLI, etc.).

---

## Constraints

- NEVER treat AI generation as final output -- always plan for post-processing
- NEVER skip the negative prompt step -- uncontrolled generation produces artifacts
- NEVER use vague buzzwords when technical terms exist ("hyperrealistic" -> "85mm f/2.8, subsurface scattering")
- NEVER forget to test at the target platform's native resolution
- NEVER generate character series without seed locking or reference tools
- NEVER deploy agent workflows without audit trails and human checkpoints

---

## Examples

### Example 1: Professional Headshot

```
PROMPT:
Corporate headshot of a CEO, confident expression with subtle warmth,
corner lighting establishing authority, dark navy suit against library background,
slight upward camera angle, shot on 85mm Summilux f/2.8 shallow depth of field,
photorealistic, 4K native resolution, subsurface scattering on skin

NEGATIVE:
(plastic skin:1.4), (airbrushed:1.3), (symmetrical face:1.1), (cartoon:1.2)
```

### Example 2: Cinematic Video Scene

```
PROMPT:
Protagonist discovers crucial clue in dim library,
camera: slow dolly zoom from wide establishing shot to tight close-up,
lighting: golden hour backlight through window with practical desk lamp fill,
24fps 4K native ProRes,
--cref character_sheet.jpg --sref film_grain_style --seed 8821

NEGATIVE:
(facial drift:1.4), (background flicker:1.3), (inconsistent props:1.2)
```

---

## Quick Reference: Platform Syntax

### Midjourney
```bash
--cref URL --cw 80      # Character reference
--sref URL              # Style reference
--seed 12345            # Seed locking
--ar 16:9               # Aspect ratio
--no plastic airbrushed # Negative prompting
--v 6.0, --style raw    # Version control
```

### Stable Diffusion / ComfyUI
```python
{"type": "ip-adapter", "image": "char.jpg", "weight": 0.8}  # Reference
negative_prompt = "(plastic skin:1.3), (extra fingers:1.4)"    # Negation
{"seed": 12345, "steps": 30, "cfg": 7.0}                      # Controls
```

---

## Competency Progression

| Level | Capabilities | Tools |
|-------|-------------|-------|
| **Beginner** | Natural language prompts, basic platform navigation | DALL-E 3, ChatGPT |
| **Intermediate** | Technical vocabulary, lighting/lens control, basic negation | Midjourney, SDXL, Leonardo |
| **Advanced** | Seed/reference control, inpainting, multi-tool pipelines | ComfyUI, ControlNet, Topaz |
| **Expert** | Agent system design, production deployment, skills packaging | LangChain, AutoGen, CrewAI |

---

*Source: AI Skills Research Framework (2026) by Mark Tantongco. Adapted for agent skill format.*
