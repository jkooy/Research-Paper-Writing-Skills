---
name: research-paper-workflow
description: Orchestrate an end-to-end ML/CV/NLP-style paper workflow: claim gating, outline planning, drafting via research-paper-writing, figure and LaTeX/PDF packaging, final review and polish, with an optional NotebookLM asset branch.
---
# Research Paper Workflow

## Overview

Use this skill as the top-level coordinator when the user wants one workflow from
experiment materials to a reviewer-ready paper package.

This skill is intentionally thin. It should decide the phase order, keep
claim-evidence discipline, and reuse existing skills instead of duplicating their
full guidance:

- `research-paper-writing` remains the main section-writing and section-polish skill.
- `notebooklm` is an optional branch for alternative figures, slide decks, or other
  presentation assets after the paper package is stable.

## Use This Skill When

Use this skill when the user wants a unified workflow such as:

1. turning a report, experiment log, repo, or draft into a paper plan and final paper
   package,
2. going from paper story -> section drafts -> figures -> LaTeX -> PDF -> review loop,
3. coordinating multiple writing stages without manually deciding the next step each time.

## Do Not Use This Skill When

Do not trigger this skill when:

1. the user only wants one section or paragraph rewritten,
2. the user only wants a literature search,
3. the user only wants slides, infographics, or other NotebookLM assets,
4. the task is purely low-level formatting with no paper-level workflow decision.

In those cases, prefer the narrower skill directly.

## Required Companion Skills

1. `research-paper-writing` is the default writing engine for section drafting,
   rewriting, clarity checks, and final wording polish.
2. `notebooklm` is optional. Only use it when the user explicitly asks for an
   alternate figure, infographic, slide deck, or other NotebookLM artifact.

If `research-paper-writing` is unavailable, stop and ask the user to install it.
If `notebooklm` is unavailable, continue the main paper path without the optional
asset branch.

## Core Workflow

Load `references/workflow-phases.md` for the detailed phase checklist.

### Phase 1: Intake and Package Definition

Collect the minimum context needed to route the workflow:

- source materials available now (repo, report, PDF, notes, draft, figures),
- target venue or paper style,
- requested deliverables (`outline`, `paper`, `figures`, `latex`, `pdf`, optional
  `notebooklm-assets`),
- current stage (`idea`, `results`, `draft`, `near-submission`).

At the end of this phase, restate the target package in one sentence.

### Phase 2: Claim Gate

Before outlining prose, build a compact claim table:

- `supported`: evidence already exists,
- `partial`: promising but still needs softer wording or more evidence,
- `unsupported`: remove, weaken, or mark as future work.

Do not let unsupported claims survive into the main paper story.

### Phase 3: Paper Plan

Create the minimum planning package needed for stable drafting:

1. one-sentence contribution statement,
2. section outline,
3. section-level claim map,
4. figure plan,
5. artifact plan (`tex`, `pdf`, optional extras).

Prefer a concise, page-aware outline over a giant planning memo.

### Phase 4: Draft the Paper

Delegate section-level writing to `research-paper-writing`.

Route section work one section at a time:

1. choose the next section,
2. load only the relevant section guidance through `research-paper-writing`,
3. draft or rewrite the section,
4. update the paper-level claim-evidence map after each section.

Keep terminology, contribution wording, and figure references stable across sections.

### Phase 5: Figures and Paper Artifacts

Produce the requested paper package:

1. finalize the figure set needed for the paper story,
2. prefer LaTeX-first artifacts,
3. produce PDF output when requested,
4. if exact quantitative details are still missing, surface them explicitly instead of
   inventing them.

This phase exists to make sure the user gets a usable paper package rather than only
raw prose.

### Phase 6: Review and Polish Loop

Run a final paper-level review pass before handoff:

1. reviewer-facing critique,
2. logic and claim-support check,
3. final polish pass for wording and flow.

Use `research-paper-writing` for the polish pass instead of re-implementing a second
writing guide here.

### Optional Phase 7: NotebookLM Branch

Only run this branch when the user explicitly asks for it.

Allowed uses:

1. alternative teaser or overview graphics,
2. slide decks,
3. other NotebookLM-generated communication assets tied to the current paper package.

Rules:

1. keep this branch non-blocking,
2. do not let NotebookLM outputs silently change the paper's core claims,
3. finish the main paper path first unless the user explicitly wants draft-quality
   assets early.

## Routing Rules

1. If the user asks only for section writing or paragraph flow, use
   `research-paper-writing` directly.
2. If the user already has a full draft and mainly wants paper-level critique, jump to
   the review and polish phases.
3. If the user wants both paper and slides, finish the paper package first, then branch
   to NotebookLM.
4. Keep this skill focused on orchestration. Put long writing rules in
   `research-paper-writing`; put presentation asset generation in `notebooklm`.

## Output Contract

When this skill is used, the response should make the current paper package explicit:

1. `workflow_state`: what phase the work is in and why,
2. `claim_gate`: supported / partial / unsupported claims,
3. `paper_plan`: thesis, outline, figure plan, deliverables plan,
4. `paper_package`: what was produced (`sections`, `figures`, `latex`, `pdf`,
   optional NotebookLM assets),
5. `review_summary`: major risks remaining, what was polished, and what still blocks
   submission quality.

## Guardrails

1. Do not overclaim beyond available evidence.
2. Prefer a smaller stable paper story over a broad fragile one.
3. Keep the orchestrator thin; reuse the narrower companion skills instead of cloning
   their instructions.
4. Prefer LaTeX and PDF as the main deliverables when the user asks for a full paper.
5. Treat the NotebookLM branch as optional output generation, not as the source of the
   paper's scientific claims.

## Example Prompts

1. `Use the research-paper-workflow skill to turn this experiment report into a paper plan, section drafts, figures, LaTeX, and PDF.`
2. `Use research-paper-workflow on this repo and get me to a reviewer-ready paper package.`
3. `Use research-paper-workflow to plan, write, review, and polish this draft, then generate optional NotebookLM slides.`
