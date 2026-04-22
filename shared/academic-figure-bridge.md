# Academic Figure Bridge for Paper Writing

Use this shared reference when planning, specifying, prompting, or reviewing
conceptual paper figures. It is not a replacement for plotting libraries,
slide tools, or LaTeX packaging; it adds figure-role, style, and QA discipline
to the paper-writing workflow.

## What This Bridge Is For

Use it for:

1. teaser, overview, and system figures,
2. architecture and module-detail diagrams,
3. comparison or ablation layouts that are more than standard bar or line charts,
4. caption and figure-reference cleanup so the figure matches the paper story.

Do not use it as a substitute for normal data plotting. If the figure is mainly a
quantitative chart, prefer a deterministic plotting workflow.

## Default Posture

1. Decide the figure's job before choosing a visual style.
2. Prefer editable or vector-first artifacts for final submission-facing figures.
   Use AI-image prompts for ideation, fast mockups, or explicit user request.
3. Default to restrained academic styling. Only use a modern airy pastel branch
   when the user asks for it or when that style clearly fits the paper.
4. Lock a palette or reference figure before generating a long prompt.
5. Keep terminology, notation, panel names, and caption wording identical to the
   paper.

## Figure Decision Flow

1. Classify the figure role: `teaser`, `overview`, `architecture`,
   `module-detail`, `comparison`, or `data-pattern`.
2. Choose the asset mode: `editable spec`, `AI prompt`, or `hybrid`.
3. Choose the style branch: `traditional minimal-ink` or
   `modern airy pastel`.
4. Define mandatory panels, arrows, labels, dimensions, formulas, and callouts.
5. Write the caption hook and cross-reference role in the paper.
6. Run the QA gate before treating the figure as ready.

## Style Branches

### Traditional Academic Default

Use this unless the user explicitly wants something else.

1. Mostly white canvas or white-filled boxes.
2. Color appears on borders, key arrows, or restrained labels rather than large
   fills.
3. Use at most two to three controlled accent colors plus greys.
4. Avoid gradients, glows, rainbow palettes, banner bars, fake dashboards, or
   decorative icons.
5. If insets or thumbnails are needed, prefer grayscale or two-color visuals.

### Modern Airy ML Style

Use this only when the user explicitly wants a modern ICLR/NeurIPS-style visual
language or the paper already fits that aesthetic.

1. Pure white canvas with white panels and only subtle shadow separation.
2. Rounded sans-serif typography, floating elements, pill labels, and pastel
   tokens.
3. Dense but uncluttered panel interiors.
4. Keep the same figure-role discipline and QA bar as the traditional branch.

## AI Prompt Rules

1. Prompts should be in English even if the surrounding explanation is in
   Chinese.
2. Resolve palette selection first unless the user already gave a reference
   figure or explicit colors.
3. Describe layout, panels, arrows, formulas, labels, content density, and
   forbidden styles explicitly.
4. Do not leave empty boxes, vague placeholders, `etc.`, or "same as above"
   instructions in final prompts.
5. If style matching matters, ask for or extract a reference image rather than
   guessing.

## Figure QA Gate

Before handoff, check:

1. Does the figure have one clear job in the paper story?
2. Would the title, abstract, and first figure tell a consistent story to a
   skeptical reviewer?
3. Are labels, notation, and panel names identical to the paper text?
4. Is the figure readable in grayscale or at least robust to low-saturation
   viewing?
5. Is most of the canvas white or near-white unless the user explicitly asked
   for a stronger visual style?
6. Are there only a few controlled accent colors rather than a decorative
   palette?
7. Are there empty or decorative boxes that should instead contain real
   structure, formulas, or miniature visuals?
8. Does the figure avoid obvious AI-looking artifacts, pictorial noise, and
   style drift away from submission-quality academic graphics?
9. Does the caption point the reader to the takeaway instead of merely
   restating visible objects?

## Output Contract for Figure Tasks

When figure work is requested, return:

1. `figure_role`
2. `asset_mode`
3. `style_branch`
4. `palette`
5. `layout_spec`
6. `required_elements`
7. `caption_hook`
8. optional English `figure_prompt`
9. `qa_risks`

## Attribution

This bridge is informed in part by the academic figure prompt workflows in
`LigphiDonk/academic-figure-generator` (MIT), adapted into the paper-writing
workflow in this repo.
