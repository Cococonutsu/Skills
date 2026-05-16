# Sentence Patterns For Academic Papers

Use these patterns to revise or teach sentence-level academic writing. They are generic and should be adapted to the user's field and evidence.

## Core Principle

A strong academic sentence usually has:

1. A concrete subject.
2. A precise main verb.
3. One main message.
4. Conditions or limitations placed where the reader needs them.
5. A clear link between evidence and interpretation when reporting results.

Do not make the sentence sound formal by adding abstract nouns. Make it stronger by making the action and relation clearer.

## Problem Sentences

Purpose: define what is hard or important.

Patterns:

- `X requires Y because Z.`
- `X remains challenging because Y.`
- `In X, models must Y before they can Z.`
- `The difficulty lies not in A alone, but in B.`

Avoid:

- `X is very important and challenging.`
- `There are many problems in X.`
- `X has attracted much attention.`

Example:

- Weak: `This task is difficult for current models.`
- Strong: `This task requires models to combine visual evidence with task-specific symbolic reasoning, which current systems often handle separately.`

## Gap Sentences

Purpose: distinguish the paper from prior work without dismissing it.

Patterns:

- `Existing work primarily addresses A, leaving B largely unexplored.`
- `While prior studies have examined A, they do not test whether models can B.`
- `These benchmarks capture A, but they do not isolate B.`
- `Unlike A, which focuses on B, our setting requires C.`

Avoid:

- `Few works study X.`
- `No one has studied X.`
- `Previous works are insufficient.`

Example:

- Weak: `Previous works only cover part of the problem.`
- Strong: `Previous benchmarks evaluate text-only ambiguity, but they do not test whether models can ground visual cues before applying phonological or symbolic mappings.`

## Contribution Sentences

Purpose: state what the paper introduces or proves.

Patterns:

- `We introduce X, a Y that Z.`
- `We propose X to Y.`
- `We present X for evaluating whether Y.`
- `Our main contribution is X: a Y that Z.`

Avoid:

- `We propose X for Y with Z.`
- `We make the following contributions. We propose...` when the sentence can be more direct.
- Overusing `novel`, `effective`, or `comprehensive` without concrete support.

Example:

- Weak: `We propose a benchmark for this problem with three settings.`
- Strong: `We introduce a benchmark that evaluates the target ability under three progressively less constrained settings.`

## Definition Sentences

Purpose: name a concept and define its scope.

Patterns:

- `We define X as Y.`
- `In this work, X refers to Y rather than Z.`
- `X denotes Y, where Z specifies A.`
- `We categorize examples according to whether A and B share C.`

Avoid:

- Changing terminology for style.
- Defining a term after using it several times.
- Using a capitalized term when a common noun is enough.

Example:

- Weak: `Type 1 has the same characters and pronunciation.`
- Strong: `Type 1 contains cases in which the source phrase and target answer share both form and pronunciation.`

## Method Sentences

Purpose: explain what the method or benchmark does.

Patterns:

- `X does Y by Z.`
- `X first A, then B.`
- `Rather than A, X B.`
- `By doing A, X enables B.`
- `This design separates A from B, allowing us to isolate C.`

Avoid:

- `We use X to do Y` when a more precise verb exists.
- Long chains of `and then and then`.
- Describing implementation details before the purpose is clear.

Example:

- Weak: `We use a script to assign the type by comparing the answers.`
- Strong: `A rule-based script assigns each type by comparing the source phrase and target answer at both the character and pronunciation levels.`

## Experiment Setup Sentences

Purpose: state what is evaluated and under what condition.

Patterns:

- `We evaluate X on Y using Z.`
- `This setting isolates A by removing B.`
- `To test whether A affects B, we compare X with Y.`
- `All models are evaluated under X; additional runs use Y when available.`

Avoid:

- Repeating `This setting mainly tests...` across several adjacent sentences.
- Hiding the evaluation contrast in a late prepositional phrase.

Example:

- Weak: `This setting mainly tests answer generation with hints.`
- Strong: `This setting tests whether partial constraints help models narrow the answer space during open-form generation.`

## Result Sentences

Purpose: report a result and make the trend legible.

Patterns:

- `X achieves A, outperforming Y by B.`
- `Accuracy drops from A to B, revealing C.`
- `Compared with A, X improves Y while preserving Z.`
- `The gains are concentrated in A, suggesting B.`
- `This trend is consistent across X and Y.`

Use interpretation verbs carefully:

- `shows` / `reveals`: direct empirical trend.
- `indicates` / `suggests`: plausible interpretation.
- `highlights`: importance or consequence.
- `validates`: evidence supports a design choice.
- `confirms`: use only when a prior expectation was stated.

Avoid:

- `The results are shown in Table X.`
- `Results show that X is better.`
- Reporting many numbers without saying what they mean.

Example:

- Weak: `The model performs much better in setting A than setting B.`
- Strong: `Accuracy drops sharply from the option-based setting to the open-form setting, revealing a gap between recognition and generation.`

## Interpretation Sentences

Purpose: explain what a result means without overclaiming.

Patterns:

- `This suggests that A, but does not imply B.`
- `These results indicate that X helps Y but does not resolve Z.`
- `One explanation is that X; however, Y remains possible.`
- `The pattern supports the view that X is a bottleneck.`

Avoid:

- Treating correlation as proof.
- Making a mechanistic claim from aggregate accuracy alone.
- Ending every result paragraph with `This shows the effectiveness of our method.`

Example:

- Weak: `This proves that the model understands the task.`
- Strong: `This suggests that the model can exploit the constrained answer space, but it does not establish reliable open-form reasoning.`

## Comparison Sentences

Purpose: contrast methods, tasks, datasets, or findings.

Patterns:

- `Compared with A, X achieves Y while requiring Z.`
- `In contrast to A, X does not rely on B.`
- `Unlike A, which assumes B, X allows C.`
- `A and B differ mainly in C.`

Avoid:

- `A is better than B` without dimension.
- `Compared to A, B is...` when the comparison target is not parallel.

Example:

- Weak: `Compared to previous benchmarks, our benchmark is harder.`
- Strong: `Compared with option-based benchmarks, this setting removes candidate answers and therefore tests open-form generation directly.`

## Limitation Sentences

Purpose: state scope without sounding defensive.

Patterns:

- `Our evaluation focuses on X and does not examine Y.`
- `A remaining limitation is that X.`
- `This analysis is limited to X, so it does not establish Y.`
- `Future work could test whether X extends to Y.`

Avoid:

- `Due to time and resource limitations...`
- Long future-work lists that dilute the actual limitation.
- Defensive claims that the limitation is unimportant.

Example:

- Weak: `There are some limitations in our work.`
- Strong: `Our evaluation considers final outputs only and does not verify whether intermediate reasoning steps are correct.`

## Conclusion Sentences

Purpose: close with the finding, not with vague optimism.

Patterns:

- `Overall, X shows that Y remains difficult under Z.`
- `These findings suggest that X, but Y remains unresolved.`
- `The results point to A as a key bottleneck for B.`
- `Current systems can A, but they still struggle to B.`

Avoid:

- `In the future, we will do more research.`
- `This work provides a foundation for future work` without saying what foundation.
- Introducing new claims in the conclusion.

Example:

- Weak: `This paper studies the problem and provides useful findings.`
- Strong: `These findings indicate that current systems can exploit constrained choices but still struggle with reliable open-form reasoning.`

## Common Sentence Problems And Fixes

### Vague `this`

Weak:

`This shows that the method works.`

Better:

`This improvement indicates that the added constraint helps the model narrow the search space.`

Rule: replace bare `this` with `this result`, `this gap`, `this setting`, `this design`, or a concrete noun phrase.

### Weak Main Verb

Weak:

`The table shows the results.`

Better:

`Table 2 summarizes accuracy across models and task settings.`

Rule: make the verb describe the table's function or the result's implication.

### Loose Prepositional Chain

Weak:

`We propose a benchmark for model ability in reasoning with images under different settings.`

Better:

`We introduce a benchmark that evaluates image-grounded reasoning under multiple answer constraints.`

Rule: turn stacked `for/in/with/under/of` phrases into a relative clause or a concrete verb.

### Overpacked Sentence

Weak:

`We evaluate many models on three settings and several prompts and show different results across types and analyze errors.`

Better:

`We evaluate models under three task settings and multiple prompting strategies. We then analyze how performance varies across example types and error modes.`

Rule: split when one sentence contains two or more independent functions.

### Formulaic Repetition

Weak:

`This setting tests A. This setting tests B. This setting tests C.`

Better:

`The first setting evaluates A under a constrained answer space. The second tests whether partial hints help B. The third isolates C by removing both options and hints.`

Rule: keep the parallel logic but vary the verb according to the actual function.

## Revision Checklist

Before finalizing a sentence, ask:

1. What function does this sentence serve?
2. Is the main actor or object the grammatical subject?
3. Does the main verb carry the intended action?
4. Is the key claim in the main clause?
5. Are conditions, contrasts, and limitations placed before the reader needs them?
6. Does a result sentence connect the number to its interpretation?
7. Is the wording precise without sounding inflated?
8. Would splitting or combining make the logic easier to read?
