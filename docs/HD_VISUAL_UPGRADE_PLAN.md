# Universal LPC HD Visual Upgrade

## Goal

Create an optional, higher-detail pixel-art asset family while preserving the existing Universal LPC assets and the character generator's modular composition workflow.

## Non-negotiable compatibility rules

- Keep the current assets unchanged; the HD work is additive and isolated.
- Do not upscale existing PNGs and call the result new artwork. New detail must be authored at the target resolution.
- Preserve transparent backgrounds, alignment anchors, directional ordering, animation frame dimensions, layer separation, and z-position behavior.
- Every new or derived PNG must have a matching attribution entry in its sheet definition. Do not copy credits blindly: verify the actual source and license for every derivative.
- Do not edit generated `dist/` metadata directly.
- Do not change existing hash keys, URLs, or existing sheet definitions unless a separate compatibility change is justified.

## Phased implementation

### Phase 1: Swordsman pilot

Create a small, self-contained HD asset family for a single swordsman:
- base body and head/hair;
- torso armor, pants, gloves, boots, cape, and one-handed sword as separate layers;
- idle and walk cycles;
- normal slash, reverse slash/backslash, thrust, overhead heavy strike, and spinning slash where source frames can be authored consistently;
- four directions where the motion can be drawn convincingly.

The pilot must be reviewed at native scale and enlarged nearest-neighbor scale. It must not be presented as complete until the frames and transparent edges have been inspected.

### Phase 2: Generator integration

Add the pilot as a separately selectable HD family, following neighboring sheet definitions and the existing attribution schema. Verify that URL selection, palette options where supported, layer ordering, preview rendering, ZIP export, and attribution output continue to work.

### Phase 3: Expand coverage

Inventory all asset categories and classify them as:
1. compatible with existing art and recolor;
2. requiring new HD artwork;
3. animation-specific;
4. not suitable for conversion without redesign.

Upgrade categories incrementally. Avoid an automated blanket conversion that damages pixel art or silently changes geometry.

## Acceptance criteria

- Original LPC selections remain unchanged.
- HD assets are opt-in and clearly labeled.
- Each new image has verified source/author/license/URL attribution.
- Frame bounds and alpha transparency are checked.
- Character parts align in all supported directions and do not drift between frames.
- Attack animations have distinct silhouettes and readable anticipation, impact, and recovery frames.
- The project’s required validation commands pass, including `npm run validate-site-sources`; relevant focused tests are run for any code changes.
- The ZIP export contains the selected assets and accurate attribution.
- Compatibility claims are made only after local visual and functional checks.

## Current status

Planning branch created. This document defines the safe implementation sequence; it does not claim that artwork has already been upgraded. The first deliverable is the Swordsman pilot, not a bulk transformation of every existing PNG.
