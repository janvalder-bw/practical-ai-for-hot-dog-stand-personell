---
marp: true
theme: default
class: invert
paginate: true
style: |
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,400;0,700;1,400&display=swap');

  :root {
    --bg: #0d1117;
    --fg: #e6edf3;
    --err: #ff6b6b;
  }

  section {
    background-color: var(--bg);
    color: var(--fg);
    font-family: 'JetBrains Mono', 'Courier New', monospace;
    padding: 70px 80px;
    font-size: 1.05em;
  }

  section::after {
    content: '';
    position: absolute;
    top: 24px;
    right: 24px;
    bottom: 24px;
    left: 24px;
    border: 1px solid rgba(230, 237, 243, 0.12);
    pointer-events: none;
    z-index: 0;
  }

  h1 {
    color: var(--fg);
    font-size: 2.6em;
    line-height: 1.15;
    font-weight: 700;
    margin-bottom: 0.3em;
  }

  h2 {
    color: var(--fg);
    font-size: 1.8em;
    font-weight: 700;
  }

  h3 {
    color: var(--fg);
    font-size: 0.85em;
    font-weight: 400;
    margin-top: 0;
  }

  p, li {
    color: var(--fg);
    line-height: 1.7;
  }

  strong {
    color: var(--err);
  }

  em {
    color: rgba(230, 237, 243, 0.5);
    font-style: italic;
  }

  code {
    background: #161b22;
    color: var(--fg);
    padding: 0.2em 0.4em;
    border-radius: 4px;
    font-size: 0.88em;
  }

  pre {
    background: #161b22;
    border-left: 3px solid rgba(230, 237, 243, 0.25);
    padding: 1em 1.5em;
    border-radius: 6px;
  }

  pre code {
    background: transparent;
    color: var(--fg);
    font-size: 0.88em;
    line-height: 1.7;
  }

  ul {
    list-style: none;
    padding-left: 0;
  }

  ul li::before {
    content: '> ';
    color: rgba(230, 237, 243, 0.4);
  }

  section.chapter {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    background-color: #161b22;
    padding-bottom: 80px;
  }

  section.chapter h1 {
    color: var(--fg);
    font-size: 3.2em;
    line-height: 1.1;
  }

  section.chapter h3 {
    font-size: 0.75em;
    margin-bottom: 0.5em;
    text-transform: uppercase;
    letter-spacing: 0.12em;
  }

  section.lesson {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  section.lesson h1 {
    color: var(--err);
    font-size: 2.4em;
    line-height: 1.2;
  }

  section.lesson::after {
    border-color: rgba(255, 107, 107, 0.2);
  }

  section.title {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding-bottom: 80px;
  }

  section.title h1 {
    font-size: 3em;
    line-height: 1.1;
  }

  footer {
    color: rgba(230, 237, 243, 0.15);
    font-size: 0.6em;
    font-family: 'JetBrains Mono', monospace;
  }
---

<!-- _class: title -->

# Practical AI
# for Hot-Dog Stand
# Personnel

### Honza Valder · UX Association · March 2026

<!--
SPEAKER NOTES:
Let the title breathe. The hot dog stand is a real ambition — Alpine sabbatical plans — but it's also a frame for this entire talk: this is not enterprise AI strategy. This is what actually happens when someone with a design background builds things with AI every day for six months. From a MacBook Air. Without a budget.
-->

---

# Left Livesport.
# Went exploring.

Half-sabbatical since 9/25.

Exploring Italy. Enjoying Austria. One part-time project. Daily experimentation.
*Building things, breaking things, learning what's real.*

<!--
SPEAKER NOTES:
You probably know me, so I'll keep this short. Left Livesport/Flashscore after several years — global sports media, 100M+ users, design leadership. Since September I've been on half-sabbatical: one part-time project and deliberate daily experimentation with AI. Not watching demos. Not reading posts. Building. This talk is what I found.

My learning loop, for context: pick up signal (yes, Twitter — most pathetic, fastest), try it immediately, map the limits, file it for later. No courses. Just build something dumb and real.
-->

---

<!-- _class: chapter -->
### Chapter 01

# From Tools
# To Teammates

---

# I stopped opening Figma

*[Peaked ~$120, now $29.39]*

<!--
SPEAKER NOTES:
This is not a bit. I genuinely, organically stopped opening Figma. Not because I read a hot take. It just stopped fitting how I was working. And then I noticed the stock chart — from $120 to $22 — and thought: maybe the market is noticing something too. Show the chart. Let it sit for a moment.
-->

---

# Why fake artifacts
# stopped making sense

Squares vs real product.

<!--
SPEAKER NOTES:
Figma is squares. The product is code. We've known this for years — the gap between a Figma file and what actually ships is the source of most designer-developer friction. AI makes this gap embarrassing. Why am I drawing a rectangle to represent a button when I can describe the button and it exists? The abstraction layer stopped feeling like a useful simplification. It started feeling like a lie.
-->

---

<!-- _class: chapter -->
### Chapter 01 · Story 01

# The Slack
# Meníčka Story

---

# Origin

I wanted daily lunch specials in Slack.

Scraping restaurants: *easy*
Slack integration: *easy*
GitHub Actions hosting: *easy*

<!--
SPEAKER NOTES:
Classic sabbatical project. Automatic daily lunch menu from nearby restaurants to a Slack channel. Sounded like a weekend build. And 80% of it was exactly that fast — scraping HTML, posting to Slack via webhook, scheduling on GitHub Actions for free. All smooth.
-->

---

# What broke

**Non-determinism.**

```
"Read this HTML/IMG/PDF, return simplified menu text."

  Run 1: ✓   Run 2: ✓   Run 3: ✗
  Run 4: ✓   Run 5: ✗   Run 6: ✗
```

*No stack trace. Just... wrong data.*

<!--
SPEAKER NOTES:
The AI part — parsing messy restaurant HTML into clean unified format — this is where I spent hours. Not struggling to write the prompt. Debugging why the same prompt produced different output every few runs. Non-determinism. The failure mode isn't a crash. It's semantic corruption: wrong data that looks right. No stack trace. You read the output and realise the AI decided today was a good day to invent an extra menu item.
-->

---

<!-- _class: lesson -->

# AI matters only
# in real workflows.

*Deploy it. Let it fail where it matters.*

<!--
SPEAKER NOTES:
When the bot actually ran in production — scheduled, deployed, posting to a real Slack channel people actually read — something clicked. AI tools that live only in browser tabs are toys. The interesting stuff happens when you deploy. When there are real consequences to failure. When you have to fix it because someone is waiting for it. If you're not deploying, you're not learning anything true.
-->

---

<!-- _class: chapter -->
### Chapter 01 · Story 02

# The Hardware
# Box Story

---

# The problem

Meeting room booking.

Evoko panel: **40 000 CZK**

*Just to show who's in the room.*

<!--
SPEAKER NOTES:
Specific office problem: knowing at a glance which meeting rooms are free. Standard enterprise solution is an Evoko panel — beautiful touchscreen, calendar integration. Also ~40 000 CZK per door. For a small office that's a significant cost for what is essentially a status light.
-->

---

# ~~Evo~~Valderoko

AI wrote the code.

*What would have taken weeks took days.*

<!--
SPEAKER NOTES:
[Show the actual device — Raspberry Pi or equivalent]
I built this. A fraction of the cost. The point isn't the hardware. The point is: with AI assistance, a UX person with basic coding literacy can build functional hardware products. This would have been a 3-week googling expedition before. It took hours.
[ADD YOUR BOX PHOTO HERE]
-->

---

<!-- _class: lesson -->

# Waterfall is back,
# baby.

*Writing the spec took longer than the build.*

<!--
SPEAKER NOTES:
This surprised me. I'm an agile person. But with AI as the builder, I kept finding myself spending more time on the spec than the build. Because AI builds fast. Your thinking is the bottleneck now. Write vaguely, get garbage. Write clearly, get something real. The premium on upfront specification has never been higher. Old lesson. New urgency.
-->

---

<!-- _class: lesson -->

# AI reduces execution cost,
# not thinking cost.

*"Deploy to production? Three clicks now."*

*The premium on judgment just went up.*

<!--
SPEAKER NOTES:
I used to avoid Docker. Not anymore. I used to dread anything requiring API setup. Not anymore. AI collapsed the execution cost of technical things towards zero. But it did not reduce the thinking cost. Knowing what to build, why, what the edge cases are, what good looks like — that's still entirely on you. The tax on execution went down. The premium on taste and clarity went up. Very good news for UXers, if you're willing to act on it.
-->

---

<!-- _class: chapter -->
### Chapter 02

# Agents Enter
# the Story

---

# *[Windows error cascade]*

<!--
SPEAKER NOTES:
[Show the infinite Windows error dialog image]
This is roughly what happened when I started playing with agents.
-->

---

# I tried it.
# I switched away.

16 gig M1 Air. Local + remote models.
Booked a restaurant. Argued with my teammate.
Sent messages to friends on Messenger.

*Impressive. Didn't like the bill.*

<!--
SPEAKER NOTES:
OpenClaw — autonomous agent platform you run locally. M1 Air handles it fine, no M4 Max Studio needed. I ran it on remote models and local ones via Ollama. The demos are genuinely impressive — it booked a restaurant, it argued with a colleague on my behalf, it sent messages on Messenger. I watched it work and thought: okay, this is real. Then I thought about it more, and switched away. Here's why.
-->

---

# Outputs, not outcomes.

Agents produce outputs all day.

Code written. Docs generated. Tickets closed.
Tabs open. Loops running. Money spending.

**Does anything actually get better?**

<!--
SPEAKER NOTES:
This framing comes from Will Manidis. It's the sharpest thing I've read about AI this year. Agents are extraordinary at producing outputs. But outputs are not outcomes. The product improving, the user's life getting better, the business actually growing — those are outcomes. And they're still on you. The danger with agents is confusing high output velocity with actually getting somewhere. Also: when you add up the cost of running chains of agents all day, you're approaching the monthly salary of a human — who at least has judgment.
-->

---

<!-- _class: chapter -->
### Chapter 03

# Orbiso
# The Real Test

---

# What is Orbiso

Digital interventions for people who need them most.

Caregivers. Teachers. Parents of children with disabilities.
Terminally ill cancer patients.

App for users + backend for intervention authors
*(doctors, psychologists, andragogists)*

AI-enhanced. Scientific. Mass market.
**Also lots of karma cleaning.**

<!--
SPEAKER NOTES:
Orbiso is the project I work on part-time as product/design lead. It's a platform for creating, delivering and executing digital therapeutic and educational interventions — full feedback loop, data exports, evidence-based. The users are some of the most vulnerable people you can build for. The authors are clinicians and specialists. It's a scientific tool designed for everyday people. I mention this not just for context — the stakes shaped how seriously we took the information architecture and the workflow. When your monorepo contains patient interaction data, you think carefully about where information lives.
-->

---

# We tried MCP

*(I hate it.)*

<!--
SPEAKER NOTES:
First thing we tried: MCP — Model Context Protocol. I hated it. Too much magic. Too much configuration. Too many silent failures. Felt like the early days of microservices: theoretically elegant, practically a debugging nightmare. The bigger conceptual problem: MCP connects your AI to separate silos. It doesn't unify them. We needed something different.
-->

---

# The organism monorepo

*A belief, not just a tool choice.*

```
/orbiso
  /docs        ← product knowledge
  /app         ← the product
  /agents      ← AI instructions
  /learnings   ← why we chose what we chose
```

One body. One truth. Everyone breathes the same air.

*And it's in GIT*

<!--
SPEAKER NOTES:
Here's the principle: when people work together, knowledge should live in one organism — not be MCP-connected from separate silos into a temporary shared context. A living monorepo of information, code, and knowledge that grows together and is versioned together. The main branch is the absolute truth. Not "aligned with" the truth. The truth. No Notion that's two weeks out of date. No Confluence that nobody reads. No design file that doesn't match what's in prod. If it's not in the repo, it doesn't exist.
-->

---

# AI wrote the entire
# production documentation

From scratch. Fed it what I knew.

*Now we update it as we build.*

<!--
SPEAKER NOTES:
One of the most practically useful things I've done this year: I fed everything I knew about Orbiso into an AI and asked it to write production documentation. It did. We put it in the repo. Now: when a developer ships something, they update the doc. When I make a product decision, I update the doc. The documentation is always current because it lives where the work happens — not in a separate system that drifts the moment you stop maintaining it.
-->

---

# No more throwing
# over the wall

```
PM vibecodes feature
  → Designer handles UI in code + components
    → Developer properly implements
```

*Daily cowork. Same repo. Same context.*
*Each role, AI-augmented.*

<!--
SPEAKER NOTES:
The workflow we're converging on. Still work in progress — I want to be honest. But the direction is clear: no more handoffs. Designer doesn't throw a Figma file over the wall. PM doesn't write a PRD and disappear. You work together, daily, in the same space. PM roughcodes a feature. Designer takes it into real components in real code. Developer properly implements. Everyone has the same context because it all lives in one repo. Each person uses AI to augment their specific skills — the PM to prototype, the designer to work in code, the developer to move faster.
-->

---

# Siloed companies:
# **you are in danger.**

Departments. Separate tools. Separate knowledge.
Clean handoffs. Defined boundaries.

*This org structure cannot run this workflow.*

<!--
SPEAKER NOTES:
This is the warning I want to leave with you. Companies organised around departments with separate tools, separate knowledge bases, and clean handoffs — they literally cannot adopt this pattern. The org structure prevents it. You can't have a monorepo of truth when design lives in Figma, product lives in Confluence, engineering lives in Jira, and nobody's allowed to touch each other's tools. The competitive gap between organisations that can work this way and those that can't is forming right now. It's not a future threat. It's current.
-->

---

# This is the Axure arc

```
Axure prototype         → thrown away
Figma mockup            → re-typed in code
Design in code          → IS the product
```

<!--
SPEAKER NOTES:
We've been here before. Every generation of design tooling has been closer to the real product — but still a translation layer. Beautiful Axure prototypes that engineers ignored. Pixel-perfect Figma files that developers "implemented" their own way. Each step was progress. Each step still had someone re-doing the work downstream. The translation layer is what kills speed, kills fidelity, and kills designer influence over what actually ships.
-->

---

<!-- _class: lesson -->

# Figma is dead.

*Not just because AI happened.*

*Because the concept was wrong.*

<!--
SPEAKER NOTES:
Figma didn't lose to AI. Figma lost because it was always a workaround — a brilliant workaround, but a workaround. We needed a way to communicate design intent to developers. So we drew rectangles and called them buttons. The fundamental problem — that design and code were separate artifacts — was never solved. AI just made the cost of that separation unbearable.
-->

---

# The future tool
# looks like Storybook

Design layer **on top of code.**

Not rectangles translated to divs.
Components documented and demonstrated
where they actually live.

*The design system IS the component library.*

<!--
SPEAKER NOTES:
Here's the positive vision. The future design tool doesn't start with a canvas. It starts with the component. Storybook is already pointing in this direction: you document, demonstrate, and design-constrain components where they actually live — in the codebase. Your design system and your component library are the same thing. No translation. No "this is what it should look like" separate from "this is what it does." The designer's job becomes defining and maintaining the truth of the component, in code, not in a parallel universe of squares.
-->

---

# What this means for you

Design is not moving to code.

Design **has already moved** to code.

*The question is whether you move with it.*

<!--
SPEAKER NOTES:
Not a prediction. This is already happening in the teams moving fastest. The designer role isn't disappearing — but the value is shifting. Less: fidelity of deliverables. More: taste, systems thinking, the ability to describe what good looks like well enough for AI to build it, and the willingness to be in the repo where the product actually lives. Your competitive advantage as a designer in an AI world is judgment and clarity. Both require you to be close to the real thing.
-->

---

# The hot dog stand lesson

You don't need M4 Max Studio.
You don't need an enterprise AI budget.

You need **to get cookin.**

*And soon: your own kitchen.*

<!--
SPEAKER NOTES:
Everything I showed you today was built on a MacBook Air, on a half-sabbatical, with no budget. The barrier is not technical and not financial. It's the decision to build something real instead of watching demos.

One more thing: I believe within a few years, running your own model on your own hardware will be normal. Like owning your kitchen instead of always eating out. For Orbiso — where we handle sensitive health and patient data — we're already thinking about this. You don't want clinical interaction data going through third-party APIs indefinitely. Your own model, on your own hardware, is your own kitchen. You control the recipe. You own the output.

The hot dog stand isn't glamorous. But the food is hot, it's yours, and you know exactly what's in it.
-->

---

<!-- _class: chapter -->
### fin

# Questions?

### honza@... · @janvalder

*This presentation is a Markdown file in a GitHub repo.*
*Presented from Cursor. No Figma was opened.*

`github.com/janvalder-bw/practical-ai-for-hot-dog-stand-personell`

<!--
SPEAKER NOTES:
And yes — this entire presentation is a .md file in a GitHub repo, presented from Cursor using Marp. The medium is the message. The repo is public — fork it, read the speaker notes, adapt it. Thank you.
-->