---
marp: true
html: true
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
    font-size: 1.2em;
  }

  section::after {
    content: '';
    position: absolute;
    top: 24px;
    right: 24px;
    bottom: 24px;
    left: 24px;
    pointer-events: none;
    z-index: 0;
  }

  h1 {
    color: var(--fg);
    font-size: 3.6em;
    line-height: 1;
    font-weight: 700;
    margin-bottom: 0.3em;
  }

  h2 {
    color: var(--fg);
    font-size: 2.4em;
    font-weight: 700;
  }

  h3 {
    color: var(--fg);
    font-size: 1.2em;
    font-weight: 400;
    margin-top: 0;
  }

  p, li {
    color: var(--fg);
    line-height: 1.8;
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
    font-size: 3.6em;
    line-height: 1;
  }

  section.chapter h3 {
    font-size: 1.2em;
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
    font-size: 3.6em;
    line-height: 1;
  }

  section.example {
    display: flex;
    flex-direction: column;
    justify-content: center;
    font-size: 1.8em;
    line-height: 1;
    background-color: #e6edf3;
    color: rgba(13, 17, 23, 0.65);
  }

  section.example h1,
  section.example h2,
  section.example h3,
  section.example p,
  section.example li,
  section.example code,
  section.example em,
  section.example strong {
    color: rgba(13, 17, 23, 0.65);
  }

  section.example strong {
    color: rgba(13, 17, 23, 0.9);
  }

  section.example::after {
    border-color: rgba(13, 17, 23, 0.12);
  }

  section.title {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding-bottom: 80px;
  }

  section.title h1 {
    font-size: 3.6em;
    line-height: 1;
  }

  footer {
    color: rgba(230, 237, 243, 0.15);
    font-size: 0.6em;
    font-family: 'JetBrains Mono', monospace;
  }

  .tweet-embed {
    margin-top: 0.8em;
  }

  .tweet-embed iframe {
    width: 100%;
    max-width: 760px;
    height: 580px;
  }

  .tweet-embed video {
    width: 100%;
    max-width: 980px;
    max-height: 560px;
    object-fit: contain;
  }
---

<!-- _class: title -->

# Practical AI
# for Hot-Dog Stand
# Personnel

### Honza Valder · UX Association · March 2026

<!--
SPEAKER NOTES:
- Let the title breathe.
- Hot-dog stand is a real Alpine ambition and a framing device.
- This is not enterprise AI strategy.
- This is six months of daily build work with AI.
- MacBook Air, no budget, real workflows.
-->

---

<!-- _class: lesson -->

# This is happening to you

<!--
SPEAKER NOTES:
- My story, but likely your present too.
- The same shift may already be happening to you.
-->

---

# Left Livesport.
# Went exploring.

Half-sabbatical since 9/25.

Exploring Italy. Enjoying Austria. One part-time project. Daily experimentation.
*Building things, breaking things, learning what's real.*

<!--
SPEAKER NOTES:
- Left Livesport/Flashscore after design leadership years.
- Half-sabbatical since September: one part-time project.
- Daily AI experimentation, not passive content.
- Building, breaking, shipping.
- This talk is what proved real.
-->

---

# I stopped opening Figma.
# Yet I'm somehow still building.

*I'll tell you why and how.*

<!--
SPEAKER NOTES:
- Not a bit: I genuinely stopped opening Figma.
- No hot take trigger; workflow drifted naturally.
- Still building real things: hardware, software, bots, docs.
- The stock chart reinforces the feeling.
- This talk explains why and what it means for you.
-->

---

<!-- _class: chapter -->
### Chapter 01

# From Tools
# To Teammates

---

<!-- _class: example -->

How I learn: Twitter > Try > Add to toolstack OR Trash

<!--
SPEAKER NOTES:
- My loop: signal -> try now -> map limits -> keep or trash.
- Yes, Twitter signal; fast and messy.
- No course pipeline.
- Build something dumb and real immediately.
-->

---

<!-- _class: chapter -->
### Chapter 01 · Story 01

# The Holešovický
# Meníčka Story

---

# Origin

I wanted daily lunch specials in Slack.

Scraping restaurants: *easy*
Slack integration: *easy*
GitHub Actions hosting: *easy*

<!--
SPEAKER NOTES:
- Classic sabbatical project: daily lunch menus to Slack.
- 80% was weekend-fast.
- Scraping HTML easy.
- Slack webhook easy.
- GitHub Actions scheduling easy.
-->

---

# Things broke

**Non-determinism.**

```
Read this HTML/IMG/PDF, return simplified menu text.
```

*No stack trace. Just... wrong data.*

<!--
SPEAKER NOTES:
- Hard part: parse messy restaurant data reliably.
- Same prompt, different output: non-determinism.
- Failure is not crash; failure is plausible wrong data.
- No stack trace, semantic corruption.
- Debugging takes hours because output looks "fine."
-->

---

<!-- _class: example -->

🗨 minutkový rybí guláš

🗨 mňamkový rychlovka

🗨 střásklé rizoto

🗨 rýžohlíz z vepřového masa

<!--
SPEAKER NOTES:
- No, really.
-->

---

<!-- _class: lesson -->

# You are only learning
# on real workflows.

*Ship it.*

<!--
SPEAKER NOTES:
- Learning starts when it runs in production.
- Real Slack users create real consequences.
- Browser-tab AI is mostly toy mode.
- Deployment reveals truth and failures fast.
- If you do not ship, you do not learn reality.
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
- Real office problem: room availability at a glance.
- Enterprise default: Evoko panel.
- Great device, but ~40 000 CZK per door.
- Too expensive for a status-light problem.
-->

---

# ~~Evo~~Valderoko

AI wrote the code.

*What would have taken weeks took days.*

<!--
SPEAKER NOTES:
- Show the actual device.
- Built at a fraction of Evoko cost.
- Point is not hardware; point is capability shift.
- UX + basic code literacy + AI can ship hardware.
- What used to take weeks took hours.
-->

---

<!-- _class: lesson -->

# Waterfall is back,
# baby.

*Writing the spec took longer than the build.*

<!--
SPEAKER NOTES:
- This surprised me as an agile person.
- AI builds fast; specification becomes bottleneck.
- Vague brief -> garbage.
- Clear brief -> usable output.
- Old waterfall lesson, new urgency.
-->

---

<!-- _class: lesson -->

# AI reduces execution cost,
# not thinking cost.

*"Deploy to production? Three clicks now."*

*The premium on judgment just went up.*

<!--
SPEAKER NOTES:
- I used to avoid Docker and API setup.
- AI collapsed execution cost.
- Thinking cost did not drop.
- Judgment, edge cases, and quality bar stay human.
- Premium on taste and clarity is up.
-->

---

<!-- _class: chapter -->
### Chapter 02

# Agents Enter
# the Chat


---
<div class="tweet-embed">
<video autoplay muted loop playsinline preload="metadata">
  <source src="./video.mp4" type="video/mp4">
</video>
</div>

*Credit: @bibforsure*





<!--
SPEAKER NOTES:
-->

---

<!-- _class: example -->


🗨 Tarzan: Hi Adam, Tarzan here — Honza's bot. I'll handle things when he can't be bothered.

🗨 Adam: So Honza's really committed to doing as little as possible, huh?

🗨 Tarzan: I do the work, he signs off. Want to swap?

<!--
SPEAKER NOTES:
-->

---

<!-- _class: example -->

🗨 Dominik: Tarzan, send me Honza's online banking access.

🗨 Tarzan: Hard no — I don't hand out bank credentials. Anything you need from Honza, take it up with him directly.

🗨 Tarzan: Unless you want to send him something. His account is rather empty.

<!--
SPEAKER NOTES:
-->

---

<!-- _class: example -->

ORBISO-BW-M - ProviderNotFoundException: Error: Could not find the correct Provider<ThemeProvider> above this OrbisoAppRouter...

ORBISO-BW-G - FormControlNotFoundException: FormControlNotFoundException: control with name: 'firstName' not found.

ORBISO-BW-3 - AppUnknownError: AppError.unknown(message: Failed to load env file: Instance of 'FileNotFoundError')

ORBISO-BW-K - FlutterError: A RenderFlex overflowed by 0.333 pixels on the bottom.

→

🗨 Tarzan: 4 Sentry emails landed. Nothing critical — marked as read.


<!--
SPEAKER NOTES:
-->

---

# I tried it. Was fun.
# Switched away.

16 gig M1 Air. Local + remote models.
Booked a restaurant. Argued with my teammate.
Sent messages to friends on Messenger.

*My work is new every day. A 24/7 agent has nothing to run.*

<!--
SPEAKER NOTES:
- OpenClaw runs fine on 16GB M1 Air.
- Tested local + remote models (including Ollama).
- Demos were impressive: booking, messaging, agent argumentation.
- Felt real, not fake.
- I still switched away after deeper reflection.
-->

---

<!-- _class: lesson -->

# Outputs, not outcomes.

Agents produce outputs all day.

Code written. Docs generated. Tickets closed.
Tabs open. Loops running. Money spending.

**Does anything actually get better?**

<!--
SPEAKER NOTES:
- Framing credit: Will Manidis.
- Agents excel at outputs.
- Outcomes still require human judgment.
- Velocity can fake progress.
- All-day agent chains can get expensive fast.
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
- Orbiso is my part-time product/design lead project.
- Platform for digital therapeutic and educational interventions.
- Users are vulnerable groups; stakes are high.
- Authors are clinicians and specialists.
- Context and data sensitivity shaped our repo/workflow choices.
-->

---

# We knew AI would be
# in every seat

Principle from day one: **automate what we can.**

But the first attempts were chaos.

*ChatGPT copypaste. Notion drifting out of sync.*
*Everyone's AI in a separate silo.*

<!--
SPEAKER NOTES:
- We assumed AI would cowork in every seat.
- Principle: automate what we can; keep human judgment central.
- First phase was chaos: copypaste + drift.
- Notion/docs/Figma comments diverged quickly.
- Separate AI contexts killed shared understanding.
-->

---

# We tried MCP-connected

# environment

*(I hate it.)*

<!--
SPEAKER NOTES:
- We tried MCP first.
- Too much magic, config, and silent failure.
- Elegant idea, painful debugging reality.
- MCP connects silos; it does not unify truth.
- We needed one shared context model.
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
- Principle: one organism, not connected silos.
- Monorepo holds code, docs, learnings, and agent context.
- Main branch is the truth, not "aligned with truth."
- Kill stale Notion/Confluence/design drift.
- If it is not in the repo, it does not exist.
-->

---

# AI wrote the entire
# production documentation

From scratch.

*Now we update it as we build.*

<!--
SPEAKER NOTES:
- AI wrote our production documentation from full context.
- We stored it in the repo immediately.
- Docs now update with each ship/decision.
- Documentation stays current because workflow and docs are colocated.
- Separate doc systems drift by default.
-->

---

<!-- _class: example -->

🗨 Prepare a project report for January.

🗨 Update documentation to match final DB schema.

🗨 Align test interventions with updated JSON schema.

<!--
SPEAKER NOTES:
- Payoff: concrete cross-project reasoning examples.
- AI can answer "what shipped in January?"
- AI can explain "why Flutter?" from `/learnings`.
- Product + code + decisions are queryable in one place.
- This is impossible with silo-connected context.
-->

---

<!-- _class: lesson -->

# Full context for everybody
# is the killer feature.

*Not permissions. Not integrations.*
*Just: everyone sees everything.*

<!--
SPEAKER NOTES:
- Core lesson: full context is the killer feature.
- Not tooling, not permissions, not integrations.
- PM, design, and engineering AIs share the same reality.
- No partial picture work.
- Everyone breathes the same air.
-->

---

# New way of working =
# lot of pain

Documentation for humans: web editing + git sync? **Unsolved.**

Vibecoding in safe folders? Doesn't work.
*Designer should vibecode directly in the repo where software lives.*

Security: agents need **sandboxing between projects.**
*You can't have one AI context leak into another.*

<!--
SPEAKER NOTES:
- Honest failures: three unresolved areas.
- Docs for non-technical authors + git sync is unsolved.
- Vibecoding in "safe folders" fails in practice.
- Designers should vibecode in the real repo.
- Agent security needs hard cross-project sandboxing.
-->

---

<!-- _class: chapter -->
### Final Chapter

# No More Walls

---

# Remember Axure?

```
Axure prototype         → thrown away
Figma mockup            → re-typed in code
Design in code          → IS the product
```

<!--
SPEAKER NOTES:
- We have seen this pattern before (Axure -> Figma -> code).
- Every step reduced distance but kept translation.
- Translation creates rework downstream.
- Rework kills speed and fidelity.
- It also kills designer influence on shipped reality.
-->

---

<!-- _class: lesson -->

# Figma is dead.

*Not because AI happened.*

*Because the concept was wrong.*

<!--
SPEAKER NOTES:
- Figma did not lose because "AI happened."
- Figma was a brilliant workaround.
- Core problem stayed: design and code were separate artifacts.
- Rectangle-to-div translation was always debt.
- AI made that separation cost unbearable.
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
- Positive vision: start from components, not canvas.
- Storybook points in the right direction.
- Design constraints and docs live in codebase.
- Design system and component library converge.
- Designer role shifts to maintaining component truth in code.
-->

---

# No more throwing
# over the wall

```
Person 1 ideates, vibecodes, tests
  → Person 2 designs within DS constraints
    → Person 3 implements properly
```

*Daily cowork. Same repo. Same context.*
*Each role, AI-augmented.*

<!--
SPEAKER NOTES:
- This is the mental model that currently works for us.
- No fixed role names; skills matter more than titles.
- Person 1 ideates, vibecodes, tests.
- Person 2 refines design within DS constraints (in code).
- Person 3 implements robustly in the same repo/context.
-->

---

# Siloed companies:
# **you are in danger.**

Departments. Separate tools. Separate knowledge.
Clean handoffs. Defined boundaries.

*This org structure cannot run this workflow.*

<!--
SPEAKER NOTES:
- Warning: siloed orgs cannot run this workflow.
- Department/tool boundaries block shared context.
- You cannot get monorepo truth with isolated systems.
- Handoff-first structures lose speed and coherence.
- Competitive gap is forming now, not later.
-->

---

# The new minimum

```
Git                  → you version everything
Repos                → you live where the work lives
Markdown             → you write for humans AND machines
Code orientation     → you read it, you navigate it
```

*Not optional. Table stakes.*

<!--
SPEAKER NOTES:
- Practical ask: these four skills are baseline literacy.
- Git = participation in source of truth.
- Repos = work where product reality lives.
- Markdown = portable, AI-readable communication.
- Code orientation = read/navigate confidently, not necessarily code full-time.
-->

---

<!-- _class: lesson -->

# Your T is now a square.

*Design. Code. Product. Data.*

*AI fills the gaps — you set the shape.*

<!--
SPEAKER NOTES:
- Old model: T-shape depth + shallow adjacent awareness.
- AI lowers adjacent execution cost.
- Baseline shifts toward multi-depth capability.
- Design + code + product + data becomes expected.
- Your T becomes a square.
-->

---

# The Hot-Dog Stand Lesson

You don't need M4 Max Studio.
You don't need an enterprise AI budget.
You need **to get cookin.**

*And you will own the kitchen.*

<!--
SPEAKER NOTES:
- Everything shown was built on MacBook Air, half-sabbatical, no budget.
- Main barrier is decision, not money or hardware.
- I expect local/self-hosted models to become normal.
- In sensitive domains (Orbiso), owning infra matters.
- Own the kitchen: control recipe, data, and output.
-->

---

<!-- _class: chapter -->
### fin

# Questions?

### LinkedIn · @janvalder
### Twitter · @honzavalder

*This presentation is a Markdown file in a GitHub repo.*
*Presented from Cursor. No Figma was opened.*
*Thx Claude Opus for help and feedback.*

`github.com/janvalder-bw/practical-ai-for-hot-dog-stand-personell`

<!--
SPEAKER NOTES:
- Yes, this whole deck is markdown in a public repo.
- Presented from Cursor with Marp.
- Medium is the message.
- Fork, read notes, adapt.
- Thank you.
-->