# Automation Guide

This guide describes a production pipeline for delivering `Daily_Bilingual_Brief_YYYY-MM-DD.pdf` by 5:00 AM in `America/Los_Angeles`. It is implementation-agnostic: use the research, document-generation, storage, and scheduling tools available in your environment.

## Pipeline overview

Run the workflow as explicit stages with saved artifacts and validation gates:

```text
load history → collect → normalize → deduplicate → select
→ draft → fact-check → lay out → render → inspect → deliver → update ledgers
```

Do not allow a later stage to silently compensate for a failed earlier stage. For example, layout code should not truncate copy to make an overlong story pass.

## Suggested run schedule

Work backward from the 5:00 AM delivery target:

- Start research early enough to absorb source or rendering delays.
- Freeze the 10-story slate before final writing.
- Reserve a dedicated render-and-revise window.
- Complete delivery checks before the target rather than scheduling the first render at 5:00 AM.

Store timestamps in UTC and convert the display and delivery date using `America/Los_Angeles`, including daylight-saving transitions.

## Inputs and state

Each run should receive:

- target issue date and timezone;
- the prior seven published PDFs or their structured story records;
- the current story ledger;
- the current glossary ledger;
- source candidates and retrieval timestamps;
- the versioned editorial and design specification.

Use stable, machine-readable records even if the final output is a PDF.

### Story ledger example

```json
{
  "story_id": "AI-01",
  "topic": "example topic",
  "company": "example company",
  "first_covered": "2026-07-18",
  "last_covered": "2026-07-20",
  "facts_reported": ["fact fingerprint or concise normalized claim"],
  "prior_interpretation": "current editorial thesis",
  "next_trigger": "specific event or threshold",
  "status": "active"
}
```

### Glossary ledger example

```json
{
  "term": "term premium",
  "last_full_explanation": "2026-07-19",
  "contexts_explained": ["long-duration Treasury yields"],
  "new_context_required": true
}
```

Validate dates, required keys, enum values, and unique story IDs before research begins.

## Stage 1: collect and normalize

Gather primary sources first, then credible reporting that provides necessary confirmation or context. Preserve:

- canonical URL;
- source name and type;
- publication and retrieval time;
- title and normalized entities;
- relevant passages or structured facts;
- market, regulatory, or clinical identifiers where available.

Canonicalize URLs by removing tracking parameters while preserving the destination. Do not treat syndications of the same report as independent evidence.

## Stage 2: deduplicate and select

Compare candidate facts—not only headlines—against the prior seven days and ledger fingerprints. Cluster candidates by company, product, event, and underlying claim.

Reject candidates that only restate known facts. Mark a candidate as an update only when it contains a hard catalyst, meaningful data, or thesis-changing evidence. Enforce these selection gates programmatically where possible:

- exactly 10 selected stories;
- at least 7 new;
- no more than 3 updates;
- no more than 2 stories per company;
- no single broad theme above roughly 20–30%;
- cooldown rules satisfied or explicitly overridden with a reason.

Save the rejected-candidate reasons for auditability.

## Stage 3: draft and fact-check

Generate stories from a structured outline that contains the stable ID, status, source facts, prior coverage, thesis, and next trigger. Produce English first. Generate Chinese as a complete comprehension layer after the English argument is stable.

Run deterministic checks for required headings, story count, IDs, status values, and question count. Then perform an evidence review:

- every number has a source;
- dates and units are consistent;
- inference is clearly distinguished from reported fact;
- the takeaway does not overstate the evidence;
- the Chinese preserves the English conclusion and uncertainty.

## Stage 4: compose the document

Build content with flow-based components. Cards must expand with content and move intact when they cannot fit. Shorten displayed URLs while attaching the canonical URL as the hyperlink target.

Recommended output sequence:

1. Cover and issue overview.
2. Ten stories grouped or clearly marked by category.
3. Today's Watchlist / 今日关注.
4. Five Terms Today / 今日五个关键词.
5. Sources & Method / 来源与方法.

Generate the final filename from the Los Angeles issue date, not the server's local date.

## Stage 5: render and inspect

PDF creation is not complete until every page has been rendered to an image and inspected.

Automated checks should cover:

- valid PDF and expected page count range;
- non-empty text extraction on content pages;
- page boxes and safe-margin bounds;
- missing-glyph or replacement-character detection;
- URL annotations inside page bounds;
- duplicate story IDs and repeated boilerplate;
- unexpectedly small font sizes where the renderer exposes them.

Visual review should inspect each full page and a mobile-reading crop or zoom for overflow, clipping, overlaps, poor contrast, card splitting, stranded headings, low-resolution images, and broken Chinese glyphs.

When a page fails, return to layout, re-render the complete PDF, and repeat the checks. Do not patch only the preview image.

## Stage 6: deliver

Before delivery, assert:

- filename matches `Daily_Bilingual_Brief_YYYY-MM-DD.pdf`;
- the issue date is correct in `America/Los_Angeles`;
- the PDF opens and all pages render;
- the delivered file hash matches the QA-approved file;
- the message contains only a short readiness note and the PDF link or attachment.

Keep the previous successful issue available until the new delivery is confirmed.

## Stage 7: commit editorial memory

Only after successful delivery, atomically update the story and glossary ledgers with the content actually published. Record the issue file hash and specification version alongside the update.

If delivery fails, do not mark candidates as covered; otherwise the next run may incorrectly suppress stories the reader never received.

## Failure handling

- **Source unavailable:** use another authoritative source or drop the candidate; never invent missing evidence.
- **Too few new stories:** widen source collection while preserving the quality bar; do not relabel updates as new.
- **Translation uncertainty:** preserve the English technical term and add a clear Chinese explanation.
- **Overflow:** add a continuation page or simplify the component; never truncate analysis or shrink it below comfortable reading size.
- **Image failure:** remove the image and preserve the story; imagery is optional.
- **Deadline pressure:** deliver a fully checked, simpler design instead of an unstable decorative layout.

## Observability and audit trail

Retain a run manifest containing:

- run and specification version;
- issue date and timezone;
- source retrieval timestamps;
- selected and rejected story IDs;
- validation results and exceptions;
- render iterations;
- final file path, page count, and hash;
- delivery timestamp and outcome;
- ledger update outcome.

This record makes repetition, source, layout, and delivery failures diagnosable without exposing unpublished research in the public PDF.

## Acceptance criteria

A run succeeds only when editorial selection, bilingual completeness, PDF rendering, full-page visual QA, mobile-reading QA, hyperlink checks, naming, delivery, and ledger persistence all pass. The PDF is the only reader-facing artifact.
