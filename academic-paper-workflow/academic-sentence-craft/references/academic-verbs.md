# Academic Verb Choice For Research Papers

Use this reference when revising or teaching academic-paper sentences where the verb feels weak, repetitive, or imprecise. The goal is not to replace simple words with ornate synonyms. The goal is to make the verb mark the sentence function accurately.

## Core Principle

Academic verbs are functional signals. A reader should be able to infer whether a sentence is introducing a contribution, defining a concept, isolating an experimental factor, reporting a result, interpreting evidence, comparing methods, or limiting a claim from the verb itself.

Prefer precise common verbs over inflated verbs. For example, `reveal` is useful when a result exposes a pattern; `suggest` is useful when a result supports a cautious interpretation; `validate` is useful when evidence supports a design choice. Do not mechanically replace every `show`.

## Quick Diagnosis

If a draft overuses these verbs, check whether the sentence function is being blurred:

- `show`: may need `reveal`, `indicate`, `suggest`, `demonstrate`, `validate`, `support`, or `highlight`.
- `test`: may need `evaluate`, `assess`, `measure`, `compare`, `isolate`, or `ablate`.
- `use`: may need `adopt`, `apply`, `employ`, or a concrete action verb. Use `leverage` only when the sentence truly means exploiting a resource, advantage, or prior capability.
- `make`: may need `enable`, `allow`, `yield`, `produce`, or `lead to`.
- `give`: may need `produce`, `generate`, `recover`, `select`, `return`, or `yield`.
- `have`: may need `contain`, `include`, `comprise`, `exhibit`, or `achieve`.

## 1. Problem And Task Difficulty

Use these verbs to state what a task demands or exposes:

- `require`: the task needs a capability.
- `involve`: the task contains multiple operations or stages.
- `demand`: stronger than `require`; use sparingly.
- `pose`: the task creates a challenge.
- `expose`: an evaluation reveals a weakness.
- `depend on` / `hinge on`: success relies on a capability.
- `rely on`: a method or model uses a source of information.

Patterns:

```latex
X requires models to combine A with B.
X involves reasoning over A rather than simply recognizing B.
X poses a challenge because Y.
Success depends on the model's ability to recover A from B.
```

Examples:

```latex
Open-ended prediction requires the model to recover the target output without candidate choices.
```

```latex
The task involves both evidence extraction and symbolic mapping, making pure recognition insufficient.
```

Avoid vague versions:

```latex
X is difficult for current models.
X is a very challenging problem.
```

## 2. Related Work And Research Gap

Use these verbs to describe prior work accurately:

- `study`, `examine`, `investigate`: general research actions.
- `explore`: early or broad investigation.
- `address`: prior work tackles a problem.
- `focus on`: prior work centers on one aspect.
- `extend`: prior work expands a line of work to a new setting.
- `evaluate`, `benchmark`: prior work measures model behavior.
- `leave`, `overlook`, `do not address`, `do not evaluate`, `fail to isolate`: gap verbs.

Patterns:

```latex
Prior work has examined A, but has not evaluated B.
Existing benchmarks focus on A, leaving B largely unexplored.
Recent work extends A to B, but does not isolate C.
These studies address A in isolation rather than the full process of B.
```

Examples:

```latex
Existing benchmarks evaluate A in controlled settings, leaving B largely unexplored.
```

```latex
Recent studies extend A to multimodal settings, but they do not isolate the operation required for B.
```

Avoid:

```latex
Previous works only cover part of the problem.
No one has studied this problem.
```

## 3. Contributions And Paper Positioning

Use these verbs to state what the paper contributes:

- `introduce`: best for benchmarks, datasets, frameworks, taxonomies, resources.
- `present`: neutral and broad; useful for methods, systems, studies, or findings.
- `propose`: best for methods, algorithms, objectives, training strategies.
- `develop`: method/system/tool with implementation substance.
- `design`: task settings, model components, protocols, or principles.
- `construct`, `collect`, `curate`: datasets or corpora.
- `release`: public code, data, model, or benchmark.

Patterns:

```latex
We introduce X, a benchmark for evaluating Y.
We present X, a framework that integrates A with B.
We propose X, a method for improving Y.
We construct a dataset of N examples covering A, B, and C.
We design three settings to isolate A from B.
```

Examples:

```latex
We introduce a benchmark that evaluates the target ability under progressively weaker answer constraints.
```

```latex
We design three evaluation settings to separate answer recognition from open-form generation.
```

Notes:

- Do not overuse `propose` for datasets or benchmarks when `introduce` is more natural.
- Avoid unsupported adjectives such as `novel`, `effective`, and `comprehensive` unless the sentence states what makes the contribution novel, effective, or comprehensive.

## 4. Definitions, Taxonomies, And Annotations

Use these verbs to define scope and categories:

- `define`: assign meaning.
- `categorize`, `classify`: sort examples into groups.
- `partition`: split a set formally.
- `distinguish`: emphasize a difference.
- `assign`: map an instance to a label or type.
- `annotate`, `label`: human or automatic labeling.
- `encode`: represent information in a structure.
- `characterize`: describe properties systematically.
- `denote`: notation.

Patterns:

```latex
We define X as Y.
We categorize examples according to A.
The script assigns each example to one of three types.
This taxonomy distinguishes A from B.
X denotes Y, while Z denotes A.
```

Examples:

```latex
We categorize examples according to the relation between the source signal and the target output.
```

```latex
A rule-based script assigns each instance to one of three relation types.
```

Avoid:

```latex
Type 1 has...
This type is about...
```

Prefer:

```latex
Type 1 contains cases in which A and B share C.
```

## 5. Dataset Collection And Construction

Use these verbs to describe data work:

- `collect`: obtain raw data.
- `curate`: collect and select carefully.
- `filter`: remove unsuitable items.
- `sample`: choose examples by a rule or distribution.
- `annotate`: add labels or explanations.
- `verify`: check correctness.
- `validate`: verify through a stronger protocol or evidence.
- `construct`: build a field, phrase, dataset, or benchmark.
- `assemble`: combine fields into final examples.
- `align`: match items across positions, modalities, or labels.
- `normalize`: standardize format.
- `retain`: keep selected items.
- `split`: divide into train/test/dev.

Patterns:

```latex
We collect X from Y.
Annotators align A with B.
We filter out examples that lack C.
We assemble the final cases from A, B, and C.
Annotators verify whether each sample satisfies the required fields.
```

Examples:

```latex
We collect raw examples from online sources and manually verify the intended answers.
```

```latex
Annotators align each visual cue with the corresponding target position before constructing the intermediate phrase.
```

Notes:

- Use `verify` rather than `check` in formal paper prose.
- Use passive voice naturally when the sample is the topic: `Samples with inconsistent fields are corrected before inclusion.`

## 6. Method Mechanism And Process

Use these verbs to describe what the method, model, or pipeline does:

- `extract`: take information from input.
- `identify`: locate or recognize relevant items.
- `map`: establish correspondence between spaces.
- `convert`: change one representation into another.
- `recover`: infer a target that is not directly given.
- `infer`: derive an answer or property from evidence.
- `generate`: produce text, images, labels, or outputs.
- `select`: choose from options.
- `combine`, `integrate`: merge information sources.
- `align`: match elements across modalities or positions.
- `preserve`: keep a property unchanged.
- `constrain`: restrict the search space.
- `remove`: take away support or information.
- `isolate`: separate one factor or ability from others.
- `expose`: make a failure or bottleneck visible.
- `decompose`: split into subproblems.
- `aggregate`: combine multiple outputs or features.
- `retain`: keep selected information.
- `replace`: substitute one component for another.
- `transform`: convert structure or representation.

Patterns:

```latex
The model extracts A from the input.
The model maps A to B.
The method converts A into B.
The setting removes A to isolate B.
The design constrains the answer space.
The model recovers the intended answer from A.
```

Examples:

```latex
The model first extracts relevant cues, maps them to intermediate representations, and then recovers the intended output.
```

```latex
The open-ended setting removes candidate choices to isolate direct answer generation.
```

Avoid:

```latex
The model gives the correct answer.
```

Prefer one of:

```latex
The model recovers the intended answer.
The model generates the target answer.
The model selects the correct option.
The model converts the intermediate phrase into the target answer.
The model completes the final mapping step.
```

## 7. Experimental Setup And Protocol

Use these verbs to describe evaluation precisely:

- `evaluate`: formally measure models or methods.
- `test whether`: examine a specific hypothesis.
- `assess`: measure an ability, effect, or impact.
- `measure`: compute a metric.
- `compare`: contrast systems or settings.
- `benchmark`: evaluate systematically over tasks/models.
- `report`: present metrics or results.
- `adopt`: use an established setup, metric, or baseline.
- `follow`: use prior protocol.
- `control`: keep a variable fixed.
- `isolate`: design an experiment to separate a factor.
- `vary`: change one factor.
- `ablate`: remove or modify a component to test contribution.

Patterns:

```latex
We evaluate models on X.
We test whether A helps B.
We assess the effect of A on B.
We measure accuracy under three settings.
We compare X against Y.
We ablate A to isolate its contribution.
```

Examples:

```latex
We evaluate all models under three answer constraints.
```

```latex
We test whether auxiliary information improves unconstrained prediction.
```

```latex
We isolate the effect of candidate choices by comparing a choice-based setting with an open-ended setting.
```

Notes:

- `evaluate` is the default for formal model assessment.
- `test whether` is best when the sentence has a clear yes/no research question.
- `isolate` is best when explaining why an experimental setting exists.

## 8. Results And Evidence

Use result verbs according to evidence strength:

- `show`: neutral result verb.
- `reveal`: a clear pattern, gap, or bottleneck becomes visible.
- `indicate`: evidence points to an interpretation.
- `suggest`: cautious interpretation.
- `demonstrate`: stronger evidence of capability or effect.
- `validate`: evidence supports a design choice or hypothesis.
- `confirm`: evidence supports a previously stated expectation.
- `support`: evidence is consistent with a claim.
- `highlight`: emphasize importance or consequence.
- `expose`: reveal a limitation or weakness.
- `explain`, `account for`: connect cause and observation.

Patterns:

```latex
The results reveal a large gap between A and B.
These results indicate that A helps B but does not resolve C.
This pattern suggests that X is the main bottleneck.
The improvement validates the design choice.
The failure cases highlight the limitation of current models.
```

Examples:

```latex
The results reveal a large gap between constrained recognition and open-ended generation.
```

```latex
The smaller gains on broad benchmarks suggest that the benefit is strongest for closely related tasks.
```

Decision guide:

- Use `reveal` for directly observed trends.
- Use `indicate` or `suggest` for interpretation.
- Use `validate` when the result supports a design.
- Use `highlight` for significance.
- Avoid `prove` unless the claim is formal or mathematically established.

## 9. Performance Change And Comparison

Use these verbs to describe metric movement and ranking:

- `achieve`, `obtain`, `reach`: get a score.
- `outperform`, `exceed`: beat a baseline.
- `match`: equal a baseline.
- `maintain`, `preserve`: keep performance or capability.
- `improve`, `increase`: go up.
- `reduce`, `decrease`: go down when lower is better or quantity is reduced.
- `drop`, `degrade`: performance becomes worse.
- `narrow`, `widen`: gaps become smaller or larger.
- `saturate`: improvement plateaus.
- `lag behind`: remain worse than a baseline.

Patterns:

```latex
X achieves the highest accuracy.
X outperforms Y by N points.
Accuracy drops from A to B.
The method maintains performance while reducing cost.
The gap widens in the harder setting.
Performance saturates after X.
```

Examples:

```latex
The strongest open-source model achieves the highest accuracy in the constrained setting.
```

```latex
Accuracy drops sharply when candidate choices are removed.
```

```latex
Auxiliary constraints improve generation accuracy but do not close the gap to choice-based recognition.
```

Notes:

- Use `achieves` for performance claims and rankings.
- Use `drops` for degradation under harder settings.
- Use `narrows` or `widens` for gap analysis.

## 10. Cross-Benchmark Generalization And Transfer

Use this section when a model is trained or tuned on one dataset, task, or domain and then evaluated directly on external benchmarks or out-of-domain test sets.

Default recommendation:

Use `generalization` as the main term for this scenario unless the paper is explicitly framed as transfer learning. If a model is trained or fine-tuned on one benchmark and then directly evaluated on other benchmarks, the cleanest wording is usually `generalization to external benchmarks`, `cross-benchmark generalization`, or `generalization gains on external benchmarks`.

Use `transfer` only for mechanism or source-to-target benefit sentences, especially when you want to say that source-task supervision improves a target task. In that case, write `positive transfer`, `transfer to related tasks`, or `limited transfer to broad benchmarks`. Do not make `transfer` the dominant section-level term unless the experiment is designed as a transfer-learning study.

Recommended wording by paper location:

| Paper location | Recommended term | Use it to say | Example |
| --- | --- | --- | --- |
| Section title | `Generalization to Related Benchmarks` | The section tests whether the trained model works outside the source benchmark. | `Generalization to Related Benchmarks` |
| Section title, broader | `Cross-Benchmark Generalization` | The section compares performance across external benchmarks. | `Cross-Benchmark Generalization` |
| Experiment setup | `evaluate generalization` | You directly test on external datasets without more training. | `We evaluate generalization by testing the fine-tuned model on external benchmarks.` |
| Figure caption | `generalization gains` | The bars/numbers are improvements on external benchmarks. | `Bars show generalization gains over the base model.` |
| Result sentence | `generalizes to` | The model performs well on related benchmarks. | `The model generalizes to related benchmarks, with the largest gains on tasks closest to the source task.` |
| Mechanism interpretation | `positive transfer` | Training on the source task helped the target task. | `This pattern suggests positive transfer from source-task supervision to related target tasks.` |
| Scope limitation | `limited transfer` | Gains do not extend strongly to broad or distant benchmarks. | `The smaller gains on broad benchmarks indicate limited transfer beyond the source task family.` |
| Negative result | `negative transfer` | Source training hurts target performance. | `Training on the source task causes negative transfer on the target benchmark.` |

Use these verbs and nouns carefully:

- `generalize`: the method performs beyond the source data or setting.
- `generalization`: the ability or evaluation focus.
- `generalization gains`: improvements on external or held-out benchmarks.
- `generalization evaluation`: an evaluation designed to test performance beyond the original benchmark.
- `transfer`: a benefit, signal, or capability carries from source to target.
- `transfer evaluation`: an evaluation framed around source-to-target benefit.
- `positive transfer`: the source training improves target performance.
- `negative transfer`: the source training hurts target performance.
- `transfer to`: the method or learned capability is applied to a target task/domain.
- `improve on`, `boost`, `yield gains on`: describe metric improvements on target benchmarks.

Patterns:

```latex
We evaluate generalization by testing the fine-tuned model on external benchmarks.
The fine-tuned model generalizes to related benchmarks, yielding consistent gains.
The gains are largest on benchmarks closest to the source task.
This pattern suggests positive transfer from source-task supervision to related target tasks.
The method transfers less effectively to broad general-purpose benchmarks.
```

Preferred mini-paragraph:

```latex
We evaluate cross-benchmark generalization by directly testing the fine-tuned model on external benchmarks without additional training. The model improves on all related benchmarks, with the largest gains on tasks closest to the source task. This pattern suggests positive transfer from source-task supervision, while the smaller gains on broad benchmarks indicate limited transfer beyond the source task family.
```

This paragraph uses `generalization` for the evaluation frame and `transfer` for the interpretation of why gains appear.

Bad and better:

| Avoid | Better | Why |
| --- | --- | --- |
| `Generalization transfer results are shown in Figure X.` | `Figure X shows generalization gains on external benchmarks.` | `generalization transfer` is an unclear compound. |
| `The model has good transfer on other benchmarks.` | `The model generalizes well to related benchmarks.` | The sentence reports out-of-benchmark performance, not the mechanism. |
| `The results show transferability.` | `The results suggest positive transfer to related tasks.` | `transferability` is vague unless the source-target relation is named. |
| `We do transfer evaluation on eight benchmarks.` | `We evaluate cross-benchmark generalization on eight external benchmarks.` | Use `transfer evaluation` only for explicit transfer-learning setups. |
| `The transfers are positive.` | `Training on the source task yields positive transfer to related tasks.` | `transfer` is not normally countable this way. |

Decision guide:

- Section title: prefer `Generalization to Related Benchmarks` or `Cross-Benchmark Generalization`.
- Metric phrase: prefer `generalization gains` when reporting improvements on external benchmarks.
- Mechanism sentence: use `positive transfer` when arguing that source-task training helped a target task.
- Experiment phrase: use `transfer evaluation` only if the setup explicitly has a source-target framing.
- Avoid mixing `transfer` and `generalization` in the same sentence unless both meanings are needed.
- Do not write `transfers are positive`; write `the model shows positive transfer` or `training yields positive transfer`.

## 11. Error Analysis And Failure Modes

Use these verbs to connect failures to mechanisms:

- `inspect`: look at examples or outputs.
- `analyze`: systematic investigation.
- `identify`: find a recurring pattern.
- `categorize`: group errors.
- `attribute`: assign a cause cautiously.
- `trace`: follow a failure back to a stage.
- `reveal`, `expose`: failures make a weakness visible.
- `indicate`, `suggest`: infer from errors.
- `stem from`, `arise from`: describe likely source.
- `correspond to`: align one pattern with another.

Patterns:

```latex
We inspect model errors by task setting.
We identify two recurring failure modes.
These errors indicate that models can A but fail to B.
This failure mode suggests that the model relies on A rather than B.
The errors stem from incomplete mapping rather than visual recognition alone.
```

Examples:

```latex
We identify two recurring failure modes: copying intermediate evidence and generating plausible but incorrect outputs.
```

```latex
These errors suggest that models often extract useful evidence but fail to complete the final decision step.
```

Notes:

- Use `suggest` rather than `prove` for error-based explanations.
- Use `stem from` only when the source is supported by evidence.

## 12. Figures, Tables, And Captions

Use verbs according to the visual object's function:

- `illustrate`: figure explains a process, example, or mechanism.
- `visualize`: figure shows distributions, embeddings, or trends visually.
- `compare`: figure/table contrasts settings, models, or groups.
- `summarize`: table compresses statistics, settings, or datasets.
- `report`: table gives results or metrics.
- `list`: table enumerates items.
- `plot`: graph shows curves or points.
- `depict`: visual depiction, often diagrams.
- `show`: acceptable generic fallback.

Patterns:

```latex
Figure~\ref{} illustrates the three-stage process.
Table~\ref{} summarizes dataset statistics.
Table~\ref{} reports accuracy across settings.
Figure~\ref{} compares gains across external benchmarks.
```

Examples:

```latex
Table~\ref{tab:dataset_overview} summarizes the dataset statistics by split.
```

```latex
Figure~\ref{fig:results} compares generalization gains across external benchmarks.
```

Decision guide:

- Process or example figure: `illustrates`.
- Statistics table: `summarizes`.
- Result table: `reports`.
- Comparison figure: `compares`.

## 13. Discussion And Mechanistic Interpretation

Use these verbs to express causal or mechanistic claims carefully:

- `suggest`, `indicate`, `imply`: evidence-to-interpretation.
- `explain`, `account for`: explanation, stronger claim.
- `attribute`: assign source; use cautiously.
- `stem from`, `arise from`: likely cause.
- `reflect`: result manifests a property.
- `correspond to`: one pattern aligns with another.
- `align with`, `be consistent with`: conservative agreement.

Patterns:

```latex
This pattern suggests that X is a bottleneck.
The improvement may stem from A.
This result is consistent with B.
The gap reflects the difficulty of C.
We attribute this improvement to A.
```

Examples:

```latex
The gap reflects the difficulty of generating a target output from a large search space.
```

```latex
The improvement is consistent with the intuition that hints constrain the answer space.
```

Avoid:

```latex
This proves that...
```

Prefer:

```latex
This suggests that...
This is consistent with...
This may indicate that...
```

## 14. Limitations And Scope

Use these verbs to state boundaries without sounding defensive:

- `focus on`: state scope.
- `consider`: state evaluated conditions.
- `examine`: state what is or is not studied.
- `leave`: future work or unaddressed scope.
- `limit`, `restrict`: constraints.
- `assume`: assumption.
- `does not address`, `does not establish`: precise limitation.
- `remain`: unresolved issue.
- `warrant`: deserves future study.

Patterns:

```latex
Our evaluation focuses on final outputs and does not examine intermediate reasoning.
This analysis is limited to X and does not establish Y.
A remaining limitation is that X.
Future work could examine whether X extends to Y.
```

Examples:

```latex
Our evaluation focuses on final outputs and does not verify whether intermediate reasoning steps are correct.
```

```latex
This analysis does not establish the causal mechanism behind the observed failures.
```

Avoid:

```latex
Due to time and resource limitations...
There are some limitations in our work.
```

## 15. Conclusion And Takeaway

Use these verbs to close with evidence-backed implications:

- `indicate`: evidence-backed takeaway.
- `suggest`: cautious broader implication.
- `highlight`: emphasize importance.
- `point to`: identify a bottleneck or direction.
- `demonstrate`: established capability/effect.
- `reveal`: discovered pattern.
- `remain`: unresolved difficulty.
- `underscore`: emphasize serious need or limitation; use sparingly.
- `motivate`: justify future work.

Patterns:

```latex
These findings indicate that current models still struggle to X.
The results point to A as a key bottleneck.
This highlights the need for B.
X remains challenging under Y.
```

Examples:

```latex
These findings indicate that current MLLMs still struggle with open-form reasoning when the answer is not listed as an option.
```

```latex
The results point to visual-to-symbolic mapping as a key bottleneck.
```

## Fast Verb Table

| Weak or overloaded verb | Better options | Use when |
| --- | --- | --- |
| `show` | `reveal` | The result exposes a clear trend, gap, or bottleneck. |
| `show` | `indicate` | The result points to an interpretation. |
| `show` | `suggest` | The interpretation should be cautious. |
| `show` | `demonstrate` | The evidence establishes an ability or effect. |
| `show` | `validate` | The result supports a design choice or hypothesis. |
| `test` | `evaluate` | You formally measure model/method performance. |
| `test` | `assess` | You measure an effect, ability, or impact. |
| `test` | `isolate` | The setup separates one factor from another. |
| `use` | `adopt` | You use an established protocol, metric, or baseline. |
| `use` | `apply` | You apply a method/tool to data or a setting. |
| `use` | `leverage` | Only when exploiting a resource, advantage, pretrained capability, or external signal. Do not use it as a decorative synonym for `use`. |
| `make` | `enable` | A method makes an ability possible. |
| `make` | `allow` | A design permits a comparison or operation. |
| `get` | `obtain`, `achieve` | You report performance or results. |
| `have` | `contain`, `include`, `comprise` | You describe dataset/resource contents. |
| `give answer` | `produce`, `generate`, `recover`, `select` | You describe output behavior. |
| `help` | `improve`, `reduce`, `constrain`, `facilitate` | You can name the concrete effect. |
| `compare` | `benchmark` | You systematically evaluate multiple models/tasks. |
| `look at` | `inspect`, `examine`, `analyze` | You study examples, outputs, or mechanisms. |

## Paper Stage Cheat Sheet

Use these verbs as defaults by section:

- Abstract: `introduce`, `present`, `evaluate`, `reveal`, `find`, `demonstrate`, `achieve`, `improve`, `indicate`.
- Introduction: `require`, `involve`, `motivate`, `remain`, `address`, `introduce`, `reveal`, `highlight`.
- Related Work: `study`, `examine`, `investigate`, `explore`, `address`, `extend`, `evaluate`, `benchmark`, `leave`, `overlook`.
- Benchmark / Dataset: `collect`, `curate`, `construct`, `annotate`, `filter`, `verify`, `categorize`, `define`, `assign`, `cover`.
- Method / Design: `design`, `propose`, `formulate`, `derive`, `decompose`, `isolate`, `constrain`, `integrate`, `preserve`, `enable`.
- Experiment Setup: `evaluate`, `assess`, `compare`, `measure`, `test`, `ablate`, `control`, `adopt`, `report`.
- Results: `achieve`, `outperform`, `improve`, `reduce`, `increase`, `drop`, `maintain`, `match`, `exceed`, `reveal`.
- Analysis: `inspect`, `identify`, `analyze`, `attribute`, `suggest`, `indicate`, `expose`, `trace`, `reflect`.
- Discussion: `suggest`, `indicate`, `imply`, `align with`, `be consistent with`, `account for`, `stem from`.
- Conclusion: `demonstrate`, `reveal`, `indicate`, `highlight`, `point to`, `remain`, `motivate`.

## Final Check

Before changing a verb, ask:

1. What is the sentence doing: introducing, defining, evaluating, reporting, interpreting, comparing, or limiting?
2. Is the verb too generic for that function?
3. Does the new verb overclaim the evidence?
4. Does the subject fit the verb naturally?
5. Would a simpler concrete verb be more precise than a formal synonym?
