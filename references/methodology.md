# Methodology — from raw input to a sharp management report

This is the thinking workflow behind the report. The template
(`assets/one-page-linear-template.html`) is *how it looks*; this file is *how to
think and write*. Read both before starting.

## Phase 1 — Intake & triage (read everything, keep only what matters)

Read every supplied file before writing a single line. As you read, ruthlessly
sort into three buckets:

| Bucket | Examples | How to treat it |
|---|---|---|
| **核心主张 (core argument)** | the single most important claim, the "why now", the directional recommendation | Highest priority. This is the hero section and the verdict. |
| **支撑证据 (supporting evidence)** | data points, quotes, benchmarks, timelines, competitor moves | Keep 2–4 strongest per argument. Kill the rest. |
| **噪音 (noise)** | background context, process details, nice-to-know, caveats, disclaimers | Discard for the report. Note for your own understanding only. |

Management reports are exercises in compression. If a piece of information
doesn't directly support the core argument or a key insight, it doesn't belong
in the report. Move caveats to a footnote; move process details to an appendix
(only if asked).

**Flag every conflict.** If two sources disagree on a number, pick the most
authoritative and note the discrepancy. Don't silently resolve ambiguity.

## Phase 2 — Distill (turn raw into sharp)

- **Lead with the conclusion.** The hero section must state the thesis. If you
  can't write it in one sentence, you haven't understood it yet.
- **One idea per card.** A card with three bullet points is fine if they all
  support one idea. A card with three unrelated ideas is three cards.
- **Be directional, not exhaustive.** Management readers want to know "what
  should we do" and "why", not "here is everything we found". Err on the side
  of a clear direction over a balanced survey.
- **Use specific data, not adjectives.** "Revenue grew 23% YoY" beats "strong
  growth". "3 of 5 regions missed target" beats "mixed performance".
- **Label the unknown.** Where a critical fact is missing, write 【待补充】
  instead of guessing. Don't let the reader discover the gap later.
- **Attribute opinions.** "据销售VP反馈" / "一线门店口径" — separate what
  someone said from what is established fact.

## Phase 3 — Argument architecture (the report's spine)

Default arc for management reports — adapt section *names* to the domain, keep
the *logic*:

```
00  核心结论          hero section: one-liner thesis + verdict box with 总判断
01  背景 / 现状         current situation → TABLE or 2-col CARDS
02  关键洞察           the 2–3 things that matter → 2-col or 3-col CARD GRID
03  策略方向           directional moves → CARDS with accent colors
04  路径 / 取舍         the key tradeoff → A/B COMPARE (logic-strip or decision-model)
05  下一步 / 行动       what happens next → TIMELINE or FLOW
(opt) 附录              supporting data, methodology notes, disclaimers
```

This arc is "here's the answer → here's why → here's what to do → here's how".
Executives can stop reading at any point and have gotten value.

**Tone calibration:** if the user says "给老板看的" or "board-ready", keep
sections tight (3–5 cards each), cards short (2–4 bullets), and language
declarative (不是"可能可以考虑"，是"建议立即启动").

## Phase 4 — Build (see SKILL.md for mechanics)

Fill the template. Match component to content (catalog in SKILL.md). Then
self-check the gotchas (hero impact, scan test, font loading, dark-box
contrast, image fallback, numbering integrity).

### Component selection guide

| If you need to show… | Use… |
|---|---|
| A single thesis | Hero header + `.callout` or `.summary-box` |
| Two opposing ideas / perspectives | `.two-col` + `.card` |
| Three pillars / dimensions / findings | `.three-col` + `.card` |
| A phased evolution / roadmap | `.timeline` > `.stage` |
| A formula / decomposition | `.formula` |
| Two paths with pros/cons | `.logic-strip` or `.decision-model` |
| A process with steps and tags | `.path-map` > `.path-panel` |
| Structured comparison across dimensions | `.table-wrap` > `table` |
| Problems / risks / challenges | `.challenge-grid` |
| Anti-patterns / things to avoid | `.avoid-grid` |
| Roles or actors | `.role-map` |
| A single powerful close | `.summary-box` + `.summary-grid` |
| Multiple one-pagers in tabs | `.onepage-tabs` + `.onepage-stage` |

## Phase 5 — Iterate on feedback

Management reports get reviewed and revised. Common edits and how to do them
cleanly:

- **"Lead more with the conclusion"** → rewrite the hero lead and the first
  callout/verdict. Move the strongest claim earlier.
- **"Too long / too dense"** → kill cards that don't earn their space. Merge
  weak cards into bullet points. Move detail to an optional appendix.
- **"This section is weak"** → either strengthen with data or kill it entirely.
  A short strong report beats a long diluted one.
- **Add / remove a section** → renumber every `.section-kicker` and verify
  cross-references stay sequential.
- **"Change the framing"** → rewrite section h2s and kickers. A different frame
  often means different section names and card groupings.
- **Contrast / legibility complaints** → check dark-background blocks haven't
  inherited dark body text; confirm font loading works.

## Output format choice

- **Default = single self-contained HTML** (one-page linear scroll,
  on-screen and print-to-PDF friendly). This is the primary deliverable.
- **Offer docx** when the user signals formal circulation / sign-off
  ("发给客户", "走流程", "需要word版"). The same arc maps cleanly onto a
  Word doc via the `docx` skill.
- Save finished files to the working directory and surface to the user.
