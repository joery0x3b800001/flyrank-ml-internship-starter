# Portfolio copy: content-refresh scoring

## Voice card

**Plain, direct, curious, careful, practical, unshowy.**

Standing instruction for my Claude Project: Use this voice in all drafts. Ask one focused
question at a time when my decisions or evidence are unclear. Use my actual words and project
artifacts; do not invent experience, results, or opinions. Keep claims within the evidence.

## Who this is for and what to do

For an SEO lead at a content-led SaaS company who owns the editorial refresh backlog and
needs to decide which pages an editor should review first. The one action:
**Book a 20-minute content-health review.**

## Case 1 — Framing a refresh-priority queue

### The problem

An editor has more pages to review than time. “Predict decline” alone does not say what the
editor should do with the result, and a wrong priority can waste review time or leave a
slipping page unattended.

### What I did

I framed the work as a ranking/scoring task: help an editor decide which pages to inspect
first. I made the content item the unit of analysis and treated the score as decision support,
not an automatic instruction to refresh. I chose a top-50 review queue as the concrete
capacity assumption to test.

### What came of it

The project now has a specific user, decision, and output to build toward. This is framing,
not a completed or validated scoring model; I have not shown that a model improves an editor's
decisions.

## Case 2 — Separating a trend label from a future prediction

### The problem

The starter data contains a decline label, but a label is only useful if I know what it
measures. Calling this a future prediction would overstate what a single snapshot can show.

### What I did

I checked the label definition before choosing a target. In this dataset, `down` means
impressions in the latest 30 days were more than 20% below the preceding 30 days. I recorded
the resulting binary value as a **retrospective proxy** and identified `trend_direction` and
`trend_pct` as label sources that must not be used as features. I also noted that same-window
signals can leak the outcome; a future-risk claim needs features cut off before a later
outcome window.

### What came of it

The 30,000-page slice has 16,262 pages labeled down (54.2%). That is a description of this
slice, not a held-out model result or evidence that a future decline can be predicted. The
label check also surfaced data caveats: 1,205 rows use `avg_position = 0` to mean no position
data, and `trend_pct` is missing for 3,388 rows. Those values need careful handling rather
than interpretation as ordinary measurements.

## Case 3 — Making the score useful to an editor

### The problem

An overall model metric can look good without answering the editor's practical question:
“If I review only a small queue, how many of the flagged pages are actually declining?”

### What I did

I chose Precision@50 as the primary success metric because it measures the share of declining
pages in the 50 highest-ranked items. I set the comparison before training: evaluate on
clients held out from training, compare against that holdout's decline prevalence and a
simple rule baseline. The full-slice prevalence gives context only: a random top-50 list
would average about 27 declining pages at the slice's 54.2% rate.

I also want the eventual queue to show concise reason codes grounded in observed signals,
so an editor can review why a page was surfaced. That is a design requirement, not a feature
I have built or validated yet.

### What came of it

The evaluation question is defined, and it is tied to a real review limit. No model has been
evaluated yet, so there is no Precision@50 result to report and no claim that the queue beats
a rule. The next step is to construct time-safe features and an outcome window, then test
whether the model earns its added complexity.

## About

I’m working on a content-refresh scoring project: the goal is to help an editor decide which
pages are worth reviewing first. I start by checking what the data actually measures, then
make the decision and the limits of the evidence explicit. I’m still building the model, so
I’ll show measured results when they exist rather than promise a lift in advance.

## Contact

**Have a content backlog you need to triage? Book a 20-minute content-health review.**

## Before / after

**Generic AI line:** “I leverage data-driven insights to empower content teams with actionable,
results-oriented optimization strategies.”

**Edited version:** “I’m testing whether a ranked list can help an editor decide which pages to
review first.”

The edited version names the actual work, its user, and the decision. It does not claim a
result the project has not measured.

## Drafting note

This draft is grounded in the completed research-question and ML-task-framing notebooks. No
personal interview answers or unmeasured project outcomes have been invented. The case copy
should be read aloud and adjusted to the author's own wording before publication.
