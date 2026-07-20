---
name: daily-bilingual-briefing-pdf
description: Generate an English-first, fully bilingual, magazine-style daily intelligence PDF covering AI, markets, and healthcare/medtech, with strong anti-repetition, terminology support, and strict layout QA.
---

# Daily Bilingual Briefing PDF Skill

## 1. Purpose

Create a premium, highly readable daily intelligence magazine for Will that is ready by early morning.

The briefing should help him:
- understand the most consequential developments in AI & technology, financial markets & investing, and healthcare & medtech;
- learn natural professional English while still having Chinese support;
- identify what changed, why it matters, and what to watch next;
- avoid repeated narratives and low-signal news;
- follow up later using stable story IDs and suggested questions.

## 2. Delivery Contract

- Output format: downloadable PDF only.
- Do not generate HTML, websites, ZIP bundles, or GPT Sites packages.
- File name: `Daily_Bilingual_Brief_YYYY-MM-DD.pdf`.
- Chat delivery: one short message saying the PDF is ready, followed by the attachment/link.
- Target availability: 5:00 AM America/Los_Angeles.
- Typical length: 12–20 pages, with no hard cap.
- Readability has priority over page count.

## 3. Editorial Scope

Cover exactly 10 high-signal stories across:
- AI & Technology
- Financial Markets & Investing
- Healthcare & Medtech

Prioritize:
- primary sources;
- company filings and investor-relations materials;
- FDA and regulator notices;
- policy documents;
- clinical publications and trial data;
- real capital flows and market pricing;
- credible reporting;
- developments relevant to EP, medical devices, semiconductors, AI products, and market positioning.

Avoid:
- recycled commentary;
- generic trend pieces without new evidence;
- duplicated facts from prior issues;
- sensational headlines without operational or investment relevance.

## 4. Anti-Repetition System

Before selecting stories:
1. Review the prior 7 days of briefings.
2. Maintain a rolling story ledger containing:
   - story ID;
   - topic/company;
   - first-covered date;
   - last-covered date;
   - facts already reported;
   - prior interpretation;
   - next trigger;
   - active/inactive status.
3. Maintain a rolling glossary ledger containing:
   - term;
   - last full explanation date;
   - contexts already explained;
   - whether a new context justifies re-explanation.

Daily composition:
- At least 7 of 10 stories must be genuinely new.
- No more than 3 may be continuing-story updates.
- A continuing story may return only for:
  - a hard catalyst;
  - meaningful new data;
  - a thesis-changing development.
- Theme repetition is allowed; fact repetition is not.
- Previously explained background should be compressed to 1–2 sentences.
- Remove a continuing story after 3 days without a meaningful update.
- Default cooldowns:
  - ordinary company news: 3 days;
  - broad industry commentary: 5–7 days;
  - same product introduction: 7 days.
- No more than 2 stories about the same company.
- No more than 20–30% of the issue should be devoted to one broad theme.

For continuing stories, include:
- What’s new today / 今日新增
- What has not changed / 未改变的判断
- Why this changes the picture / 为什么值得再提
- Next trigger / 下一观察节点

## 5. Story Structure

Assign a stable story ID:
- `AI-01`
- `MKT-02`
- `MED-03`

Assign one status:
- NEW / 全新
- UPDATE / 进展
- THESIS CHANGE / 判断变化
- WATCH / 观察中

Every story must include:
1. 10-second takeaway / 10秒看懂
2. Why Will should care / 为什么与你有关
3. What happened / 发生了什么
4. Why it matters / 为什么重要
5. Signal vs. noise / 信号还是噪音
6. Next trigger / 下一观察节点
7. Ask next / 可以继续追问

Include 1–3 bilingual suggested follow-up questions per story.

## 6. English-First Bilingual Hierarchy

English is the primary reading layer.

### English treatment
- Larger font size than Chinese.
- Darker color and stronger visual weight.
- Appears first in each section.
- Natural editorial English, not literal translation.
- Use professional phrasing suitable for business, markets, and medtech.

### Chinese treatment
- Appears directly below the English.
- Slightly smaller font size.
- Softer color and lighter weight.
- Functions as fast comprehension support.
- Must remain fully readable and complete.

### Visual priority rule
The reader’s eye should naturally land on English first, then use Chinese for clarification.

Do not:
- make English light gray to the point of being visually secondary;
- put Chinese first in the content stack;
- reduce English to a short summary while Chinese contains the real analysis;
- duplicate both languages at identical visual weight if it makes the page dense.

## 7. Key-Term Cards

Add a bilingual key-term card when a moderately technical concept could block understanding.

Each card must include:
- What it is / 它是什么
- What it means here / 在本文语境中意味着什么
- Do not confuse it with / 不要与什么混淆

Explain only terms that materially affect understanding.

Examples of terms that often require explanation:
- prompt injection;
- inference capacity;
- Brent crude;
- term premium;
- core CPI;
- Instructions for Use (IFU);
- dual-energy ablation;
- non-inferiority;
- free cash flow;
- implied volatility.

## 8. Five Terms Today

End each issue with:
`Five Terms Today / 今日五个关键词`

For each term include:
- English term;
- Chinese name;
- plain-language definition;
- one authentic English usage example;
- one natural Chinese translation of that exact example.

Hard rule:
- Each example must demonstrate the term’s actual meaning in context.
- Do not reuse the same sentence template.
- Do not write placeholders such as:
  - “X is the key term to watch today.”
- Every example must be semantically specific to the term.

## 9. Visual Design System

Style:
- premium editorial-tech;
- calm, high-end, and comfortable;
- cream or light neutral paper background;
- dark information cards;
- restrained category accent colors;
- strong typographic hierarchy;
- generous whitespace;
- selective bolding;
- page numbers;
- clean section dividers;
- signal gauges, term cards, pull quotes, and compact data boxes.

Recommended category colors:
- AI: blue-violet
- Markets: amber/gold
- Medtech: teal/green

Preferred composition:
- one story per page;
- use a second page for a story when needed;
- never compress content solely to meet a page-count target.

Images:
- optional;
- use only when legally and technically usable;
- include small bilingual credits;
- never let image sourcing cause the briefing to fail.

## 10. Strict Layout-Safety Rules

No text, border, card, chart, caption, source line, or decorative element may:
- cross the page boundary;
- bleed beyond the safe margin;
- protrude outside its container;
- be clipped;
- overlap another element.

Required safeguards:
- clear safe margin on all four sides;
- sufficient internal padding in every card;
- automatic wrapping for long English words, product names, URLs, and bilingual headings;
- shorten display URLs while preserving clickable hyperlinks;
- never use fixed-height cards for variable-length bilingual content;
- move an entire bordered card to the next page if it does not fit;
- avoid splitting glossary cards, source boxes, callouts, and bordered UI elements across pages;
- prevent widows, orphans, and stranded headings;
- never solve overflow by shrinking text below comfortable iPhone-reading size;
- if a story is too dense, continue on a clearly labeled second page.

## 11. Quality Assurance

Before delivery:
1. Render every PDF page.
2. Review full-page view.
3. Review a closer mobile-reading zoom.
4. Check:
   - text wrapping;
   - card boundaries;
   - safe margins;
   - Chinese glyphs;
   - English product names;
   - source links;
   - page numbers;
   - card splitting;
   - glossary examples;
   - duplicated phrases;
   - repeated stories;
   - tiny text;
   - low-resolution images.
5. If any text or UI element overflows:
   - revise the layout;
   - re-render;
   - re-check.
6. If a complex design element causes instability:
   - simplify the design;
   - preserve complete bilingual content;
   - do not fail the entire briefing.

## 12. Final Pages

The issue should end with:
1. Today’s Watchlist / 今日关注
   - concise;
   - actionable;
   - no more than 5–8 items.
2. Five Terms Today / 今日五个关键词
3. Sources & Method / 来源与方法
   - source name;
   - publication date;
   - clickable link;
   - note explaining anti-repetition and editorial selection.

## 13. Core Editorial Principle

Topics may repeat, but facts must not.

English leads.
Chinese supports.
Readability beats page count.
New information must change understanding or action.
