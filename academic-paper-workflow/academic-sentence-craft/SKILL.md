---
name: academic-sentence-craft
description: Sentence-level English academic writing craft for research papers. Use when Codex needs to diagnose, teach, or revise awkward academic-paper sentences, sentence logic, subject-verb choice, clause placement, information packaging, result sentences, contribution sentences, gap sentences, comparison sentences, or non-native English phrasing. Especially useful when the user says a sentence feels unnatural, asks how to write better academic English sentences, wants reusable sentence patterns from strong papers, or needs prose that reads like ML/CV/NLP conference writing. Do not use as the primary skill for paper story/section logic, reviewer argument design, LaTeX compilation, venue formatting, citation checks, or broad submission review.
---

# Academic Sentence Craft

## Purpose

Use this skill to improve the internal logic and English expression of academic-paper sentences. Focus on how a sentence is built: what the subject is, what action the verb carries, where conditions and clauses are placed, how evidence connects to interpretation, and why a sentence feels natural or awkward to an expert reader.

This skill is intentionally narrower than paper-level writing skills. It does not decide the paper story, section order, or claim-evidence strategy. It also does not perform LaTeX engineering, bibliography repair, compilation, or venue-format checks.

## Boundary

Use this skill for:

- Revising awkward English sentences in abstracts, introductions, related work, methods, experiments, analyses, conclusions, limitations, and captions.
- Explaining why a sentence feels unnatural even when grammar is technically correct.
- Turning literal translation, loose academic prose, or AI-like phrasing into precise research prose.
- Producing reusable sentence patterns by function: problem, gap, contribution, method, result, interpretation, comparison, limitation, and conclusion.
- Teaching sentence-level academic writing through before/after examples and compact rules.

Prefer other skills when the request is mainly about:

- Paper story, section function, paragraph role, reviewer-facing narrative, or claim-evidence alignment: use `research-paper-writing`.
- Existing `.tex` source safety, compilation, formatting, citations, table/figure checks, or source-aware line comments: use `latex-paper-en`.
- Peer-review simulation, pass/fail readiness, or major/minor review findings: use `paper-audit`.

If a request spans both paper logic and sentence craft, first stabilize the paper/paragraph message with the relevant paper-writing skill, then use this skill to revise sentence construction.

## Workflow

1. Identify the sentence function before rewriting.
   Decide whether the sentence defines a problem, states a gap, introduces a contribution, explains a method, reports a result, interprets evidence, compares methods, states a limitation, or closes a section.

2. Diagnose the awkwardness by sentence mechanics.
   Check subject choice, verb strength, modifier placement, clause load, noun-phrase density, preposition chains, vague pronouns, unnecessary passive voice, overused `show`, and unsupported interpretation.

3. Preserve the scientific claim.
   Do not invent methods, results, citations, baselines, motivations, or evidence. If the original claim is ambiguous, propose a conservative rewrite and flag the ambiguity.

4. Rewrite at the smallest useful unit.
   Prefer sentence-level or two-sentence rewrites. Split overloaded sentences when one sentence carries multiple functions. Combine choppy sentences only when their logical relation is clear.

5. Explain the move, not just the correction.
   For each important rewrite, state what changed: subject, verb, clause order, information focus, contrast, result-to-interpretation link, or tone.

6. Provide reusable patterns when helpful.
   Give function-specific templates only after showing how they apply. Avoid dumping generic phrase lists without diagnosing the user's sentence.

## Sentence Function Router

Use the sentence function to choose the default structure:

- Problem sentence: `X requires Y because Z` or `X remains challenging because Y`.
- Gap sentence: `Existing work addresses A, but leaves B unresolved`.
- Contribution sentence: `We introduce X, a Y that Z`.
- Definition sentence: `We define X as Y, where Z`.
- Method sentence: `X does Y by Z` or `Rather than A, X B`.
- Mechanism sentence: `By doing X, the method enables Y`.
- Experiment sentence: `We evaluate X on Y under Z`.
- Result sentence: `X improves/drops from A to B, indicating Y`.
- Comparison sentence: `Compared with A, X achieves Y while preserving Z`.
- Limitation sentence: `This study focuses on X and does not examine Y`.
- Conclusion sentence: `These findings suggest that X, but Y remains unresolved`.

For detailed patterns and anti-patterns, load `references/sentence-patterns.md`.

## Diagnostic Labels

When reviewing prose, use concise labels:

- `WEAK SUBJECT`: The sentence starts from a vague holder such as `this`, `it`, `there`, `the ability`, or `the problem` when a concrete research object should be the subject.
- `WEAK VERB`: The main verb is too generic, often `show`, `use`, `make`, `do`, `have`, `include`, or `study`.
- `LOOSE PREPOSITIONS`: The sentence relies on stacked prepositional phrases such as `for X in Y with Z of A`.
- `CLAUSE LOAD`: The sentence has too many subordinate clauses or competing conditions.
- `MISPLACED FOCUS`: The important information appears at the end as an afterthought or in a weak subordinate phrase.
- `RESULT WITHOUT INTERPRETATION`: The sentence reports numbers without explaining what they mean.
- `INTERPRETATION WITHOUT EVIDENCE`: The sentence makes an implication stronger than the reported evidence supports.
- `TRANSLATIONESE`: The sentence is grammatical but follows Chinese-style information order or uses unnatural collocations.
- `FORMULAIC REPETITION`: Adjacent sentences repeat the same skeleton, such as `This setting mainly tests...`.

## Output Formats

For targeted revision, use:

```text
Original:
[sentence]

Issue:
[diagnostic label] - [one-sentence reason]

Revised:
[replacement sentence]

Why it works:
[sentence-level explanation]
```

For multiple sentences, use a compact table:

```text
Function | Original problem | Revised sentence | Sentence move
```

For teaching requests, group patterns by sentence function and include one natural example per pattern. Keep examples domain-generic unless the user provides a domain.

## Style Rules

- Prefer precise common verbs over decorative academic verbs.
- Keep the main claim in the main clause.
- Use `we` for author actions: `we introduce`, `we evaluate`, `we find`.
- Use passive voice when the process or artifact is more important than the actor: `Samples are filtered...`.
- Use `which`, `where`, and participial phrases to attach explanation, not to hide the main claim.
- Use short sentences for key findings and long sentences only when the internal relation is clear.
- Use hedging for interpretations: `suggests`, `indicates`, `may`, `is consistent with`.
- Avoid vague `this` unless followed by a clear noun: `this result`, `this gap`, `this setting`, `this design`.
- Do not replace every simple word with a formal synonym; stronger academic writing is usually more precise, not more ornate.

## Reference

Load `references/sentence-patterns.md` when the task asks for reusable templates, broad sentence-level teaching, or a systematic rewrite across many sentence functions.
