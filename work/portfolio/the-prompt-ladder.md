# The Prompt Ladder — FlyRank Content Refresh

**Track:** General AI Fluency · Week 2  
**Example task:** Ask an AI assistant to help frame the Content Refresh ML problem.

> **Method note:** The six response excerpts below are illustrative, controlled comparisons showing the kind of output each prompt is designed to elicit. They are not transcripts from six separately executed model calls. For a fully empirical submission, run each prompt in a fresh chat, paste the actual response into the matching section, and revise the notes to match what happened. This distinction is intentional: I am not presenting simulated outputs as observed test results.

## 1. Baseline — weak prompt

**Layer:** Baseline (no added layer)

**Prompt**
```text
Help me with my machine learning internship project.
```

**Representative output excerpt**
> Machine learning is a branch of artificial intelligence. First, identify your problem, collect data, preprocess it, choose an algorithm, train your model, and evaluate its performance. You can use Python libraries such as pandas and scikit-learn.

**Four notes**
- **Prompt change:** None. This is the vague prompt I might have typed without thinking.
- **What improved in the output:** Nothing specific to my project. It gives a basic ML workflow, but that is not yet useful for a decision.
- **What still failed:** It does not know my internship lane, dataset, user, task type, or what I need to produce.
- **What I would try next:** State the exact goal.

---

## 2. Version 1 — clearer goal

**Single added layer:** A clearer goal

**Prompt**
```text
Help me define the machine-learning task for my FlyRank internship project. I need to decide what the model should do.
```

**Representative output excerpt**
> Start by deciding whether the task is classification, regression, clustering, or ranking. Define the prediction target and the output the team needs. Then choose a metric that matches that output.

**Four notes**
- **Prompt change:** I changed only the goal from broad project help to defining the ML task.
- **What improved in the output:** The response now focuses on task framing rather than explaining what machine learning is.
- **What still failed:** It still gives generic advice and does not know which business workflow I am working on.
- **What I would try next:** Name the audience who will use the result.

---

## 3. Version 2 — defined audience

**Single added layer:** A defined audience

**Prompt**
```text
Help me define the machine-learning task for my FlyRank internship project. I need to decide what the model should do. Write for a junior ML intern explaining the task to a content or SEO team.
```

**Representative output excerpt**
> The team needs a practical way to decide which pages to review first. Explain the model in terms of the team's review queue, not only in terms of algorithms. The output should help a person decide what to inspect.

**Four notes**
- **Prompt change:** I added only the intended reader: a junior ML intern communicating with a content or SEO team.
- **What improved in the output:** The explanation starts connecting the model to a team's day-to-day decision and avoids assuming the reader only cares about algorithms.
- **What still failed:** The response is still hypothetical. It does not know that my chosen lane is Content Refresh or what data I have.
- **What I would try next:** Add the real project context.

---

## 4. Version 3 — real context

**Single added layer:** Real context

**Prompt**
```text
Help me define the machine-learning task for my FlyRank internship project. I need to decide what the model should do. Write for a junior ML intern explaining the task to a content or SEO team.

My selected lane is Content Refresh. The project uses an anonymized starter dataset with 30,000 webpage records and 44 columns. Available signals include content age, impressions, clicks, CTR, average search position, and engagement measures. The team needs to prioritize pages for human review.
```

**Representative output excerpt**
> This is a ranking problem: produce an ordered list of webpages for the content team to review. Each row represents one webpage. Signals such as content age and search performance can help rank pages, but the ranking is decision support; a person still decides whether a page needs an update.

**Four notes**
- **Prompt change:** I added only the real project context: Content Refresh, the dataset shape, available signal types, and the team's review decision.
- **What improved in the output:** It now identifies ranking as a sensible task and describes an output that matches the actual workflow: an ordered review queue.
- **What still failed:** The answer could still be hard to reuse. It is not structured as a clear assignment response, and the context alone does not prevent unsupported claims about future decline.
- **What I would try next:** Specify the output format.

---

## 5. Version 4 — specified output format

**Single added layer:** A specified output format

**Prompt**
```text
Help me define the machine-learning task for my FlyRank internship project. I need to decide what the model should do. Write for a junior ML intern explaining the task to a content or SEO team.

My selected lane is Content Refresh. The project uses an anonymized starter dataset with 30,000 webpage records and 44 columns. Available signals include content age, impressions, clicks, CTR, average search position, and engagement measures. The team needs to prioritize pages for human review.

Return the answer with these headings: Task type, Target, Unit of analysis, Expected output, and Why this task fits.
```

**Representative output excerpt**
> **Task type:** Ranking  
> **Target:** A relevance signal for identifying pages that may need review. Ideally, this would be based on an observed decline in a future time window.  
> **Unit of analysis:** One webpage per row.  
> **Expected output:** An ordered list of pages for human review.  
> **Why this task fits:** The team needs to prioritize limited review time, not simply label every page as good or bad.

**Four notes**
- **Prompt change:** I added only a required response structure with five headings.
- **What improved in the output:** It is easier to compare, check, and transfer into my assignment notebook. It separates the target from the unit and output.
- **What still failed:** The answer may still blur an ideal future outcome and a proxy label in the starter data. Adding more structure did not automatically make the reasoning more accurate.
- **What I would try next:** Add one constraint that prevents unsupported prediction claims.

---

## 6. Version 5 — constraints

**Single added layer:** Constraints

**Prompt**
```text
Help me define the machine-learning task for my FlyRank internship project. I need to decide what the model should do. Write for a junior ML intern explaining the task to a content or SEO team.

My selected lane is Content Refresh. The project uses an anonymized starter dataset with 30,000 webpage records and 44 columns. Available signals include content age, impressions, clicks, CTR, average search position, and engagement measures. The team needs to prioritize pages for human review.

Return the answer with these headings: Task type, Target, Unit of analysis, Expected output, and Why this task fits.

Constraints: Do not claim that the model predicts future Google rankings or proves that a page needs updating. Distinguish an observed future outcome from a rule-derived proxy label. Do not invent model results or business impact. Keep the final decision with the human content team.
```

**Representative output excerpt**
> **Task type:** Ranking  
> **Target:** The ideal target is a decline measured in a later time window. If the starter dataset only provides a rule-derived decline label, describe it as a proxy for current decline signals, not as a verified future outcome.  
> **Unit of analysis:** One webpage per row.  
> **Expected output:** A ranked review queue for a human team.  
> **Why this task fits:** The aim is to help the team decide which pages to inspect first. This does not establish causation or predict Google's future rankings.

**Four notes**
- **Prompt change:** I added only constraints against future-ranking claims, confusing proxies with observed outcomes, fabricated metrics, and removing human judgement.
- **What improved in the output:** The wording becomes more careful about what the starter data can and cannot show. It keeps the review decision with the team.
- **What still failed:** The answer is more reliable, but it still needs a metric to explain how I would judge the ranked list. The constraints also make it longer.
- **What I would try next:** This is the fifth and final ladder version. For a future prompt, I would test a success metric or a verification requirement as a separate experiment rather than quietly adding another layer here.

---

# Side-by-side learning

| Run | One named layer added | Main output change | Remaining weakness |
|---|---|---|---|
| Baseline | None | Generic ML workflow | No project relevance |
| Version 1 | Clearer goal | Focuses on framing the ML task | Still no lane context |
| Version 2 | Defined audience | Explains the decision in team language | Still hypothetical |
| Version 3 | Real context | Identifies ranking and a review queue | Output not structured; proxy nuance weak |
| Version 4 | Output format | Clear sections that are easy to inspect | Structure does not guarantee accuracy |
| Version 5 | Constraints | Avoids overclaiming and distinguishes proxy from future outcome | Does not yet specify evaluation metric |

## Honest result

The changes did not make every part better. Adding an audience made the explanation more relevant, but it did not add factual project detail. Adding the output format improved readability, but it did not fix the target/proxy ambiguity. The constraints made the final response safer and more defensible, although longer. This is why I should test one layer at a time instead of adding many instructions and guessing which one helped.

---

# Final reusable prompt

Use this prompt when framing a machine-learning task for a content or SEO team. Replace the bracketed details for another project.

```text
Act as a practical machine-learning mentor helping a junior ML intern explain a project to the team that will use its output.

Project context:
- Project or lane: [describe the workflow]
- Decision the team needs to make: [describe the real decision]
- Dataset: [describe source, size, unit of analysis, and relevant columns]
- Intended user: [describe who will use the result]

Help me frame the ML task. Return these sections:
1. Task type: choose classification, regression, clustering, ranking, or scoring and explain why.
2. Target: state what is being predicted or optimized. Say whether it is an observed outcome or a proxy, and explain the limitation.
3. Unit of analysis: state exactly what one row represents.
4. Expected output: describe what the model returns and how the team will use it.
5. Success metric: recommend one metric that matches the real decision and explain what a good result would mean. Do not invent a measured score.
6. Human decision: state what the model can support and what a person must still decide.

Constraints:
- Use only the project facts I provide. Do not invent data, labels, results, deployment, or business impact.
- Do not present correlation or a proxy label as proof of causation or a verified future outcome.
- Identify possible data leakage if a target is derived from other columns.
- Explain technical terms in plain language the intended user can understand.
- If important information is missing, list the missing information instead of silently assuming it.
- Keep the recommendation practical and specific to the stated workflow.
```

## Final check before submission

- [x] Baseline plus five versions (six prompt runs represented)
- [x] Exactly one named layer per version
- [x] Each version includes a representative output excerpt and four notes
- [x] Includes an honest limitation: structure improved readability but did not fix accuracy
- [x] Final prompt is reusable by another intern after replacing the project details
- [ ] Replace representative excerpts with actual model outputs if the assignment reviewer expects evidence of six live runs
