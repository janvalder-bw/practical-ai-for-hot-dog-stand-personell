# I Stopped Opening Figma. I'm Somehow Still Building.

**What six months of daily AI experimentation taught a designer about tools, teams, and what comes next.**

*Honza Valder · March 2026*

---

I left Livesport after several years — global sports media, 100M+ users, design leadership — and went on a half-sabbatical. One part-time project. Daily experimentation with AI. Not watching demos. Not reading posts. Building.

This is what I found.

I genuinely, organically stopped opening Figma. Not because I read a hot take. It just stopped fitting how I was working. The stock chart — peaked at $120, now under $30 — suggests the market is noticing something too. But I'm still building things. Real things. Hardware, software, bots, documentation. Just not in Figma.

This is my story. But I'm worried the same things are happening to you right now.

## From tools to teammates

### The lunch menu that broke everything

Classic sabbatical project. I wanted automatic daily lunch specials from nearby restaurants posted to a Slack channel. Scraping HTML, posting via webhook, scheduling on GitHub Actions for free — 80% of it was a weekend build.

The AI part broke everything.

I had the model parse messy restaurant HTML into a clean unified format. It worked. Then it didn't. Then it did again. Then it invented an extra menu item.

```
"Read this HTML/IMG/PDF, return simplified menu text."

  Run 1: ✓   Run 2: ✓   Run 3: ✗
  Run 4: ✓   Run 5: ✗   Run 6: ✗
```

Non-determinism. The failure mode isn't a crash. It's semantic corruption: wrong data that looks right. No stack trace. You read the output and realise the AI decided today was a good day to hallucinate a lunch special.

But when that bot actually ran in production — posting to a channel people actually read — something clicked. AI tools that live only in browser tabs are toys. The interesting stuff happens when you deploy. When there are real consequences to failure. When you have to fix it because someone is waiting for it.

**If you're not deploying, you're not learning anything true.**

### The 40,000 CZK status light

Another problem: meeting room booking. The standard enterprise solution is an Evoko panel — beautiful touchscreen, calendar integration. Also around 40,000 CZK per door. For what is essentially a status light.

I built one. A fraction of the cost. AI wrote the code. What would have been a three-week googling expedition took days.

Two things surprised me.

First: **waterfall is back.** I'm an agile person. But with AI as the builder, I spent more time on the spec than the build. Write vaguely, get garbage. Write clearly, get something real. The premium on upfront specification has never been higher.

Second: **AI reduces execution cost, not thinking cost.** I used to avoid Docker. I used to dread API setup. Not anymore — three clicks now. But knowing *what* to build, *why*, what the edge cases are, what good looks like? That's still entirely on you. The tax on execution went down. The premium on taste and clarity went up.

Very good news for designers and UXers, if you're willing to act on it.

## Agents enter the story

I ran an autonomous agent platform locally. 16 gig M1 Air. Local and remote models. The demos were genuinely impressive — it booked a restaurant, argued with a colleague on my behalf, triaged Sentry errors, sent messages on Messenger.

I watched it work and thought: okay, this is real.

Then I thought about it more, and switched away.

The sharpest framing I've read this year comes from Will Manidis: **agents produce outputs, not outcomes.** Code written. Docs generated. Tickets closed. Tabs open. Loops running. Money spending. But does anything actually get better?

The product improving, the user's life getting better, the business actually growing — those are outcomes. And they're still on you. The danger with agents is confusing high output velocity with actually getting somewhere. When you add up the cost of running chains of agents all day, you're approaching the monthly salary of a human — who at least has judgment.

My work is new every day. A 24/7 agent has nothing to run.

## Orbiso: the real test

Orbiso is the project I work on part-time as product and design lead. It's a platform for digital therapeutic and educational interventions — caregivers, teachers, parents of children with disabilities, terminally ill cancer patients. The users are some of the most vulnerable people you can build for. The authors are doctors, psychologists, specialists. Also lots of karma cleaning.

When we started, the conviction was clear: AI will cowork with humans on this project. Not as a gimmick. As a core part of how we build. So we set a principle: **automate what we can**, keep humans where judgment matters.

The first phase was pure chaos. Everyone pasting ChatGPT outputs into Notion. Documentation drifting out of date within days. Design decisions living in Figma comments nobody reads. Each person's AI context was isolated — the PM's AI knew nothing about the developer's decisions, the developer's AI knew nothing about the product strategy.

We tried MCP — Model Context Protocol. I hated it. Too much magic. Too much configuration. Too many silent failures. The bigger conceptual problem: MCP connects your AI to separate silos. It doesn't unify them.

### The organism monorepo

Here's the principle we landed on: when people work together, knowledge should live in one organism. Not be connected from separate silos into a temporary shared context. A living monorepo of information, code, and knowledge that grows together and is versioned together.

```
/orbiso
  /docs        ← product knowledge
  /app         ← the product
  /agents      ← AI instructions
  /learnings   ← why we chose what we chose
```

The main branch is the absolute truth. Not "aligned with" the truth. *The* truth. No Notion that's two weeks out of date. No Confluence that nobody reads. No design file that doesn't match what's in prod. If it's not in the repo, it doesn't exist. And it's in git.

One of the most practically useful things I've done this year: I fed everything I knew about Orbiso into an AI and asked it to write production documentation. It did. We put it in the repo. Now when a developer ships something, they update the doc. When I make a product decision, I update the doc. The documentation is always current because it lives where the work happens.

The killer feature isn't the structure. It's that every person — and every AI — working on the project has full context. The PM's AI knows the code decisions. The developer's AI knows the product strategy. The designer's AI knows the user research. No one is working from a partial picture.

**Full context for everybody is the killer feature.** Not permissions. Not integrations. Just: everyone sees everything.

### What hasn't worked

Let me be honest. Three things.

**Documentation for humans.** We still haven't cracked web-based editing that syncs to git. Doctors and psychologists need to edit content. They need an interface that doesn't require a code editor. We don't have that yet.

**Vibecoding in safe folders.** We tried giving designers sandboxed folders to vibecode in, separate from the real codebase. It doesn't work. The whole point is working in the real repo. If you vibecode on the side, you're back to throwing things over the wall. The radical conclusion: designers vibecode directly where the software lives.

**Security.** When you have AI agents with full repo access across multiple projects, you need hard sandboxing. One project's patient data cannot leak into another project's context. We're still figuring this out.

## No more walls

We've been here before. Every generation of design tooling has been closer to the real product — but still a translation layer.

```
Axure prototype         → thrown away
Figma mockup            → re-typed in code
Design in code          → IS the product
```

Beautiful Axure prototypes that engineers ignored. Pixel-perfect Figma files that developers "implemented" their own way. Each step was progress. Each step still had someone re-doing the work downstream.

**Figma is dead.** Not just because AI happened. Because the concept was wrong. Figma was always a workaround — a brilliant workaround, but a workaround. We needed a way to communicate design intent to developers. So we drew rectangles and called them buttons. The fundamental problem — that design and code were separate artifacts — was never solved. AI just made the cost of that separation unbearable.

The future design tool doesn't start with a canvas. It starts with the component. Storybook is already pointing in this direction: you document, demonstrate, and design-constrain components where they actually live — in the codebase. Your design system and your component library are the same thing. No translation. The designer's job becomes defining and maintaining the truth of the component, in code, not in a parallel universe of squares.

### The workflow that works (so far)

This is the mental model we're converging on at Orbiso. Still work in progress. But I believe it will shape how AI-augmented design and development actually runs.

```
Person 1 ideates, vibecodes, tests
  → Person 2 designs within DS constraints
    → Person 3 implements properly
```

Notice: no role names. Person 1 could be a PM, a designer, anyone with the idea. They ideate, vibecode a rough version, test it. Person 2 takes that into proper design within the design system's constraints — in code, not in Figma. Person 3 implements it properly. The boundaries between roles blur. What matters is the skill, not the title. Everyone works in the same repo, same context, same truth.

Companies organised around departments with separate tools, separate knowledge bases, and clean handoffs — they literally cannot adopt this pattern. The org structure prevents it. You can't have a monorepo of truth when design lives in Figma, product lives in Confluence, engineering lives in Jira, and nobody's allowed to touch each other's tools.

The competitive gap between organisations that can work this way and those that can't is forming right now. It's not a future threat. It's current.

### The new minimum

If you're a designer, PM, or researcher, four things are no longer nice-to-have developer skills. They're literacy:

- **Git** — you version everything
- **Repos** — you live where the work lives
- **Markdown** — you write for humans AND machines
- **Code orientation** — you read it, you navigate it

Not optional. Table stakes. Without these four, you're locked out of the workflow I just described.

The old model was the T-shape: deep expertise in one area, shallow awareness of others. AI changes the math. When execution cost drops towards zero in adjacent skills, you can — and must — go deeper in more directions. A designer who understands code, product, and data isn't a unicorn anymore. They're the baseline.

**Your T is now a square.** AI fills the gaps — you set the shape.

## The hot-dog stand lesson

Everything I described was built on a MacBook Air, on a half-sabbatical, with no budget. The barrier is not technical and not financial. It's the decision to build something real instead of watching demos.

One more thing. I believe within a few years, running your own model on your own hardware will be normal. Like owning your kitchen instead of always eating out. For Orbiso — where we handle sensitive health and patient data — we're already thinking about this. You don't want clinical interaction data going through third-party APIs indefinitely.

Your own model, on your own hardware, is your own kitchen. You control the recipe. You own the output.

The hot dog stand isn't glamorous. But the food is hot, it's yours, and you know exactly what's in it.

---

*This article is based on my talk at UX Monday (Asociace UX), Prague, March 2026. The presentation itself is a Markdown file in a GitHub repo, presented from Cursor using Marp. No Figma was opened.*

*[github.com/janvalder-bw/practical-ai-for-hot-dog-stand-personell](https://github.com/janvalder-bw/practical-ai-for-hot-dog-stand-personell)*
