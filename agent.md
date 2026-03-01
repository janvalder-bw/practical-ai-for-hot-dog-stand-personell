# agent.md

> How this presentation was built — a log of the AI collaboration process.
> Written by the AI agent (Claude, via Anthropic's Cowork) at the end of the session.

This document exists because the talk argues that AI works best as a collaborator in real workflows — not as a demo tool, not in isolation. So: here is the actual record of how this talk was built, in practice, with an AI.

---

## The brief

**Input:** Honza Valder, UX practitioner on half-sabbatical, had three presentations due in March 2026. We focused on the first: a 30-40 minute English talk for UX Association's UX Monday event.

**Starting material:**
- A skeleton Google Slides deck (inaccessible due to network restrictions — resolved by PDF export)
- Five PDFs of previous talks — used to understand voice, visual style, and presentation approach
- A GitHub repo already created: `janvalder-bw/practical-ai-for-hot-dog-stand-personell`

**Format decision:** Early in the session, Honza proposed switching from slides to Markdown-in-a-repo using Marp. The reasoning: one of the talk's central arguments is that designers should move to code and repos. Presenting the talk itself as a `.md` file in a GitHub repo makes the medium the message. This was agreed immediately.

---

## How the content was assembled

### Step 1 — Reading the room

Before writing a word, the agent read all five uploaded PDFs from previous talks. Key observations:
- Bold, single-idea-per-slide approach
- Minimal words, maximum impact per slide
- Punchy section transitions (dark full-screen dividers)
- Humour as a vehicle for serious points
- Numbered case studies / stories with explicit lessons called out
- Strong personal voice — direct, irreverent, not corporate

This informed every content and formatting decision that followed.

### Step 2 — Extracting the skeleton

The Monday presentation skeleton arrived as a PDF (Google Slides export). It contained ~20 slides in outline form — titles with 1-2 bullet note points each. Several slides were stubs (`Box reveal`, `OpenClaw intro`). Key lessons were already bolded by Honza.

### Step 3 — Filling the gaps via conversation

Several slides needed story context that wasn't in the skeleton. These were resolved through direct questions:

| Gap | Question asked | Answer received |
|-----|----------------|-----------------|
| Opening slide (5 emoji bubbles) | What's the story here? | Dropped — no longer relevant |
| Slack Meníčka | What happened exactly? | Scraping easy, non-determinism the real pain |
| OpenClaw | What is it, what did you do? | Tried it, switched away — agents produce outputs not outcomes |
| Orbiso | What does it do? | Digital interventions platform — caregivers, terminally ill patients, karma cleaning |
| Ending | What's the actual close? | "Design has already moved to code — question is whether you move with it" |

### Step 4 — First full draft

With gaps resolved, the agent wrote the entire presentation as a Marp `.md` file in one pass. Structure: Intro → Ch1: From Tools to Teammates → Ch2: Agents Enter the Story → Ch3: Orbiso → Closer.

### Step 5 — Second pass (belief layer added)

Honza shared additional convictions that weren't in the skeleton but belong in the talk:

- **Outputs vs outcomes** (Will Manidis framing) — agents produce outputs, outcomes are still on you
- **Organism monorepo** — when teams cowork, knowledge should live in one body, not be API-connected across silos
- **No more walls** — future team workflow is daily cowork (PM + designer + dev), each AI-augmented, no handoffs
- **Siloed companies are in danger** — org structures built around departmental separation cannot run this workflow
- **Figma dead by concept, not just by AI** — future design tools stem from Storybook: design layer on top of code, not rectangles translated to divs
- **Local model hosting** — belief that owning your model/hardware is the future; relevant for Orbiso given sensitive health data

These were integrated into a full rewrite. The intro was also shortened significantly (Honza is a known face at this event — two slides instead of four).

---

## Structural decisions

### Chapter dividers
Used as breathing room and pacing markers. Dark grey background, bottom-aligned title — mirrors the style in Honza's existing decks.

### Lesson slides
Three dedicated "Lesson:" slides in red (`#ff6b6b`). Honza confirmed the weight was right. These are the explicit landing points after each story — the things the audience should remember.

### Speaker notes
Every slide has detailed speaker notes. These are not scripts — they're the story behind the slide, the context, the thing Honza knows and the audience doesn't yet. Written in his voice, not in corporate presentation language.

### Code blocks
Used for the Meníčka non-determinism illustration, the repo structure, the Axure arc, and the Orbiso workflow. Functional: they make abstract claims concrete and reinforce the "we're in a repo" aesthetic.

---

## What the agent couldn't do

- Add actual images (Figma stock chart, hardware box photo, Windows error cascade) — these are marked as placeholder comments in the `.md` file

---

## What worked

The back-and-forth clarification loop was fast. Short targeted questions, short answers, immediate integration. No long research phases. No unnecessary verification steps. The agent had enough context from the existing PDFs to write in Honza's voice without being corrected on tone or style.

The format decision (Marp) made everything simpler: no design tool, no export chain, just text. The agent could write and iterate the entire presentation as a single file.

---

## Reflection

The process of building this talk was itself an instance of the talk's argument. A human with strong opinions, taste, and real experience provided direction and story. An AI handled structure, drafting, and iteration speed. Neither could have produced this alone at this pace.

The monorepo holds both the artifact and the process. That's the point.

---

## Session 2 — Finetuning (Cursor, Claude claude-4.6-opus)

Agent handoff: a second agent (Claude via Cursor) picked up the repo and `agent.md` as context. The brief: finetune design and audit content against the original skeleton PDF.

### Design: three-color palette

The original CSS used 7–8 distinct hex values (green headings, blue inline code, grey subtitles, dark grey footers). Honza asked for exactly three colours: background, content, and error (learning).

| Role | Value | Used for |
|------|-------|----------|
| Background | `#0d1117` | slide bg (+ `#161b22` as background shade for code blocks, chapters) |
| Content | `#e6edf3` | all text, headings, code, bullets — opacity variants for hierarchy |
| Error | `#ff6b6b` | lesson headings, `strong`, emphasis moments |

Everything chromatic (green, blue, medium grey) was removed. Hierarchy now comes from opacity: `h3` at 0.4, `em` at 0.5, bullet markers at 0.4, footer at 0.15. CSS variables (`--bg`, `--fg`, `--err`) make the palette maintainable.

### Design: ASCII border

Added a `section::after` pseudo-element — 1px solid border inset 24px from slide edges at 12% content-colour opacity. Lesson slides get the same border in error colour at 20% opacity. Gives every slide a subtle terminal-window frame.

### Design: hot-dog stand ASCII art

Added a code block with ASCII art of a hot dog stand to the title slide. Sits above the title (the title slide uses `flex-end` alignment, so the art occupies the upper space naturally).

### Content audit: skeleton vs current deck

Compared the original 47-slide Google Slides skeleton (PDF export) against the current 33-slide Marp deck. Full findings:

**Improvements over skeleton:**
- Tighter pacing (33 vs 47, no filler slides)
- Three explicit "Lesson:" callout slides with red accent
- Detailed speaker notes on every slide (skeleton had none)
- Six strong conceptual additions not in skeleton: "Outputs not outcomes", "Organism monorepo", "Siloed companies in danger", "Axure arc", "Figma is dead" as thesis, "Storybook as future tool", "Your own kitchen" (local model hosting)

**Significant omissions from skeleton — flagged for Honza's decision:**

1. **"What This Means for Teams" chapter (skeleton slides 36–43) — entirely missing.** This included: the thdxr tweet ("this isn't about AI building products"), "You as manager" (happy people → effective delivery), Purpose–People–Process matrix, design process + vibe, role adjustment for UI designers (code-to-Figma-to-code, vibe-dressing, missing tooling), and role shift/reduction funnel. For a UX audience, these are arguably the most directly actionable slides.

2. **Agents chapter lost 6 slides of concrete examples** — Slack screenshot (humor), dinner reservation (humanizes automation), Sentry triage, wishlist orchestration, "I stopped using AI as a tool — I started managing it like a junior teammate" (great quote), token burn as standalone punch.

3. **"Failures we needed" slide (skeleton 35) — dropped entirely.** Sync pain, git branch reality, vibecoding outside repo, security/sandboxing concerns. A dedicated honesty-about-failures slide builds credibility.

4. **Intro lost:** "My T shape (before AI)" skill visual, "How I learn new tech" (signal→try→map→apply — only in speaker notes now), "This Story is About Your (Future) Daily Work" framing slide.

5. **Orbiso lost:** Early AI chaos phase (ChatGPT copypaste hell, Notion drift), cross-project reasoning examples, demo questions ("What did we ship in January?"), "full context for everybody is killer feature" as standalone.

6. **Closing lost:** "Tool Shaped Objects" chapter, "Some final Wisdom" standalone.

---

*Session 1: Generated by Claude (Anthropic) via Cowork mode · February 28, 2026*
*Session duration: ~2 hours · Slides produced: 33 · Files: 3*

*Session 2: Claude (Anthropic) via Cursor · February 28, 2026*
*Design finetuning + content audit against original skeleton*