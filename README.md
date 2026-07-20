# Daily Bilingual Briefing Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-2f855a.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-5b5bd6.svg)](CHANGELOG.md)

An English-first, Chinese-supported editorial system for producing a polished daily intelligence PDF across AI and technology, financial markets and investing, and healthcare and medtech.

The project is a reusable specification for an AI agent or automated pipeline. It defines what to research, how to reject repeated or low-signal stories, how to structure bilingual analysis, and how to verify every page before delivery.

## Sample output

- [Full sample issue](examples/Daily_Bilingual_Brief_Sample.pdf) — a complete magazine-style briefing.
- [English-first visual demo](examples/English_First_Visual_Demo.pdf) — the approved bilingual hierarchy and page treatment.

GitHub can preview both PDFs in the browser. Download them for the most reliable font and hyperlink rendering.

## Key features

- Exactly 10 high-signal stories across three editorial domains.
- At least 7 genuinely new stories per issue and no more than 3 meaningful updates.
- A rolling seven-day story ledger with stable IDs, prior facts, thesis state, and next triggers.
- English as the primary reading layer, with complete Chinese directly beneath it.
- Bilingual key-term cards that explain technical concepts in context.
- A closing watchlist, five practical vocabulary terms, and a transparent source record.
- Strict PDF layout QA for margins, wrapping, card boundaries, links, Chinese glyphs, and mobile readability.

## Editorial workflow

```text
Review prior 7 days and ledgers
            ↓
Collect primary-source candidates
            ↓
Score novelty, consequence, relevance, and evidence
            ↓
Select 10 stories and assign stable IDs/statuses
            ↓
Write English-first analysis and Chinese support
            ↓
Lay out, render every page, inspect, and revise
            ↓
Publish the PDF and update both ledgers
```

The three domains are intentionally broad, but the selection bar is narrow: prefer primary sources, filings, regulator notices, clinical evidence, policy documents, real pricing or capital flows, and credible reporting. Reject recycled commentary and headlines without operational or investment relevance.

See [Editorial Method](docs/editorial-method.md) for the complete selection and writing process.

## Anti-repetition by design

Topics may repeat; facts must not.

Before composing an issue, review the prior seven days and compare every candidate against a rolling story ledger. A continuing story returns only when there is a hard catalyst, meaningful new data, or a thesis-changing development. Background already explained is compressed, ordinary company news receives a three-day cooldown, broad commentary receives five to seven days, and the same product introduction receives seven days.

The result is a daily briefing that advances the reader's understanding instead of retelling yesterday's narrative.

## English-first bilingual design

English appears first, larger, darker, and with stronger editorial weight. Chinese follows immediately as a complete but visually quieter comprehension layer. The hierarchy is designed to support professional English learning without making the analysis slower to use.

Read the full component, color, typography, spacing, and overflow guidance in the [Design System](docs/design-system.md).

## Use the skill

Clone the repository and ask a capable research-and-document agent to follow `SKILL.md`:

```bash
git clone https://github.com/waileungl/daily-bilingual-briefing-skill.git
```

Example request:

```text
Use SKILL.md to create today's Daily Bilingual Briefing PDF.
Review the prior seven issues and both ledgers first. Research exactly
10 high-signal stories, render every page, perform layout QA, and return
only Daily_Bilingual_Brief_YYYY-MM-DD.pdf.
```

For production scheduling, ledger schemas, pipeline stages, failure handling, and delivery checks, see the [Automation Guide](docs/automation-guide.md).

## Repository map

```text
.
├── SKILL.md
├── README.md
├── LICENSE
├── CHANGELOG.md
├── examples/
│   ├── Daily_Bilingual_Brief_Sample.pdf
│   └── English_First_Visual_Demo.pdf
├── docs/
│   ├── design-system.md
│   ├── editorial-method.md
│   └── automation-guide.md
└── social/
    ├── x-launch-en.md
    └── x-launch-zh.md
```

## Roadmap

- Add machine-readable story and glossary ledger templates.
- Add reference rendering and overflow-detection scripts.
- Add a source-quality and novelty scoring worksheet.
- Add optional CI checks for links, filenames, and PDF page geometry.
- Publish anonymized example ledgers spanning a full seven-day cycle.

## Attribution

The original editorial specification and sample artifacts are maintained by [@waileungl](https://github.com/waileungl). Contributions and adaptations are welcome; preserve source attribution when redistributing the included examples.

## License

Released under the [MIT License](LICENSE).
