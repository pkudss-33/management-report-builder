---
name: management-report-builder
description: >-
  Turn strategic thinking into a polished, one-page linear management /
  strategy report as a single self-contained HTML file (print-to-PDF ready),
  with a clean modern corporate design system. Use this skill WHENEVER the user
  asks for a 管理摘要 (management summary), 一页纸摘要 (one-page brief), 核心策略报告
  (core strategy report), 管理报告 (management report), one page, one-pager, executive
  summary, strategy memo, or board briefing — even just "帮我写个一页纸", "整理成管理报告",
  "做个核心策略摘要", or "生成 one page". Also use when iterating on a management
  report already produced this way (adding sections, swapping content, fixing layout).
  The hallmark: concise strategic narrative in, one clean linear-scroll one-page report out.
  Defaults to HTML; can also output a Word .docx for formal circulation.

  **This skill is for management / strategy reports.** For research reports
  (field research, multi-source interview synthesis, case studies, competitor
  deep-dives), use `huangwei-report-builder` instead. The difference: management
  reports are executive-facing, conclusion-first, dense but scannable;
  research reports are evidence-heavy, multi-section, methodology-explicit.
---

# Management Report Builder

Turn strategic thinking into a polished, one-page linear management report.
The value is twofold: (1) a disciplined **top-down narrative workflow** that
forces the single most important argument to the surface, and (2) a proven
**clean corporate design system** — thin modern fonts, cool-tone palette,
grid-based cards — so the result looks like a senior strategy deliverable,
not a generic document.

## When this applies

The user asks for a management summary, one-page brief, strategy memo, executive
briefing, board update, or any "one page" / "一页纸" / "管理报告" deliverable.
The input may be messy — meeting notes, scattered data points, strategic
directions, org charts — and the output is a single, linear-scroll, visually
structured HTML page that an executive can read in under 10 minutes.

**Key differentiator from `huangwei-report-builder`:**
- **Management Report (this skill):** executive-facing, concise, one-page linear
  layout, cool corporate aesthetic, thin modern sans-serif fonts. Focus on
  decisions, directions, and tradeoffs — not exhaustive evidence.
- **Research Report (huangwei):** evidence-heavy, multi-section arc, warm
  editorial serif design, methodology-explicit. Focus on synthesis from
  multiple field-research sources.

If the task feels like a "strategy one-pager" or "board briefing" → use this skill.
If it feels like a "research paper" or "field study" → use `huangwei-report-builder`.

## Workflow

### 1. Read the methodology first
Read `references/methodology.md` in full. It defines the five phases (intake →
distill → argument spine → build → iterate) and writing rules specific to
management reports (lead with the conclusion, one idea per card, be directional,
design for scanning). Don't skip — it's what makes the report *sharp*, not
just pretty.

### 2. Distill the input
Read all supplied materials. Management reports are exercises in compression:
of 20 pages of notes, the report should surface the 3–5 things that matter.
Sort each piece into:
- **Core argument** (the one thing the reader must remember)
- **Supporting evidence** (2–4 data points / facts per argument)
- **Direction / decision** (what should happen next)
Discard everything else.

### 3. Architect the argument
Lay out sections using the default arc adapted for management reports:

```
00  核心结论          one-liner + VERDICT / KEY INSIGHT box
01  背景 / 现状       the current situation in 2–3 cards or a table
02  关键洞察          the 2–3 things that matter → card grid
03  策略方向          directional moves → numbered or card layout
04  路径 / 取舍       the key either/or → A/B compare
05  下一步 / 行动     what happens next → timeline or flow
(opt) 附录 / 数据      supporting data — trim aggressively
```

Adapt section *names* to the domain; keep the top-down conclusion-first logic.

### 4. Build the HTML report from the template
Copy `assets/one-page-linear-template.html` to your workspace. Keep its
`<style>` block intact (that IS the design system) and fill in the content,
replacing `[[...]]` placeholders. Match each piece of content to the right
component:

| Component | CSS class | Use for |
|---|---|---|
| **Hero header** | `.hero` | Report title, eyebrow label, one-line lead |
| **Section head** | `.section-head` + `.section-kicker` | Numbered section header with kicker label |
| **Card grid (2-col)** | `.two-col` > `.card` | Side-by-side comparison, two perspectives |
| **Card grid (3-col)** | `.three-col` > `.card` | Three pillars, three options, three findings |
| **Card (accented)** | `.card.accent-blue` etc. | Color-coded key points (blue/green/amber/red/teal) |
| **Timeline** | `.timeline` > `.stage` | Phased progression, roadmap, evolution |
| **Logic strip** | `.logic-strip` > `.logic-card` | Two ideas connected by an operator/arrow |
| **Formula row** | `.formula` | A = B + C + D decomposition |
| **Voice / perspective grid** | `.voice-grid` > `.voice-card` | Multiple voices/perspectives/lenses |
| **Challenge grid** | `.challenge-grid` > `.challenge-card` | Problems, risks, challenges |
| **Path map** | `.path-map` > `.path-panel` | Process flows, decision paths, journey steps |
| **Decision model** | `.decision-model` > `.model-card` | Two models side-by-side with images |
| **Role map** | `.role-map` > `.role-card` | Org roles, responsibilities, actors |
| **Base map** | `.base-map` > `.base-card` | Foundation / infrastructure elements |
| **Avoid / warning grid** | `.avoid-grid` > `.avoid-item` | Anti-patterns, risks to avoid, red flags |
| **Table** | `.table-wrap` > `table` | Structured comparison, OS/dimension mapping |
| **Callout** | `.callout` | A single key insight, left-border accent |
| **Panel** | `.panel` | Inline bordered content box |
| **Summary box** | `.summary-box` | The final synthesis, prominent close |
| **Summary grid** | `.summary-grid` > `.summary-tile` | Key takeaways in compact tiles |
| **Flow** | `.flow` | Horizontal process steps (6-col) |
| **One-page tabs** | `.onepage-tabs` + `.onepage-stage` | Embed project one-pagers in tabs |
| **Progress bar** | `.progress` | Fixed gradient reading-progress indicator |
| **Tags / pills** | `.tags` > `span` | Compact labels on path steps |

To re-skin for a different brand/subject, change only the `:root` CSS variables,
not individual components.

### Theme selection (built-in alternative themes)

The template includes two complete themes. Switch between them by changing the `<html>` tag:

| Keyword triggers | Theme | `<html>` tag |
|---|---|---|
| (default, no keyword) | **Cool Corporate** — blue-centric, thin sans-serif (weight 300), white/gray background | `<html lang="zh-CN">` |
| **"reflection格式"** / **"绿色主题"** / **"简洁主题"** | **Reflection** — deep forest green on warm cream, all sans-serif (Inter + Noto Sans SC), tight headings, generous whitespace. Inspired by reflection.ai | `<html lang="zh-CN" data-theme="reflection">` |

When the user includes ANY of the keywords "reflection格式", "绿色主题", or "简洁主题" in
their request, activate the Reflection theme by setting `data-theme="reflection"` on the
`<html>` tag. The CSS overrides are already in the template — no need to write new styles.

### 5. Self-check before delivering
- **Hero impact:** the hero section alone should communicate the entire report's
  thesis. If the eyebrow + h1 + lead don't tell the story, rewrite them.
- **One idea per card:** each card should make exactly one point. Split cards
  that try to do too much.
- **Scan test:** a reader should understand the argument by reading only the
  section kickers, h2s, and card h3s. Everything else is detail.
- **Font loading:** the template loads Inter + Noto Sans SC from Google Fonts.
  Confirm the `<link>` tags are intact.
- **Dark boxes:** if you add any dark-background block, give its `<p>` a light
  color explicitly — the global `color` will otherwise make it unreadable.
- **Images:** every `<img>` has `loading="lazy"` + an `onerror` fallback.
  Prefer base64 for offline rendering.
- **Numbering integrity:** section kickers run sequentially; re-verify after
  any add/remove.
- **Render check:** always render/scroll through the full page to confirm
  layout, then eyeball the hero, a card-heavy section, and any dark box.

### 6. Deliver & iterate
Save to the working directory as `<name>.html`, present with a short summary
of the report's core argument. On revisions, follow Phase-5 guidance in the
methodology (renumber sections, reframe comparisons honestly, kill weak cards).
Offer a Word `.docx` version when the user signals formal circulation.

## Output format
Default: one self-contained `.html` (CSS inline, images inline or
lazy-with-fallback), print-to-PDF friendly. The layout is a **linear-scroll
single page** — the "one page" is literal. Switch to `.docx` when the user
wants a formal circulating document.

## Files
- `references/methodology.md` — the thinking workflow & writing rules. **Read first.**
- `assets/one-page-linear-template.html` — the full design system + every
  component as a commented, placeholder-filled example. Copy and fill.
