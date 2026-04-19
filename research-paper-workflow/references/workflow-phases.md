# Workflow phases for `research-paper-workflow`

Use this reference to keep the orchestrator thin and consistent.

## Standard path

| Phase | Goal | Typical output | Skip or shorten when |
| --- | --- | --- | --- |
| Intake | Define the target paper package | scope summary, deliverables list | the user already gave a precise package |
| Claim gate | Decide what the paper can honestly claim | supported / partial / unsupported table | never skip entirely |
| Plan | Lock the paper story before prose | thesis, outline, figure plan | only shorten when the draft is already stable |
| Draft | Write sections with `research-paper-writing` | section drafts, updated claim-evidence map | skip if the user already has a full draft |
| Package | Produce figures + LaTeX + PDF artifacts | figure set, `.tex`, `.pdf` | shorten if the user only wants text |
| Review | Run critique and polish | review notes, polish summary, remaining blockers | never skip for submission-facing work |
| NotebookLM (optional) | Produce presentation assets | alt figures, slides, study-guide style assets | skip unless explicitly requested |

## Claim gate template

Use a compact table:

| Claim | Evidence | Status | Action |
| --- | --- | --- | --- |
| Main contribution | benchmark table + ablation | supported | keep |
| Broad generalization claim | only one dataset | partial | narrow wording |
| Strong causal claim | no causal evidence | unsupported | remove or reframe |

Rules:

1. Unsupported claims do not survive into the main outline.
2. Partial claims must be narrowed before they appear in the abstract or introduction.
3. The one-sentence contribution statement should only use supported or carefully
   narrowed partial claims.

## Planning package

The plan should usually fit on one screen:

1. one-sentence contribution,
2. target reader / venue framing,
3. section outline,
4. figure list,
5. final requested artifacts.

Avoid turning planning into a long detached memo unless the user explicitly asks for
that.

## Drafting package

During drafting, keep one living paper-level checklist:

1. terminology is stable,
2. each section has a clear role,
3. abstract and introduction only contain claims backed by the later sections,
4. figures are referenced where they matter,
5. any missing numbers are surfaced explicitly rather than guessed.

## Review package

Before final handoff, answer three questions:

1. **Story:** is the contribution statement still the smallest honest version of the
   paper?
2. **Support:** does every major abstract/introduction claim map to concrete evidence?
3. **Presentation:** would a skeptical reviewer understand the story from title,
   abstract, intro, and first figure/table?

If any answer is weak, revise before treating the package as done.

## Optional NotebookLM branch

NotebookLM outputs are downstream communication assets.

Use them for:

1. alternate teaser or overview graphics,
2. slide decks,
3. other explanatory assets tied to a finished or near-finished paper.

Do not use them as a substitute for the main paper-writing path.
