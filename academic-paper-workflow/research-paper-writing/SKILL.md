---
name: research-paper-writing
description: Content-level research paper writing coach for ML/CV/NLP-style manuscripts, focused on paper story, section logic, paragraph flow, claim-evidence alignment, and reviewer-facing presentation. Use when the user asks to draft, rewrite, or reason about Abstract, Introduction, Related Work, Method, Experiments, Conclusion, figures/tables, or paper narrative without needing source-aware LaTeX/Typst compilation, formatting, citation verification, or submission-gate review. Prefer format-specific skills such as latex-paper-en, typst-paper, or latex-thesis-zh when an existing .tex/.typ thesis or paper project is present and the task involves source files, build errors, venue formatting, bibliography, labels, macros, or syntax preservation. Prefer paper-audit when the user wants reviewer-style critique, pass/fail readiness, peer-review reports, or blocker triage rather than direct rewriting.
---
# Research Paper Writing

## Overview

Use this skill to rewrite a research paper into a reviewer-friendly, high-clarity draft.
Prioritize first-impression quality (figures/tables/layout), logical flow, and evidence-backed claims.

## Routing Boundary

This skill is the content-writing layer. It should handle the intellectual shape of a paper: the central story, section function, paragraph roles, contribution framing, claim-evidence alignment, and prose proposals.

Prefer the newly installed academic-writing skills when the task is tied to a concrete source project:

- Use `latex-paper-en` for existing English `.tex` conference or journal papers, especially when preserving LaTeX commands, compiling, checking venue format, validating BibTeX/Biber, reviewing tables/figures/pseudocode, or making source-aware comments.
- Use `typst-paper` for existing `.typ` papers, especially when preserving Typst syntax, labels, citations, math, bibliography files, or export behavior.
- Use `latex-thesis-zh` for existing Chinese master's or doctoral `.tex` theses, especially for GB/T 7714, school templates, chapter structure, thesis-specific abstract/literature-review logic, and Chinese academic title or de-AI checks.
- Use `paper-audit` when the user asks for review rather than rewriting: peer-review simulation, submission readiness, pass/fail gate decisions, blocker triage, major/minor issues, or re-audit after revision.
- Use `bib-search-citation` when the main task is finding papers, validating citations, repairing `.bib` entries, or checking reference metadata.

If a request could use both this skill and a format-specific skill, use the format-specific skill first for source safety and mechanical checks, then apply this skill only to the prose or argument-level rewrite.

## Core Workflow

1. Clarify the paper story before sentence-level edits.
2. Use section-specific guidance in `references/`.
3. Before choosing a table, figure, or prose-only treatment, identify the reader task and map the information to the clearest representation.
4. Rewrite paragraph-by-paragraph with one message per paragraph.
5. Run reverse outlining after writing each section.
6. Check every major claim in Abstract/Introduction against experimental evidence.
7. Run final-paper adversarial review with `references/paper-review.md`.

## Global Principles

1. Keep one paragraph for one message only.
2. State the paragraph message in the first sentence.
3. Make nouns self-contained; define new terms before reusing them.
4. Maintain sentence-to-sentence flow (cause, contrast, consequence, or refinement).
5. Iterate with adversarial self-review: read as a skeptical reviewer.
6. Treat visual quality as core content, not decoration.
7. Use a clean teaser and pipeline figure.
8. Use readable, minimal-ink tables.
9. Match each information type to the clearest visual form instead of defaulting to tables.
10. Keep formatting consistent and tidy.

## Transferable Paper-Writing Methodology

Use these rules across method papers, benchmark papers, dataset papers, system papers, analysis papers, rebuttals, and technical reports. Do not overfit the writing strategy to one paper type.

### 1. Start From The Center Sentence

Before drafting or revising, compress the paper into one sentence:

`We study [problem], propose/show/analyze [main idea], and demonstrate [main finding].`

Adapt the sentence to the paper type:

- Method paper: `We study [limitation], propose [method], and show that it improves [target capability] under [setting].`
- Analysis paper: `We study whether [models/systems] exhibit [behavior], and show [main finding] through [analysis method].`
- Dataset/benchmark paper: `We introduce [resource] for studying [problem], and show that current models struggle with [key challenge].`
- System paper: `We build [system] to support [task/user], and show that it improves [quality/efficiency/reliability].`

Every section and paragraph should support the center sentence by clarifying the problem, method/resource, evidence, or implication.

### 2. Give Each Paragraph One Job

A paragraph should perform one clear function: define the problem, motivate importance, identify a gap, describe a design choice, report a result, explain a result, or state a limitation. If the paragraph performs several unrelated jobs, split it or rewrite it.

Use this paragraph test:

1. What should the reader remember after this paragraph?
2. Does the first sentence state that message?
3. Does each following sentence explain, support, contrast, or refine that message?
4. Can any sentence be removed without losing the paragraph's function?

### 3. Fix Logic Before Sentences

Revise in this order:

1. Paper story and center sentence.
2. Section roles.
3. Paragraph roles and order.
4. Claim-evidence alignment.
5. Sentence clarity.
6. Terminology, captions, tables, references, and formatting.

Do not polish sentences before the logical structure is stable. A fluent sentence that supports the wrong story still weakens the paper.

### 4. Write Sections By Function

Use the function of each section to decide what to include.

- Abstract: problem, gap, core contribution, main evidence, implication.
- Introduction: define the problem, explain why it matters, show why existing work is insufficient, state the contribution, summarize the main findings.
- Related Work: organize by difference dimensions, not by a list of papers.
- Method: explain why each component exists, what it does, and what output it provides to the next step.
- Experiments: write around questions, not around tables. Each experiment should answer one question.
- Analysis: explain the main experiment's unresolved questions; avoid unrelated extra experiments.
- Conclusion: recover the problem, main finding, deeper explanation, and implication; do not introduce new claims.
- Limitations: state concrete boundaries briefly; do not write a defense or a future-work essay.
- Appendix: support reproducibility and extra evidence; order appendix sections by first mention in the main text.

### 4.1 Keep Abstract Results Selective

The abstract may include results, but it should not become an experiment summary. Report only the most important result or trend needed to support the paper's main claim. If the paper introduces a dataset, benchmark, resource, or system, reserve abstract space for the contribution itself: data scale, data source, covered categories, task scope, and why the resource matters. Move detailed per-setting numbers, ablations, and secondary findings to the main experiments.

Use this check:

1. Does each number in the abstract directly support the main claim?
2. Can several detailed numbers be replaced by one key number or a short trend?
3. For resource papers, does the abstract clearly say what was collected, how much was collected, where it came from, and what categories or phenomena it covers?

### 5. Prefer Concrete Actions Over Abstract Labels

When possible, write what the model/system/method actually does. Avoid replacing concrete behavior with vague labels such as `capability`, `mechanism`, `paradigm`, `signal`, `alignment`, or `understanding` unless the term is defined and needed.

Prefer:

`The model selects the correct answer from options but fails to generate the answer without options.`

Over:

`The model shows a gap between recognition and generation capability.`

Use task names, input/output behavior, comparison targets, and measured results when they are clearer than abstractions.

### 6. Use Simple, Accurate Words

Avoid difficult or decorative words when a common word is more precise. Typical replacements:

- `utilize` -> `use`
- `facilitate` -> `help`
- `demonstrate` -> `show`
- `substantial` -> `large` or `clear`
- `salient` -> `key`
- `leverage` -> `use`
- `delve into` -> `analyze` or `study`

Do not remove technical terms that are necessary. Define them once and reuse them consistently.

### 7. Keep Terminology Stable

One concept should have one name across the title, abstract, figures, tables, main text, appendix, prompts, and code-facing descriptions. Do not vary core terms for style. If the paper uses `Hint Category`, avoid later switching to `category hint`, `semantic category`, or `tip_cate` unless explicitly explaining an implementation variable.

### 8. Make Figures And Tables Do Argument Work

Each figure or table should support a specific claim. Before presenting experimental results, dataset properties, analyses, or examples, run a representation-choice check:

1. What should the reader learn first: exact values, ranking, magnitude, trend, distribution, correlation, workflow, taxonomy, or qualitative failure mode?
2. What comparison should be visually effortless: across rows, across columns, against a baseline, across time, or between groups?
3. Would the information be clearer as prose, a table, a chart, a pipeline diagram, a case grid, or an appendix artifact?

Use this mapping as the default starting point:

- Exact lookup, many values, reproducibility details, or protocol settings -> table.
- Ranking or magnitude comparison across categories -> sorted bar chart, dot plot, or lollipop chart; use horizontal bars for long labels.
- Gains/losses against a baseline or zero point -> deviation bar, delta bar, dumbbell plot, or arrow plot.
- Change over time, training dynamics, or scaling behavior -> line chart, slope chart, or small multiples.
- Distribution, variance, or spread -> histogram, box plot, violin plot, ridge plot, or beeswarm.
- Correlation or relationship between two variables -> scatter plot; add a trend line only when the pattern justifies it.
- Part-to-whole composition -> stacked bar, 100% stacked bar, treemap, or simple pie/donut only for very few parts.
- Process, annotation pipeline, model pipeline, or task flow -> flow diagram or pipeline figure.
- Taxonomy, task schema, or benchmark structure -> structured diagram with clear grouping and labels.
- Qualitative examples, error modes, or model responses -> compact case grid with consistent fields.

Apply visual design rules:

1. Prefer common scales, aligned positions and lengths over angles, areas, 3D shapes or decorative encodings.
2. Use restrained, color-blind-aware palettes; keep most elements neutral and reserve one accent color for the key comparison.
3. Avoid gradients, heavy borders, chart junk, redundant legends and oversized in-figure titles.
4. Label sub-settings explicitly, for example `PunMemeCN (hard)` or `MultiMM (Chinese)`, when a row is not the full dataset name.
5. Put exact values on the chart only when they help the reader avoid looking back to the text.
6. Move exhaustive tables to the appendix when the main text only needs the trend or ranking.

Captions should usually state:

1. What the figure/table shows.
2. The key trend, contrast, or reading instruction.
3. Any abbreviations, sub-settings, units, or missing-result conventions needed to read it.

Do not use captions only as labels. Do not repeat the full body-text explanation in the caption. When confident, proactively recommend a better representation to the user and explain why it serves the paper claim better. When uncertain, consult reliable visualization references such as the Financial Times Visual Vocabulary, Datawrapper Academy, Nielsen Norman Group, or perception research before choosing.

### 9. Report Results As Answers To Questions

For every experiment paragraph, identify the question first:

- Does the method improve the main task?
- Which component matters?
- Does the result generalize?
- Where does the method fail?
- What explains the main trend?

Then report the setting, result, and implication. A number is useful only when the text explains what question the number answers.

### 10. Use Revision Rounds With A Single Target

Avoid editing everything at once. Use focused rounds:

1. Structure and paper story.
2. Introduction and contribution logic.
3. Method clarity.
4. Experiment and analysis interpretation.
5. Terminology unification.
6. Figure/table captions.
7. Appendix reproducibility.
8. Final compression, grammar, references, and formatting.

After each round, report exactly what changed, why it changed, what was verified, and what remains unverified.

### 11. Final Self-Review Questions

Before delivery or submission, answer these questions as a skeptical reviewer:

1. What problem does the paper solve, in one sentence?
2. Why is the problem important now?
3. What is the clearest difference from prior work?
4. Does every major claim in the Abstract and Introduction have evidence?
5. Are the method/resource/analysis details reproducible?
6. Do figures and tables have self-contained captions?
7. Are core terms used consistently everywhere?
8. Are limitations concrete and not defensive?
9. Are references real, relevant, and formatted consistently?
10. Does the conclusion avoid new claims?


## Additional Writing Preferences

Apply these preferences when they do not conflict with clarity or paper logic:

1. Prefer concrete nouns over pronouns when a pronoun could make the sentence unclear. Do not mechanically ban `it`, `this`, `they`, or `these`; use them only when the reference is obvious. Repeat the key noun when repetition makes the claim clearer.
2. Use quotation marks sparingly.
3. Use colons sparingly.
4. Avoid the `, and` construction when a cleaner sentence structure is available.

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

## Section Guides

Load only the needed section file:

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
3. Perform adversarial writing: review as a skeptical reviewer and resolve every high-risk question.
4. Revise until major rejection risks are explicitly addressed.

## Execution Rules

1. Build a mini-outline before drafting prose.
2. For each subsection, explicitly include motivation, design, and technical advantage when applicable.
3. Avoid writing style that looks like incremental patching of a naive baseline.
4. Keep terminology stable across the full paper.
5. If a claim cannot be supported by results, weaken or remove the claim.
6. Before finalizing, append and answer a five-dimension self-review question list, then revise the paper based on unresolved items.
7. Do not load all section references (Introduction/Abstract/Related Work/Method/Experiments/Conclusion) at once; load only the specific section guide needed for the current edit target.

## Output Contract

When asked to rewrite or draft sections, return:

1. A compact section outline (3-7 bullets).
2. Revised paragraphs with explicit paragraph roles (opening/challenge/method/advantage/evidence/limitation).
3. A short self-review checklist covering clarity, flow, terminology consistency, unsupported claims, and missing evidence.
4. A claim-evidence map for each major claim in the revised text using `Claim: ... | Evidence: ... | Status: supported/needs evidence`.

