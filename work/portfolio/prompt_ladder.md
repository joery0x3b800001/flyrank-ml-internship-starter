# Prompt ladder: explain my content-refresh project

## What I tested

The task is to draft a short project description for the content-refresh scoring work. I kept
the project facts and the assistant the same, then added exactly one named prompt layer at
each step. The output excerpts below are the assistant's first-draft responses for each
version in this session; no external Claude or other provider was run. I include the weak
baseline on purpose and keep unsupported claims visible rather than silently correcting them.

The final reusable prompt is at the end.

## Baseline — weak prompt

**Prompt**

> Help me with my content project.

**Output**

> Your content project can use AI and data to improve performance, find opportunities, and
> help your team make smarter decisions.

**Notes**

- **What changed in the prompt:** Nothing; this is the deliberately vague starting point.
- **What improved in the output:** Nothing useful. It returned a generic description that
  could fit almost any project.
- **What still failed:** No user, decision, evidence, scope, or concrete output. “Improve
  performance” implies an outcome the work has not demonstrated.
- **What I would try next:** Add one clear goal for the response.

## Version 1 — add a clearer goal

**Only new layer:** Clearer goal.

**Prompt**

> Write a short description of my content-refresh project.

**Output**

> This project uses data to rank content pages by decline risk so a team can prioritize
> refreshes and improve organic performance.

**Notes**

- **What changed in the prompt:** I specified the requested goal: describe the project.
- **What improved in the output:** It now names ranking and refresh prioritization instead of
  talking about generic “opportunities.”
- **What still failed:** It still claims “decline risk” and improved performance without
  explaining what the label measures or whether a model has been evaluated.
- **What I would try next:** Name the reader so the explanation has someone specific to speak
  to.

## Version 2 — add a defined audience

**Only new layer:** Defined audience.

**Prompt**

> Write a short description of my content-refresh project for an SEO lead who owns an
> editorial refresh backlog.

**Output**

> For an SEO lead managing a refresh backlog, this project uses data to identify pages at
> risk of decline and prioritize updates that can protect organic traffic.

**Notes**

- **What changed in the prompt:** I named the intended reader: an SEO lead responsible for
  the refresh backlog.
- **What improved in the output:** It connects the work to a recognizable job and backlog,
  rather than addressing an abstract “team.”
- **What still failed:** This version got worse in an important way: it confidently says
  updates can protect traffic. The audience alone encouraged the draft to sound persuasive,
  not accurate; no refresh effect has been measured.
- **What I would try next:** Supply the actual project facts so the answer has evidence to
  use instead of filling the gaps with assumptions.

## Version 3 — add real context

**Only new layer:** Real context.

**Prompt**

> Write a short description of my content-refresh project for an SEO lead who owns an
> editorial refresh backlog. Context: the starter slice contains 30,000 content items. Its
> retrospective `down` label means impressions in the most recent 30 days were more than 20%
> below the previous 30 days; 16,262 items (54.2%) have that label. I have framed a ranking
> task, but have not trained or evaluated a model.

**Output**

> This project uses a 30,000-item content snapshot to frame a ranking task for an SEO lead's
> refresh backlog. In the snapshot, 16,262 items (54.2%) have a retrospective decline label:
> impressions fell more than 20% in the latest 30 days versus the previous 30. The model
> has not yet been trained or evaluated.

**Notes**

- **What changed in the prompt:** I added the real dataset size, exact retrospective label
  definition, observed count, and current project status.
- **What improved in the output:** The 54.2% figure now has a denominator and a definition;
  the output also stopped implying that a model already exists.
- **What still failed:** It describes the data but does not state what the SEO lead should do
  with the ranking. “Uses a snapshot” is also more about the method than the decision.
- **What I would try next:** Specify a structure that makes the decision and evidence easy
  to compare.

## Version 4 — add a specified output format

**Only new layer:** Output format.

**Prompt**

> Write a short description of my content-refresh project for an SEO lead who owns an
> editorial refresh backlog. Context: the starter slice contains 30,000 content items. Its
> retrospective `down` label means impressions in the most recent 30 days were more than 20%
> below the previous 30 days; 16,262 items (54.2%) have that label. I have framed a ranking
> task, but have not trained or evaluated a model. Format the answer as three labeled lines:
> Decision, Evidence, Status.

**Output**

> **Decision:** Help an SEO lead decide which pages to review first in the refresh backlog.
> **Evidence:** In a 30,000-item starter slice, 16,262 items (54.2%) meet the retrospective
> decline definition: impressions fell more than 20% in the latest 30 days versus the
> previous 30.
> **Status:** The ranking task is framed; no model has been trained or evaluated.

**Notes**

- **What changed in the prompt:** I requested three labeled lines: Decision, Evidence, and
  Status.
- **What improved in the output:** The audience's action, the observed figure, and the
  not-yet-built status are now distinct and easy to check.
- **What still failed:** “Meet the decline definition” is accurate but could still be read as
  a future-risk signal if separated from “retrospective.” The labels make the copy feel a
  little like a report, not portfolio prose.
- **What I would try next:** Add one explicit constraint against unsupported predictive or
  causal wording.

## Version 5 — add constraints

**Only new layer:** Constraints.

**Prompt**

> Write a short description of my content-refresh project for an SEO lead who owns an
> editorial refresh backlog. Context: the starter slice contains 30,000 content items. Its
> retrospective `down` label means impressions in the most recent 30 days were more than 20%
> below the previous 30 days; 16,262 items (54.2%) have that label. I have framed a ranking
> task, but have not trained or evaluated a model. Format the answer as three labeled lines:
> Decision, Evidence, Status. Do not claim future prediction, causal impact, traffic
> protection, or model performance.

**Output**

> **Decision:** Help an SEO lead decide which pages to review first in the refresh backlog.
> **Evidence:** In this 30,000-item starter slice, 16,262 items (54.2%) had a retrospective
> decline label, defined as impressions more than 20% lower in the latest 30 days than in
> the preceding 30.
> **Status:** I have framed a ranking task; I have not trained or evaluated a model. This
> describes an observed historical pattern, not a forecast or proof that a refresh changes
> traffic.

**Notes**

- **What changed in the prompt:** I added one constraint: do not claim future prediction,
  causal impact, traffic protection, or model performance.
- **What improved in the output:** The last line now directly distinguishes historical
  observation from a forecast or intervention effect. It no longer promises protected
  traffic.
- **What still failed:** The three-line form is useful for review but stiff as final public
  copy. Also, the exact label definition must travel with the 54.2% statistic.
- **What I would try next:** Keep the facts, audience, and constraints, but ask for natural
  prose while retaining a review checklist in the reusable prompt.

## Final reusable prompt

Copy this prompt for another project on the same track. Replace every bracketed field with
verified project details before running it.

> Draft a concise portfolio case-study introduction for **[specific reader who can act or
> hire]**. The introduction should help that reader understand **[the decision or problem
> this work addresses]**.
>
> Verified project context:
> - Project/data: [what the work is and what data it uses]
> - Unit of analysis: [one row/item represents what]
> - Target or proxy and exact definition: [what is measured, how, and over what period]
> - Evidence available now: [counts, metrics, and denominator; write “not measured yet” when
>   applicable]
> - Work completed: [what you actually did]
> - Work not completed: [what has not been built or tested]
>
> Write three short labeled sections: **The problem**, **What I did**, and **What came of
> it**. Make the reader's decision and next action clear. Use plain, direct language. Do not
> invent personal motivations, project steps, results, model performance, or customer impact.
> Do not imply that association proves causation or that a retrospective label predicts a
> future outcome. Keep each number attached to its denominator and definition. If an
> essential fact is missing, ask me one focused question instead of guessing.
>
> Before returning the draft, check it against the facts above. Then list any sentence that
> exceeds the evidence or any missing input that prevents a reliable claim.
