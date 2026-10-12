---
name: mryx-festival-poster
description: Create Meiji Everyday Enjoy (每日悦享) holiday/solar-term poster directions and prompts for 9:16 vertical posters, using fixed logo and product assets when provided.
---

# mryx-festival-poster

This skill is specialized for **美赞臣每日悦享** holiday / solar-term posters.
Default format is **9:16 vertical**.

This upgraded version supports **fixed logo assets** and **fixed product packshot assets**.
The skill must treat selected logo/product files as locked brand assets, not generative subjects.

## Core Goal
Transform a short poster brief into:
1. Selected assets
2. Poster direction
3. Composition
4. Visual element plan
5. Background-only image prompt
6. Compositing instructions
7. Negative constraints

## Default assumptions
If the user does not specify otherwise:
- poster type: holiday / solar-term brand poster
- aspect ratio: 9:16 vertical
- retain a title-safe area
- retain a clean product-display area
- premium, restrained, warm, branded tone
- avoid strong promotional aesthetics

## Fixed asset rules
When asset files are provided or mentioned, always prefer existing assets from:
- assets/logos/
- assets/products/
- assets/brand-guides/asset-manifest.md

### Non-negotiable rules
- Do not redraw the logo.
- Do not reinterpret the logo typography.
- Do not redesign product packaging.
- Do not change product proportions.
- Do not fabricate package graphics or labels.
- Do not claim real assets were used if none were provided.

If no fixed asset files are supplied, explicitly say that the current output is for **background generation / layout planning only**.

## Workflow
When the user gives a request:

1. Determine whether the request is a holiday poster or a solar-term poster.
2. Determine the tone: gift-like / warm / clean / seasonal / restrained / festive.
3. Select the best composition pattern from `references/composition-9x16.md`.
4. Select logo/product assets if specified or infer likely asset placeholders from `asset-manifest.md`.
5. Plan clear title-safe area and product-display area.
6. Decide suitable supporting visuals and color atmosphere.
7. Produce a **background-only prompt**.
8. Produce **compositing instructions** for the fixed logo/product assets.

## Output structure
Always return the following sections.

### Selected Assets
List:
- Logo asset
- Product asset(s)
- Whether they are real provided assets or only placeholders

### Poster Direction
A one-paragraph art-direction summary.

### Composition
Describe the 9:16 layout, title-safe area, product position, and supporting visual balance.

### Visual Elements
List the main scene elements, seasonal cues, and supporting props.

### Color & Lighting
Define palette and lighting behavior.

### Background Prompt
Write a generation-ready prompt for the **background / scene only**.
Do not ask the model to generate logo or product if fixed assets should be composited later.

### Compositing Instructions
Specify:
- where the logo goes
- where product packshot(s) go
- approximate scale
- whether to add contact shadows / subtle reflection / integration adjustments
- what must remain unchanged

### Negative Constraints
List what must be avoided.

## Execution preference
If the user asks for prompt-only output, provide the structured output only.
If the environment later supports reliable image generation, the recommended production flow is:
- generate background first
- composite fixed logo and product assets afterward

## Important behavior
Never describe the logo/product as “generated” if the workflow is background-only.
Never say fixed assets were applied unless they are actually specified.
