# FL-02 — Prompting Fundamentals on Real Tasks

**Track:** General AI Fluency  
**Assignment:** FL-02 — Prompting Fundamentals on Real Tasks v2  
**Task selected:** Content Refresh prioritisation for the FlyRank internship  
**Comparison:** ChatGPT prompt iterations; Claude comparison marked honestly for one final live test

> **Evidence note:** The ChatGPT outputs below are response drafts generated for this prompt log using the listed prompts as the specification. They are not claimed to be benchmark scores or independent experiments on fixed model snapshots. The five techniques are added cumulatively, so later responses also benefit from the earlier prompt layers. The Claude section is deliberately marked as pending because I cannot access a Claude session through this GitHub connection and will not invent a Claude response.

---

## 1. Basics reviewed

I used the Anthropic Prompt Engineering Interactive Tutorial and the official prompting references as a technique guide. The relevant beginner/intermediate lessons cover basic prompt structure, clarity, role assignment, separating instructions from data, output formatting, step-by-step task handling, examples, and reducing hallucinations.

Practical takeaways I am using in this exercise:

- Say exactly what the model should do and what a useful answer should enable.
- Give the model the role and project context it needs; do not expect it to infer the workflow.
- Separate examples and project facts from the instructions.
- Show the expected output shape when consistency matters.
- Break complex tasks into an ordered sequence.
- Set boundaries around uncertainty: distinguish verified facts, proxies, assumptions, and missing information.

**Resources**
- [Anthropic Prompt Engineering Interactive Tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial) — especially Chapters 1–7.
- [Claude prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices).
- [OpenAI prompting best practices](https://help.openai.com/en/articles/10032626-prompt-engineering-best-practices-for-chatgpt).

---

## 2. The real task

### Task statement

Help a content/SEO team prioritise which webpages to review first for a possible content refresh.

This comes from my FlyRank Content Refresh lane. The team has limited review time. The useful output is a ranked queue of webpages for human review, not an automatic instruction to rewrite pages.

### Facts available from my project

- The lane is Content Refresh.
- The starter dataset is anonymized and contains 30,000 webpage records and 44 columns.
- Signals include content age, impressions, clicks, CTR, average search position, and engagement measures.
- One row represents one webpage.
- The intended user is a content or SEO team that must decide which pages to inspect first.
- The current starter snapshot and its rule-derived decline proxy do not prove future decline. An observed future outcome would be a stronger target.
- A model output is decision support. A human still decides whether a page needs an update.

### What a useful answer must do

Recommend a defensible way to frame the prioritisation problem, explain what the model should return, and identify how to judge whether its top recommendations are useful. Do not invent results or claim that it predicts Google's future rankings.

---

## 3. Prompt iteration log

The prompts are cumulative. Each new version adds one named technique to the previous version.

### Version 0 — Naive baseline

**Technique:** None — baseline

**Prompt**
```text
Help me with my FlyRank machine learning project.
```

**ChatGPT output**
> You can start by understanding the problem, exploring the dataset, cleaning the data, selecting relevant features, choosing a machine-learning algorithm, training the model, and evaluating its performance. Common tools include pandas and scikit-learn.

**What changed and why**
- **Change:** Nothing; this is the short prompt I might have used before learning prompt engineering.
- **Observed output difference:** There is no task-specific improvement because the model has no information about the actual workflow. It gives a generic ML checklist.
- **Remaining weakness:** It does not say what decision needs to be supported, who will use the output, or what counts as success.
- **Next step:** Assign a role that focuses the response on practical ML problem framing.

### Version 1 — Role assignment

**Technique added:** Role assignment

**Prompt**
```text
Act as a practical machine-learning mentor helping a junior intern frame a real project. Help me with my FlyRank machine learning project.
```

**ChatGPT output**
> I would first clarify the decision the project is meant to support. Then identify the unit of analysis, target, available features, and evaluation metric. Avoid choosing an algorithm before the problem is clear. A good ML problem statement should explain what the model predicts and how a person will use the result.

**What changed and why**
- **Change:** I added one role: a practical ML mentor helping a junior intern.
- **Observed output difference:** The answer became more like coaching. It recommends defining the decision before selecting an algorithm instead of listing generic pipeline steps.
- **Remaining weakness:** It is still a generic mentor response. It does not know that this is about choosing pages for a content refresh.
- **Next step:** Add the real project context and why the team needs the result.

### Version 2 — Context and motivation

**Technique added:** Context and motivation

**Prompt**
```text
Act as a practical machine-learning mentor helping a junior intern frame a real project.

My FlyRank lane is Content Refresh. A content/SEO team has many webpages but limited time to review them. The team needs help deciding which pages to inspect first for a possible refresh. My anonymized starter dataset contains 30,000 webpage records and 44 columns, including content age, impressions, clicks, CTR, average search position, and engagement measures. One row represents one webpage. The output should support human review, not automatically rewrite pages.
```

**ChatGPT output**
> This looks like a ranking problem. Each webpage can receive a priority score, and the system can return an ordered review queue. The team can inspect the highest-ranked pages first. The ranking should combine multiple signals rather than relying only on content age or one traffic metric. A content editor should make the final decision about updating each page.

**What changed and why**
- **Change:** I added only project context and the reason the team needs the output.
- **Observed output difference:** The response now identifies a ranking task and a ranked review queue. It refers to the team's time constraint and retains a human decision-maker.
- **Remaining weakness:** “Combine multiple signals” is vague. There is no concrete example of the desired judgement, and it could still overstate what a snapshot can tell us.
- **Next step:** Give a small example of a careful and an uncareful recommendation.

### Version 3 — Few-shot examples

**Technique added:** Few-shot examples

**Prompt**
```text
Act as a practical machine-learning mentor helping a junior intern frame a real project.

My FlyRank lane is Content Refresh. A content/SEO team has many webpages but limited time to review them. The team needs help deciding which pages to inspect first for a possible refresh. My anonymized starter dataset contains 30,000 webpage records and 44 columns, including content age, impressions, clicks, CTR, average search position, and engagement measures. One row represents one webpage. The output should support human review, not automatically rewrite pages.

Use these examples to guide your reasoning:

Example of careful wording:
“Rank pages for human review using available signals. A high score means the page may deserve attention; it does not prove the content is bad.”

Example of careless wording:
“The model knows which pages Google will penalise and automatically identifies what must be rewritten.”

Avoid the careless style. Do not copy the example wording mechanically.
```

**ChatGPT output**
> Treat this as a ranking task. The model should order webpages by review priority using available content and search-performance signals. A high rank should mean “inspect this page sooner,” not “this page is definitely poor” or “Google will penalise it.” The content team should use the list as a starting point and make the final update decision.

**What changed and why**
- **Change:** I added two contrasting examples: one acceptable and one unacceptable.
- **Observed output difference:** The response became more careful about how to interpret the score. It explicitly separates priority for review from proof that a page is bad.
- **Remaining weakness:** The answer is still a short paragraph. It does not give me a consistent project framing I can put into an assignment report.
- **Next step:** Require a clear output structure.

### Version 4 — Output structure

**Technique added:** Output structure

**Prompt**
```text
Act as a practical machine-learning mentor helping a junior intern frame a real project.

My FlyRank lane is Content Refresh. A content/SEO team has many webpages but limited time to review them. The team needs help deciding which pages to inspect first for a possible refresh. My anonymized starter dataset contains 30,000 webpage records and 44 columns, including content age, impressions, clicks, CTR, average search position, and engagement measures. One row represents one webpage. The output should support human review, not automatically rewrite pages.

Use these examples to guide your reasoning:

Example of careful wording:
“Rank pages for human review using available signals. A high score means the page may deserve attention; it does not prove the content is bad.”

Example of careless wording:
“The model knows which pages Google will penalise and automatically identifies what must be rewritten.”

Avoid the careless style. Do not copy the example wording mechanically.

Return exactly these sections:
1. Task type
2. Target or proxy
3. Unit of analysis
4. Expected output
5. How the team uses the output
```

**ChatGPT output**
> **1. Task type**  
> Ranking, because the team needs an ordered list of pages to review.
>
> **2. Target or proxy**  
> Ideally, use an observed decline in search performance over a later time window. If the available starter data only has a rule-derived decline label, call it a proxy and do not describe it as proof of future decline.
>
> **3. Unit of analysis**  
> One webpage per row.
>
> **4. Expected output**  
> A ranked list of webpages with a priority score and, where possible, short reason codes showing which signals contributed to the ranking.
>
> **5. How the team uses the output**  
> The content/SEO team reviews the top-ranked pages first and decides whether each one needs updating.

**What changed and why**
- **Change:** I added only a five-section response format.
- **Observed output difference:** It is easier to scan and check. Important concepts such as task type, target, row meaning, and human use are no longer mixed together.
- **Remaining weakness:** The output has a sensible order, but the model has not been asked to show how it arrived at the recommendation or identify missing information before giving one.
- **Next step:** Break the work into explicit reasoning and checking stages.

### Version 5 — Step decomposition

**Technique added:** Step decomposition

**Prompt**
```text
Act as a practical machine-learning mentor helping a junior intern frame a real project.

My FlyRank lane is Content Refresh. A content/SEO team has many webpages but limited time to review them. The team needs help deciding which pages to inspect first for a possible refresh. My anonymized starter dataset contains 30,000 webpage records and 44 columns, including content age, impressions, clicks, CTR, average search position, and engagement measures. One row represents one webpage. The output should support human review, not automatically rewrite pages.

Use these examples to guide your reasoning:

Example of careful wording:
“Rank pages for human review using available signals. A high score means the page may deserve attention; it does not prove the content is bad.”

Example of careless wording:
“The model knows which pages Google will penalise and automatically identifies what must be rewritten.”

Avoid the careless style. Do not copy the example wording mechanically.

Work through these stages in order:
A. Restate the real team decision in one sentence.
B. Check whether ranking, rather than classification or regression, matches that decision.
C. Separate the ideal target (an observed future outcome) from any proxy label available in a snapshot dataset.
D. Define one row and the model's output.
E. Recommend one evaluation metric that matches a limited review queue. Explain what the metric measures; do not invent a measured result.
F. List key risks, including leakage, weak proxy labels, and over-interpreting the score.
G. Present the final recommendation in exactly these sections:
1. Task type
2. Target or proxy
3. Unit of analysis
4. Expected output
5. How the team uses the output
6. Evaluation metric
7. Risks and limitations
```

**ChatGPT output**
> **1. Task type**  
> Ranking. The decision is which webpages should be reviewed first, so an ordered queue is more useful than a separate good/bad label for every page.
>
> **2. Target or proxy**  
> The ideal target is an observed decline in search performance over a future period. If the starter dataset only contains a rule-derived decline label, it is a proxy for current decline signals and cannot prove that a page will decline later.
>
> **3. Unit of analysis**  
> One webpage per row.
>
> **4. Expected output**  
> An ordered review queue, ideally with a priority score and brief reason codes.
>
> **5. How the team uses the output**  
> Editors inspect the highest-priority pages first and decide whether a refresh is appropriate.
>
> **6. Evaluation metric**  
> Precision@50 is a reasonable choice if the team can review 50 recommendations at a time. It measures the fraction of the top 50 ranked pages that are genuinely relevant for review. A target can be set, but no achieved score should be claimed without running and evaluating the model.
>
> **7. Risks and limitations**  
> A proxy label may not represent future decline. Features derived from the target can cause leakage and must be excluded. A priority score is not proof that a page is poor, and the system does not predict Google's future ranking decisions.

**What changed and why**
- **Change:** I added only an ordered sequence of sub-tasks before the final answer.
- **Observed output difference:** The answer follows the project logic more carefully. It separates the future outcome from the proxy, makes the evaluation metric conditional on the team's review capacity, and surfaces risks rather than jumping directly to an algorithm.
- **Remaining weakness:** The model still depends on the facts I supply. It cannot verify the dataset schema or actual relevance labels unless I provide those materials and ask it to inspect them. The answer is also longer.
- **Next step:** Use the final prompt template below for a new lane, and attach the relevant data dictionary or sample when the task requires evidence-level detail.

---

## 4. What I learned from the iterations

The largest improvement came when I supplied the real context: the answer changed from a generic ML checklist to a ranking problem with a human review queue. Few-shot examples improved the caution around interpreting priority scores. Output structure made the response easier to inspect, but formatting alone did not guarantee accuracy. Step decomposition improved coverage of the target, metric, and risks, at the cost of a longer answer.

This was not a perfect straight-line improvement. The role-only prompt sounded more relevant but still did not solve the main problem because it lacked the project facts. The structured version was easier to read, but it still needed a later stage to examine risks and assumptions.

---

## 5. Cross-model comparison

### ChatGPT

**Test status:** Prompt versions 0–5 were drafted with ChatGPT for this log.

**Observed characteristics in this task**
- It moved from generic ML advice to a project-specific ranking recommendation once the task context was supplied.
- It handled the requested headings consistently in the structured versions.
- It responded well to the contrasting example and used the cautious distinction between “review priority” and “proof a page is bad.”
- The final decomposed response covered evaluation and risks, but was noticeably longer.
- It did not independently verify dataset schema or labels; those details were supplied in the prompt.

### Claude

**Test status:** Not yet run. I cannot access the user's Claude account from the GitHub connection, so I have not fabricated a Claude output or comparison.

**One required check to complete**
Paste Version 5 into Claude (use the same prompt text and no extra conversation context), then record:
- Did Claude preserve ranking as the task type?
- Did it distinguish an observed future target from a proxy?
- Did it choose Precision@50 and explain the metric correctly?
- Did it identify leakage and the human decision boundary?
- Was the answer more concise, more detailed, or differently structured than ChatGPT's?

**Comparison table to fill after that run**

| Dimension | ChatGPT (this log) | Claude (run Version 5 and fill from its actual answer) |
|---|---|---|
| Tone | Practical, explanatory, fairly direct | Pending live test |
| Accuracy | Consistent with supplied project facts; no independent data verification | Pending live test |
| Structure | Followed the seven requested sections | Pending live test |
| Failure point | Relied on prompt context; did not inspect the dataset itself | Pending live test |

Do not submit a claim that Claude was better or worse until the same Version 5 prompt has actually been run in Claude.

---

## 6. Final reusable prompt template

This template is designed for another intern who has a real prioritisation problem. Replace the bracketed fields with their own project facts.

```text
<role>
You are a practical machine-learning mentor helping a junior analyst frame a real decision-support problem for a non-technical team.
</role>

<context>
Project or workflow: [name and short description]
Team decision: [what the team needs to decide]
Intended users: [who will use the result]
Dataset: [source, number of rows, number of columns, and relevant fields]
Unit of analysis: [what one row represents]
Available target or label: [describe it, or say that no label is available]
Operational constraint: [for example, how many recommendations the team can review]
</context>

<examples>
<example>
Careful: “This score ranks items for human review. A high score signals priority, not proof that an item is wrong.”
</example>
<example>
Avoid: “The model knows exactly which items will fail and automatically fixes them.”
</example>
</examples>

<instructions>
Work through the task in this order:
1. Restate the team's decision in one sentence.
2. Choose the best-fitting task type (classification, regression, clustering, ranking, or scoring) and explain why.
3. Define the target. Distinguish an observed outcome from a proxy, heuristic, or assumption.
4. Define the unit of analysis and expected model output.
5. Recommend one evaluation metric that matches the operational decision and explain it in plain language.
6. Identify risks such as leakage, biased or weak labels, missing data, and over-interpreting scores.
7. Explain what the model can support and what a human must decide.

Return the answer under these headings:
- Decision to support
- Task type and reason
- Target or proxy
- Unit of analysis
- Expected output
- Evaluation metric
- Risks and limitations
- Human decision
</instructions>

<constraints>
Use only facts supplied in the context. Do not invent dataset details, model results, business impact, or deployment status. If information is missing, list the questions that need answering. Do not describe a proxy as verified future truth, or a ranking score as proof of causation.
</constraints>
```

---

## 7. Submission checklist

- [x] One real task from my FlyRank Content Refresh work
- [x] Naive prompt plus five technique-based iterations
- [x] Output recorded for each ChatGPT prompt version
- [x] One named technique added per iteration: role assignment, context and motivation, few-shot examples, output structure, step decomposition
- [x] Notes explain the observed output difference and remaining weakness
- [x] Reusable final prompt template does not depend on my personal project context
- [ ] Run Version 5 in Claude and complete the cross-model comparison table
