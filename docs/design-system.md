# Design System

This document turns the visual rules in `SKILL.md` into a practical layout specification. The goal is a calm, premium editorial PDF that remains comfortable on an iPhone and makes English the natural first reading layer.

## Design principles

1. **English leads.** English appears first and carries the strongest size, color, and weight.
2. **Chinese supports.** Chinese is complete and readable, but visually quieter.
3. **Whitespace is functional.** Space separates ideas, exposes hierarchy, and reduces bilingual density.
4. **Components grow with content.** Variable-length text must never be forced into a fixed-height card.
5. **Readability beats page count.** Continue a dense story on a labeled second page instead of shrinking type.

## Page system

- Use a cream or light-neutral paper background.
- Keep a clear safe margin on all four sides; apply the same margin grid throughout the issue.
- Prefer one story per page. Use a continuation page when the bilingual copy, term cards, or sources cannot fit comfortably.
- Place page numbers consistently outside the main content flow but inside the safe margin.
- Keep headings with the content they introduce and avoid widows, orphans, and stranded labels.

For automated layouts, define the safe rectangle once and require every text box, line, card, chart, image, caption, and page number to remain inside it.

## Color roles

Use category accents sparingly. They identify sections and statuses; they should not compete with the content.

| Role | Direction | Typical use |
| --- | --- | --- |
| Paper | Cream or warm light neutral | Page background |
| Ink | Near-black or deep navy | English body and primary headings |
| Secondary ink | Softer charcoal | Chinese body and metadata |
| Dark card | Deep neutral with high-contrast text | Key data, takeaways, or pull quotes |
| AI accent | Blue-violet | AI labels, rules, small icons |
| Markets accent | Amber or gold | Markets labels and data cues |
| Medtech accent | Teal or green | Healthcare and medtech labels |

Check contrast in the rendered PDF, not only in the source layout. Avoid pale English text that makes Chinese appear primary.

## Type hierarchy

Recommended relative hierarchy:

| Element | English treatment | Chinese treatment |
| --- | --- | --- |
| Issue title | Largest, bold, dark | Smaller subtitle beneath |
| Story headline | Large, strong weight | Smaller, medium weight below |
| Section label | Compact uppercase or small caps | Short Chinese label alongside or beneath |
| Body | Comfortable mobile-reading size | Slightly smaller and softer, never tiny |
| Metadata/source | Compact but readable | Match only when bilingual metadata is required |

Use typefaces with reliable Latin punctuation, numbers, and Simplified Chinese glyph coverage. Test mixed strings containing product names, acronyms, percentages, and Chinese punctuation before committing to a font stack.

## Bilingual composition

Within every section:

1. Place natural editorial English first.
2. Add a modest vertical gap.
3. Place the complete Chinese support directly below.
4. Add a larger gap before the next conceptual section.

Do not place the two languages in narrow side-by-side columns on mobile-oriented pages. Do not give both layers identical visual weight. Chinese must not contain analysis omitted from English.

## Core components

### Story header

Include the stable story ID, category, status, and bilingual headline. Allow long product names and bilingual headings to wrap. The status is one of `NEW / 全新`, `UPDATE / 进展`, `THESIS CHANGE / 判断变化`, or `WATCH / 观察中`.

### Ten-second takeaway

Use a visually distinct card near the top. Keep the English conclusion dominant and the Chinese translation immediately below. The card may grow vertically and should move intact to the next page when it cannot fit.

### Analysis sections

Use clear bilingual labels for:

- Why Will should care / 为什么与你有关
- What happened / 发生了什么
- Why it matters / 为什么重要
- Signal vs. noise / 信号还是噪音
- Next trigger / 下一观察节点
- Ask next / 可以继续追问

Avoid excessive boxes. A strong heading and whitespace are often clearer than another border.

### Continuing-story block

Show four concise rows: what is new, what has not changed, why the update changes the picture, and the next trigger. Visually separate new evidence from compressed background.

### Key-term card

Keep all three fields together: what it is, what it means here, and what not to confuse it with. Do not split the card across pages.

### Signal gauge and data box

Use these only when they encode a real editorial judgment or a compact set of numbers. Label the basis of the judgment and avoid decorative precision.

### Sources

Display a short source name and publication date. Shorten the visible URL while preserving the full clickable hyperlink. Keep the source line inside the safe rectangle.

## Image use

Images are optional. Include one only when it adds evidence or orientation and is legally and technically usable. Add a small bilingual credit, verify resolution at final size, and let the issue ship without images when sourcing would delay it.

## Overflow prevention

- Enable wrapping for long English words, URLs, product names, and bilingual headings.
- Do not use fixed heights for content-driven components.
- Keep internal padding on every side of a card.
- Treat bordered cards, glossary entries, source boxes, and callouts as indivisible blocks.
- Continue a story on another page before reducing type below a comfortable phone-reading size.
- Recalculate layout after font substitution; glyph metrics can change wrapping and page breaks.

## Visual QA checklist

Render every page and inspect it twice: once as a full page and once at a mobile-reading zoom.

- All elements remain inside the page and safe margins.
- No text is clipped, overlapped, or protruding from a card.
- Chinese glyphs, punctuation, and weights render correctly.
- English product names and long technical terms wrap correctly.
- Page numbers are present and consistent.
- Links are clickable and their display text is concise.
- No bordered component is split across pages.
- Body type is comfortable and primary English is visibly dominant.
- Images are sharp and credits remain readable.

Any failure requires a layout revision and a complete re-render. If a complex visual remains unstable, simplify it while preserving the full bilingual content.
