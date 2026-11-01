# Week 3 — Map the content, give it a face

## One-line claim

I turn search-performance data into a testable page-priority workflow for SEO editors.

**Person:** An SEO lead at a content-led SaaS company who owns the editorial refresh backlog.  
**One action:** Book a 20-minute content-health review.

This describes the project direction, not a proven model outcome. The current work frames the decision and checks the starter data; it does not yet show that a model improves prioritization.

## Content map

Keep the site to one page with four anchored sections. The case studies stay together under Work; no extra pages are needed.

| Section | What belongs here | Why it earns its place |
|---|---|---|
| Home | The one-line claim, a short evidence note, and the single CTA. | A visitor can tell who the work is for and what decision it supports. |
| Work | Three cases: framing the page-priority problem; checking what the decline label actually means; choosing a top-50 evaluation question. Each case uses Problem / What I did / What came of it. | These are the evidence for the claim, with limits stated beside the work. |
| About | A short note on how I work: check the measure, make the decision explicit, and report only what the evidence supports. | Helps the SEO lead understand the judgment behind the analysis. |
| Contact | Repeat the same “Book a 20-minute content-health review” action and link it to a real contact route. | Gives the visitor one clear next step. Do not publish a fake booking link or placeholder address. |

### Proof still needed before publishing as a finished portfolio

- Execute the warehouse data-contract notebook against the real gated data and replace any test-only outputs.
- Build and evaluate the time-safe ranking workflow on a held-out set; report the real Precision@50 and baseline comparison.
- Capture a real, legible view of the resulting review queue and its reason codes, if that interface is built.
- Add the author's real contact destination. No booking URL or email is invented here.
- Add a real portrait only if wanted; do not generate a synthetic personal photo.

## Visual identity

### Type

Use **IBM Plex Sans**, a free type family, in Regular and SemiBold. Keep one family across headings, body copy, labels, and buttons.

- Page title: 32–40 px, SemiBold.
- Section heading: 24–28 px, SemiBold.
- Body: 17–19 px, Regular; keep paragraphs short and line length comfortable.
- Labels and chart notes: 12–14 px, Medium.

### Palette

| Role | Color | Use |
|---|---|---|
| Signal teal | `#2F746D` | Links, the primary CTA, and one important chart series. |
| Near-black | `#202927` | Headlines and body text. |
| Warm paper | `#F7F7F2` | Main background. |
| Soft sage | `#DDE8E2` | Quiet cards, chart rails, and supporting surfaces. |

Use the neutral colors for most of the page. Teal is an accent, not a background wash. Let real evidence carry the visual interest.

### Mark and reusable style note

The small mark is three incoming signal rows becoming ordered bars. It labels this project, not the author's personal identity. The SVG logo and favicon are simple enough to reproduce without an image model.

> Quiet, clear, evidence-first. Use IBM Plex Sans, warm paper, near-black text, and one signal-teal accent. Give content generous whitespace; align to a simple grid; use restrained borders and no decorative gradients. Keep the claim and one CTA easy to find. Show real project evidence at readable size. Never use generated imagery to imply a working interface, result, or personal portrait.

## Image choices

The case-study image should be the real label-distribution chart made from the anonymized starter CSV: 30,000 content items across 32 pseudonymized clients. It shows the observed retrospective label mix—16,262 items (54.2%) labeled `down`—and explicitly says it is not a prediction, model result, or refresh effect.

For connective tissue, choose **Option A**, the quiet “signals in → review order” vector, and keep it small. It describes the intended decision flow without pretending a model or interface already exists.

**Rejected:** Option B's magnifier is a generic search symbol and adds no evidence. Option C's page cards read like a product mockup, which could imply an interface that has not been built. Neither earns space over the real chart.

The available workspace has no image-generation model/tool. The three alternatives are original, assistant-drafted SVG concepts rendered locally, **not** AI image-model outputs. No synthetic portraits, fake product screenshots, or invented results are included. Replace the connective vector with a carefully reviewed generated asset only if it adds something the real work cannot show.

## Files

- [One-page sitemap sketch](./sitemap_sketch.png)
- [Identity board](./assets/identity-board.png)
- [Image options and curation board](./assets/image_curation_board.png)
- [Observed label chart](./assets/decline-label-distribution.png)
- [Selected signal-to-queue vector](./assets/decision-path.svg)
- [Option A](./assets/option_a_signal_to_queue.svg) · [Option B](./assets/option_b_magnifier.svg) · [Option C](./assets/option_c_page_cards.svg)
- [Project logo](./assets/logo.svg)
- [Favicon](./assets/favicon.svg)
- [Case-study copy](./case_studies.md)
