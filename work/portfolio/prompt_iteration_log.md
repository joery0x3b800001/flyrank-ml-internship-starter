# Prompt iteration log: interpreting the decline label

## Run status and scope

**Task chosen:** Draft a short, accurate explanation for an SEO lead of the decline-label
result in my content-refresh project. This is grounded in the completed ML-task framing work:
the starter slice contains 30,000 content items, and 16,262 (54.2%) have the retrospective
`down` label.

**What this does and does not prove:** `down` means impressions in the most recent 30 days
were more than 20% below the previous 30 days. The starter CSV is a snapshot; this label
describes a historical comparison, not a future outcome. No model has been trained or
evaluated yet.

**Run provenance:** The six prompts and representative responses below were drafted in this
Copilot session to make the controlled iteration concrete. They are not captured transcripts
from six separate Anthropic or OpenAI API runs. I attempted to open Claude and ChatGPT for
the final provider comparison, but the browser continued to show Claude's sign-in page and
ChatGPT's “Log in” state. The genuine Claude-vs-ChatGPT comparison is therefore **pending**;
no provider-specific behavior is fabricated here.

**FL-01 note:** I could not find a completed FL-01 audit artifact in this repository. I chose
the closest verified task in my existing lane work: explaining the 54.2% retrospective
decline-label rate without implying future prediction.

## Baseline — naive one-line prompt

**Prompt**

> Explain this data: 30,000 pages; 54.2% are marked down.

**Representative response**

> More than half of the pages are declining, which suggests a widespread content-performance
> problem. The team should review and refresh underperforming pages to improve traffic.

**What changed and why**

Nothing yet. This is the intentionally weak starting point.

**Output comparison**

- **Improved:** Nothing; it produces a readable sentence.
- **Still failed:** It treats the retrospective label as general “declining” and jumps from
  the number to an untested refresh recommendation.
- **Next:** Add one explicit role to focus the response.

## Version 1 — role assignment

**Only added technique:** Role assignment.

**Prompt**

> You are an SEO analyst. Explain this data: 30,000 pages; 54.2% are marked down.

**Representative response**

> As an SEO analyst, I’d read this as a broad search-performance decline: 16,262 of the
> 30,000 pages are marked down. The content team should prioritize those pages for refresh
> review.

**What changed and why**

I assigned an SEO-analyst role, hoping to get a work-relevant interpretation rather than a
generic explanation.

**Output comparison**

- **Improved:** It makes the count explicit (16,262) and speaks in an SEO context.
- **Still failed:** The role made the answer sound more authoritative, but did not make it
  more accurate. It still turns “marked down” into a broad decline and recommends refresh
  review without explaining the label or its limits.
- **Next:** Give it the project's actual context and why the explanation is needed.

## Version 2 — context and motivation

**Only added technique:** Context and motivation.

**Prompt**

> You are an SEO analyst. Explain this data: 30,000 pages; 54.2% are marked down. Context:
> this is a starter snapshot for a content-refresh prioritization project. An SEO lead needs
> to understand what the observed label means before deciding what pages to review.

**Representative response**

> In this 30,000-page starter snapshot, 16,262 pages (54.2%) carry the `down` label. This
> gives the SEO lead a useful starting point for deciding which pages to examine in the
> content-refresh backlog.

**What changed and why**

I added the snapshot/project context and the audience's decision.

**Output comparison**

- **Improved:** The output now frames the number as a snapshot and connects it to a review
  decision, rather than calling for an immediate refresh.
- **Still failed:** It still does not define `down`; a reader could mistake it for a forward
  risk label.
- **Next:** Show an example of the cautious distinction I want it to make.

## Version 3 — few-shot example

**Only added technique:** Few-shot example.

**Prompt**

> You are an SEO analyst. Explain this data: 30,000 pages; 54.2% are marked down. Context:
> this is a starter snapshot for a content-refresh prioritization project. An SEO lead needs
> to understand what the observed label means before deciding what pages to review.
>
> Example of the distinction to preserve: if a snapshot has 4 of 10 items labeled “down,”
> say “4 of 10 items carried the historical down label in this snapshot,” not “4 of 10 items
> will decline.”

**Representative response**

> In this 30,000-page starter snapshot, 16,262 pages (54.2%) carried the historical `down`
> label. That describes the measured comparison in this data, not how many pages will
> decline in the future.

**What changed and why**

I added one example that contrasts a historical label with a future prediction.

**Output comparison**

- **Improved:** The response now uses past-tense language and explicitly rejects the future
  interpretation.
- **Still failed:** It does not say how the label is calculated, so the “historical”
  qualifier is hard to verify.
- **Next:** Specify a consistent output structure that reserves space for the label
  definition and its limit.

## Version 4 — output structure

**Only added technique:** Output structure.

**Prompt**

> You are an SEO analyst. Explain this data: 30,000 pages; 54.2% are marked down. Context:
> this is a starter snapshot for a content-refresh prioritization project. An SEO lead needs
> to understand what the observed label means before deciding what pages to review.
>
> Example of the distinction to preserve: if a snapshot has 4 of 10 items labeled “down,”
> say “4 of 10 items carried the historical down label in this snapshot,” not “4 of 10 items
> will decline.”
>
> Use two labeled parts: **Observed** and **Use/limit**.

**Representative response**

> **Observed:** In the 30,000-page starter snapshot, 16,262 pages (54.2%) carried the
> historical `down` label.
>
> **Use/limit:** This can help an SEO lead decide what to inspect, but it does not say that
> these pages will decline or that refreshing them will improve traffic.

**What changed and why**

I requested two labeled parts: one for the observed result and one for how to use it.

**Output comparison**

- **Improved:** It is easier to separate the statistic from the decision and the claim limit.
- **Still failed:** The exact definition is still missing, and “what to inspect” is broader
  than necessary.
- **Next:** Ask for a short sequence of checks before drafting so the definition and claim
  boundary are handled before the prose.

## Version 5 — step decomposition

**Only added technique:** Step decomposition.

**Prompt**

> You are an SEO analyst. Explain this data: 30,000 pages; 54.2% are marked down. Context:
> this is a starter snapshot for a content-refresh prioritization project. An SEO lead needs
> to understand what the observed label means before deciding what pages to review.
>
> Example of the distinction to preserve: if a snapshot has 4 of 10 items labeled “down,”
> say “4 of 10 items carried the historical down label in this snapshot,” not “4 of 10 items
> will decline.”
>
> Use two labeled parts: **Observed** and **Use/limit**.
>
> Work in these steps: (1) state what the percentage counts and its denominator; (2) explain
> the label definition and time comparison; (3) draft the two parts using only those facts;
> (4) check that neither part implies future prediction or causal impact. Return only the
> two labeled parts.

**Representative response**

> **Observed:** In the 30,000-page starter snapshot, 16,262 pages (54.2%) had the
> retrospective `down` label, defined as impressions in the latest 30 days being more than
> 20% below the previous 30 days.
>
> **Use/limit:** An SEO lead can use this as context when choosing pages for review. It
> describes a past 30-day comparison; it does not predict future decline or show that a
> refresh will improve traffic.

**What changed and why**

I broke the task into ordered checks: denominator, label definition, draft, then claim audit.

**Output comparison**

- **Improved:** The response now carries the exact denominator and label window and states
  both limits. It answers the SEO lead's review question without promising a refresh effect.
- **Still failed:** This prompt structure does not prove that the interpretation is useful
  to an editor, and it does not validate any model. The real next step is a time-safe target
  and evaluation, not more assertive copy.
- **Next:** Run this exact final prompt independently in Claude and ChatGPT, then compare
  their actual outputs before deciding whether the steps earn their length.

## Cross-model comparison — pending actual runs

| Provider | Status | What can be compared |
|---|---|---|
| Claude | Not run; the integrated browser remained on Claude sign-in | No tone, accuracy, structure, or failure claim can be made |
| ChatGPT | Not run; the integrated browser showed “Log in” and did not accept a prompt | No tone, accuracy, structure, or failure claim can be made |

Use the final prompt below in a fresh chat in each provider. Save each exact response here.
Then compare whether it preserves the `down` definition, 30,000 denominator, 54.2% observed
rate, historical-vs-future distinction, and causal limit. Do not infer a provider difference
from these representative drafts.

## Final reusable prompt template

Replace every bracketed field with verified details. Do not paste private queries or
client-identifying information.

> You are a **[relevant role]** helping **[specific audience]** make **[specific decision]**.
> Explain this result using only the facts supplied:
>
> - Dataset or slice: **[what and when]**
> - Unit and denominator: **[one row represents what; total n]**
> - Observed result: **[count and percentage]**
> - Target or label: **[exact definition and measurement window]**
> - Project status: **[what has and has not been built or validated]**
>
> Example: for a historical label, say “N of M items carried the label in this snapshot,”
> not “N of M items will have the outcome.”
>
> Work in these steps: (1) verify the count and denominator from the supplied facts; (2)
> state the label definition and time window; (3) draft an **Observed** statement and a
> **Use/limit** statement for **[audience]**; (4) check for unsupported prediction,
> causality, or performance claims. Return only those two labeled statements. If a necessary
> fact is missing, ask one focused question instead of guessing.

## Resource and learning note

The linked OpenAI prompting-best-practices page was accessible during this task; its guidance
supports clear instructions and iterative refinement. I could not access the Anthropic
interactive tutorial in this session: the direct documentation request was blocked and the
likely tutorial host returned a 404. I have therefore not marked the tutorial chapters or
the two provider runs as completed. The five iterations above practice the assignment's
named techniques, but they are not a substitute for recording the provider runs.

## Sources

- [OpenAI: Prompt engineering best practices for ChatGPT](https://help.openai.com/en/articles/10032626-prompt-engineering-best-practices-for-chatgpt)
- Anthropic Interactive Tutorial and Anthropic Prompting Best Practices: use the assignment's
  resource-library links; access not verified in this session.
- Verified project context: `work/notebooks/w02_ml_task_framing.ipynb` and
  `docs/data-dictionary.md`.
