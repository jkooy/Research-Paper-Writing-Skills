# Agent-Style Bridge for Paper Writing

Use this shared reference as a thin style gate on top of the existing paper-writing
skills. It does not replace section structure or reviewer-facing logic; it sharpens the
final prose so the paper reads like formal technical writing instead of default LLM text.

## What This Bridge Is For

Use it when drafting or polishing:

1. Abstracts and introductions that are at risk of overclaiming.
2. Related-work sections that summarize papers without precise support.
3. Method and experiment sections that drift into vague nouns or overloaded sentences.
4. Final review passes that need to remove generic LLM writing patterns.

## Hard Constraints

1. Support factual claims with a real citation or concrete evidence from the paper.
2. Never fabricate citations, venues, years, or quantitative details.
3. Calibrate verbs to the available support. Use `suggests`, `indicates`, or `is
   consistent with` when the evidence is limited; reserve stronger verbs for stronger
   support.
4. If a sentence depends on hidden context, rewrite it so a reviewer can parse it in one
   pass.

## Core Prose Rules Adapted for Paper Work

### Reader Clarity

1. Name concrete objects instead of abstract placeholders such as `factors`, `aspects`,
   or `various settings` when the paper can be specific.
2. Keep related words together. Avoid long parenthetical detours between subject and verb.
3. Put the most important new information near the end of the sentence.
4. Split long sentences before they exceed the reader's working memory.
5. Cut filler phrases such as `in order to`, `it is worth noting that`, or `we can see
   that` unless they add real meaning.

### Academic Style Hygiene

1. Keep terms, abbreviations, metric names, and dataset names stable across the paper.
2. Prefer full forms over contractions in the final paper.
3. Use bullets only for genuine lists. Keep connected argumentation in paragraphs.
4. Avoid repeated sentence starts and empty transitions such as `Additionally`,
   `Furthermore`, or `Moreover` when the logical relation is obvious from the content.
5. Do not end every paragraph with a sentence that merely restates the paragraph's point.

### Section-Specific Guidance

#### Abstract

1. Every sentence should earn its place.
2. The contribution claim should be the smallest honest version supported by the paper.
3. Quantitative claims should reference the exact comparison or evidence available in the
   paper.

#### Introduction

1. State the problem, gap, and contribution in concrete terms.
2. Remove motivational filler that does not change the technical framing.
3. Keep the contribution wording aligned with what later sections actually show.

#### Related Work

1. Use citations to support both factual statements and comparisons.
2. Describe the relationship between prior work and the current paper precisely
   (`studies`, `benchmarks`, `proposes`, `focuses on`, `differs by`) instead of with vague
   praise.
3. If a citation is uncertain, mark it for verification instead of guessing.

#### Method and Experiments

1. Prefer exact nouns for datasets, metrics, checkpoints, and settings.
2. Keep notation and terminology stable across prose, figures, and tables.
3. Separate observation from interpretation when reporting results.

## Fast Final-Pass Checklist

Before handoff, scan for:

1. unsupported or weakly supported claims,
2. missing citations in factual or comparative statements,
3. terminology drift,
4. overlong sentences,
5. filler phrases,
6. repeated sentence openings,
7. bullet lists that should be prose.

## Attribution

This bridge adapts ideas from *The Elements of Agent Style*
(`https://github.com/yzhao062/agent-style`), CC BY 4.0, to the paper-writing workflow in
this repo. See `../NOTICE.md` for the attribution note.
