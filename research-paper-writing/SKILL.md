---
name: research-paper-writing
description: Improve academic paper writing quality for ML/CV/NLP-style papers with clear section structure, paragraph flow, agent-style-backed clarity, citation discipline, reviewer-facing presentation, and figure-story discipline. Use when drafting or revising sections, planning teaser/overview/method figures, generating figure specs or AI figure prompts, polishing figures/tables, checking claim-support alignment, or performing self-review before submission.
---
# Research Paper Writing

## Overview

Use this skill to rewrite a research paper into a reviewer-friendly, high-clarity draft.
Prioritize first-impression quality (figures/tables/layout), logical flow, and evidence-backed claims.
Load `../shared/agent-style-paper-bridge.md` as the shared prose-quality layer before
sentence-level edits. It adds claim calibration, citation discipline, terminology stability,
and anti-LLM-tell cleanup without replacing the section guides.
Load `../shared/academic-figure-bridge.md` when the task includes teaser, overview,
method, or comparison figures, figure prompts, or figure QA. It adds figure-role,
style-branch, and asset-mode discipline without replacing normal charting or LaTeX
packaging.

## Core Workflow

1. Clarify the paper story before sentence-level edits.
2. Load `../shared/agent-style-paper-bridge.md` plus the needed section-specific guidance in
   `references/`.
3. If the task includes conceptual figure work, also load
   `../shared/academic-figure-bridge.md` and decide the figure role before choosing a
   style or writing a prompt.
4. Rewrite paragraph-by-paragraph with one message per paragraph.
5. Run reverse outlining after writing each section.
6. Check every major claim in Abstract/Introduction and every factual synthesis in Related
   Work against experimental evidence or real citations.
7. For figure tasks, choose `editable spec`, `AI prompt`, or `hybrid` mode, then run the
   figure QA gate before final handoff.
8. Run final-paper adversarial review with `references/paper-review.md`.
9. Finish with a style sweep against the shared bridge: remove filler, repeated sentence
   starts, unsupported facts, terminology drift, and forced bullets.

## Global Principles

1. Keep one paragraph for one message only.
2. State the paragraph message in the first sentence.
3. Make nouns self-contained; define new terms before reusing them.
4. Maintain sentence-to-sentence flow (cause, contrast, consequence, or refinement).
5. Support factual claims with citation or concrete evidence; never invent support.
6. Calibrate verbs to evidence strength; prefer `suggests` or `indicates` over `proves` when
   support is limited.
7. Keep terminology and abbreviations stable across the full paper.
8. Keep related words together, put important information in the stress position, and split
   long sentences before they become hard to parse.
9. Iterate with adversarial self-review: read as a skeptical reviewer.
10. Treat visual quality as core content, not decoration.
11. Use a clean teaser and pipeline figure.
12. Use readable, minimal-ink tables.
13. Keep formatting consistent and tidy.
14. Prefer formal technical prose: bullets only for genuine lists, and avoid casual
    contractions in the final paper.

## Paragraph Clarity Check (Important)

Use this quick test whenever the user asks whether a paragraph "flows" or is clear.

1. Read as an external reader:
   - Does this paragraph have one explicit message?
   - Does the first sentence state what this paragraph will do?
   - Are all key nouns/terms readable without hidden context?
   - Does each sentence connect to the previous one with a clear relation (cause, contrast, consequence, refinement, example)?
2. Run reverse outlining for the current section:
   - Write down thesis/main claim.
   - Write down each paragraph topic sentence.
   - Write down the evidence/explanation points under each paragraph.
   - Check mapping: topic sentence -> thesis, and evidence -> topic sentence.
   - Revise or remove any paragraph that cannot be mapped cleanly.
3. If flow is still weak, add temporary section headers and explicit transition phrases during revision, then remove unnecessary headers before finalizing.

Source reference for this check:

- `references/does-my-writing-flow-source.md`

## Figure Work (Important)

Use `../shared/academic-figure-bridge.md` whenever figure work is part of the
writing task.

1. Start with the figure's job in the paper story, not with a visual style.
2. Prefer editable or vector-first specs for final submission-facing figures; use
   AI-image prompts for ideation, mockups, or explicit user request.
3. Default to restrained academic styling; only use the modern airy pastel branch
   when the user asks for it or the paper already fits that style.
4. Keep terminology, notation, panel labels, and caption wording identical to the
   paper text.
5. Use normal plotting workflows for quantitative charts; use this bridge for
   conceptual diagrams, teaser figures, and prompt or spec generation.
6. Do not hand off a figure brief or prompt until the figure QA gate is clean.

## Section Guides

Load only the needed section file:

- Shared style bridge: `../shared/agent-style-paper-bridge.md`
- Shared figure bridge: `../shared/academic-figure-bridge.md`
- Introduction: `references/introduction.md`
- Abstract: `references/abstract.md`
- Related Work: `references/related-work.md`
- Method: `references/method.md`
- Experiments: `references/experiments.md`
- Conclusion: `references/conclusion.md`
- Paper review (Paper Rview): `references/paper-review.md`
- Paragraph clarity source: `references/does-my-writing-flow-source.md`
- Example bank index: `references/examples/index.md`

## Paper Review Core Points

Use `references/paper-review.md` for the full checklist and workflow.

1. Add an end-of-draft self-review question list in five dimensions:
   - contribution,
   - writing clarity,
   - experimental strength,
   - evaluation completeness,
   - method design soundness.
2. Treat claim-evidence alignment as a hard constraint, especially for Abstract and Introduction.
3. Treat claim-citation alignment as a hard constraint for Related Work and any factual background statement.
4. Perform adversarial writing: review as a skeptical reviewer and resolve every high-risk question.
5. Revise until major rejection risks are explicitly addressed.
6. Review the first figure, its caption, and its in-text reference against the paper story; if
   the visual sells a different story than the text, revise one or both.

## Execution Rules

1. Build a mini-outline before drafting prose.
2. For each subsection, explicitly include motivation, design, and technical advantage when applicable.
3. Avoid writing style that looks like incremental patching of a naive baseline.
4. Keep terminology stable across the full paper, figures, and tables.
5. If a claim cannot be supported by results or real citations, weaken or remove the claim.
6. Before finalizing, append and answer a five-dimension self-review question list, then revise the paper based on unresolved items.
7. Run a final agent-style sweep for filler phrases, overlong sentences, repeated sentence openings, and empty transition words.
8. Do not load all section references (Introduction/Abstract/Related Work/Method/Experiments/Conclusion) at once; load only the specific section guide needed for the current edit target.
9. For conceptual figure work, decide `figure_role -> asset_mode -> style_branch -> layout_spec -> QA` in that order.
10. Prefer editable figure specs or vector-first instructions for final submission-facing work; only emit raw AI-image prompts when the user wants them or when ideation speed matters more than editability.

## Output Contract

When asked to rewrite or draft sections, return:

1. A compact section outline (3-7 bullets).
2. Revised paragraphs with explicit paragraph roles (opening/challenge/method/advantage/evidence/limitation).
3. A short self-review checklist covering clarity, flow, terminology consistency, claim calibration, unsupported claims, missing evidence, and missing citations.
4. A claim-evidence map for each major claim in the revised text using `Claim: ... | Evidence: ... | Status: supported/needs evidence`.
5. A style-risk list naming any remaining filler, sentence-length, terminology, or citation-discipline issues.
6. When figure work is requested, a figure brief with `figure_role`, `asset_mode`,
   `style_branch`, `layout_spec`, `caption_hook`, optional English `figure_prompt`, and
   `qa_risks`.
