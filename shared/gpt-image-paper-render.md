# GPT Image Paper Render Bridge

Use this shared reference when a paper figure task needs an actual raster render or
reference-image edit through OpenAI GPT Image 2. This is a rendering backend, not a
 replacement for the paper's figure-role, caption, or QA logic.

## What This Bridge Is For

Use it for:

1. teaser or overview figure mockups,
2. concept-heavy system figures that need a fast visual draft,
3. Chinese typography or poster-like layouts where GPT Image 2 is especially strong,
4. reference-image editing when the user already has a figure or visual starting point.

Do not use it for:

1. exact benchmark plots, scaling curves, or other quantitative charts,
2. final camera-ready diagrams that still need frequent geometry edits,
3. workflows that depend on mask-based inpainting with GPT Image 2.

## Preconditions

1. Start from a figure brief that already locks `figure_role`, `style_branch`,
   `layout_spec`, and `caption_hook`.
2. Prefer the local `gpt-image` skill if it is installed.
3. If the skill is unavailable, the backend can still be called through the CLI:

```bash
uvx --from git+https://github.com/wuyoscar/gpt_image_2_skill \
  gpt-image -p "PROMPT" --size 2k --quality high -f out.png
```

4. `OPENAI_API_KEY` must be available in env or `~/.env`.

## When GPT Image 2 Is a Good Fit

Choose this backend when one or more of these are true:

1. The user explicitly wants a rendered image, not only a figure brief.
2. The figure contains rich layout, icons, scene composition, or Chinese text.
3. A reference image should be restyled while preserving composition.
4. Fast ideation matters more than editability for this iteration.

Stay with spec-only or vector-first work when exact editability is more important than
speed.

## Recommended Workflow

1. Lock the figure brief through `academic-figure-bridge.md`.
2. Choose render mode:
   - `text-to-image` for fresh mockups,
   - `reference-image edit` when the user already has a useful starting image.
3. Convert the figure brief into an English prompt with explicit panels, labels,
   arrows, colors, and forbidden artifacts.
4. Default to `--quality high` for paper-facing renders. Typography and dense layouts
   degrade noticeably below that.
5. Use `--size 2k` or larger for paper mockups unless the user explicitly wants a fast
   low-cost draft.
6. If using reference images, preserve the figure's labels, composition, and panel
   semantics rather than asking for a vague restyle.
7. Save the output path and run render QA before treating the asset as usable.

## Render QA

Before handing off a GPT Image 2 output, check:

1. Are all required labels readable and spelled exactly as requested?
2. Is any Chinese or dense typography clean rather than garbled?
3. Does the image keep the intended panel structure instead of collapsing into poster
   noise?
4. Does it avoid decorative clutter, fake UI chrome, or irrelevant icons?
5. Does it still match the paper's terminology and caption hook?
6. If the asset may survive into submission, should it be traced or rebuilt as an
   editable vector figure before final use?

## Known Backend Pitfalls

1. The GPT Image 2 reference-image path uses the Responses API; mask-based inpainting is
   not supported there.
2. Low quality settings are often too weak for typography-heavy paper figures.
3. Real-person likeness edits may refuse; surface the refusal instead of silently
   retrying with a different story.
4. Use GPT Image 2 for figure ideation and controlled mockups, not for exact numeric
   charts.

## Output Contract for Render Tasks

When GPT Image 2 rendering is requested, return:

1. `render_backend`: `gpt-image`
2. `render_mode`: `text-to-image` or `reference-image edit`
3. `render_prompt`
4. `render_inputs` (reference images, size, quality, output path)
5. `render_qa_risks`

## Attribution

This bridge is informed in part by `wuyoscar/gpt_image_2_skill` (CC BY 4.0),
adapted into the paper-writing workflow in this repo.
