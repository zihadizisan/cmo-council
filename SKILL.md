---
name: CMO Council
description: "Build a marketing plan by convening a working council of six marketing and stakeholder seats — Insight Lead, Brand & Positioning Strategist, Growth Lead, Creative Director, Sales & Frontline Lead, Marketing Ops — who each draft their part of the plan, then cross-review each other's sections blind to surface contradictions, then a CMO chairman resolves every conflict and writes one coherent, costed, sequenced plan. Asks a short round of clarifying questions before convening. MANDATORY TRIGGERS: 'cmo council', 'build me a marketing plan', 'write a marketing plan', 'create a marketing plan', 'I need a GTM plan', 'plan my launch', 'build a campaign plan', 'help me plan this launch'. STRONG TRIGGERS (use when the user supplies context, goals, or a rough draft and wants a finished plan back): 'here is my draft marketing plan, make it better', 'turn this into a real plan', 'what should our marketing look like for X', 'we need a plan for [product/quarter/launch]', 'rebuild this plan'. ROUTING: this skill WRITES a plan. If the user already has a plan and wants it scored, critiqued, or given a go/no-go verdict, use the marketing-council skill instead. Do NOT trigger for writing a single ad, post, email, or piece of copy, or for generic marketing questions and channel how-tos."
---

# CMO Council

Ask one AI for a marketing plan and you get a plan-shaped object. It has all the headings — objective, audience, channels, timeline — and it collapses the moment anyone has to run it, because a single author writes a plan where nothing conflicts. No budget is contested. No week is oversubscribed. Sales never disagrees with brand. Everything fits, because one author never had to negotiate with anyone.

Real plans are the residue of an argument. The CMO Council stages that argument on purpose: six seats draft their own part of the plan independently, read each other's work blind, name the contradictions, and then a CMO resolves every one of them and writes the plan that survives.

This is the LLM Council methodology (Karpathy) turned from evaluation to construction. Its sibling skill, `marketing-council`, takes a finished plan and scores it. This one produces the plan in the first place. They chain: build here, pressure-test there.

---

## The design principle

The review council is staffed by **critical lenses.** This one is staffed by **owners.**

Every seat here leaves the room with a section of the plan bearing its name, a budget line it defended, and a number it is accountable for. That difference matters more than it sounds. A critic can say "the timeline is unrealistic" and be finished. An owner has to say what the timeline *is*, and then defend it against five other people who want its weeks and its money.

The tension is not simulated by assigning opposing personalities. It emerges structurally, because the seats compete for three genuinely scarce resources:

- **Money** — one budget, six seats with plans for it
- **Weeks** — one calendar, six seats with things to launch
- **Attention** — one audience with one working memory, six seats with messages

A plan is what you get when those three scarcities are resolved deliberately instead of accidentally.

---

## The roster

Six fixed seats. One optional swing seat. One CMO chairman.

| Seat | Owns in the plan | Naturally fights with |
|---|---|---|
| **1. Insight Lead** | Audience definition, the buying trigger, the core insight, the evidence behind it | Sales Lead — research says X, the pipeline says Y |
| **2. Brand & Positioning Strategist** | Positioning, the primary claim, message hierarchy, what the brand refuses to say | Growth Lead — equity vs. this quarter |
| **3. Growth Lead** | Channel mix, budget allocation, funnel math, targets and measurement | Creative Director — proven formats vs. the swing |
| **4. Creative Director** | The big idea, creative platform, hooks, asset list | Marketing Ops — ambition vs. what ships |
| **5. Sales & Frontline Lead** | Conversion path, objection handling, follow-up, the handoff after the click | Brand Strategist — what closes vs. what positions |
| **6. Marketing Ops** | Calendar, sequencing, owners, capacity, tooling, dependencies | Everyone — they all want the same three weeks |

**The swing seat.** Add at most one, and only when the brief plainly demands it — a regulated category needs Compliance, a channel-led business needs Partnerships, a multi-SKU launch needs Product Marketing, a reputation-sensitive moment needs PR. Adding a seventh seat for general thoroughness costs signal and buys nothing. Bench and criteria in `references/roster.md`.

**The CMO chairman** does not sit in round one. It arrives after the argument and rules on it. Its job is decision, not summary.

Full prompts for every seat: `references/roster.md`

---

## When to run it

**Run the CMO Council for:**
- A marketing plan for a quarter, a year, or a specific goal
- A go-to-market plan for a new product, service, or market
- A launch plan with a date and a number attached
- A rough draft the user wants rebuilt into something executable
- A budget that exists with no plan for spending it

**Do not run it for:**
- Scoring or critiquing a plan that already exists → `marketing-council`
- Writing copy, an ad, a post, an email, a landing page
- Generic marketing questions and channel how-tos
- A goal so undefined that the intake round cannot produce an objective, an audience, and an offer — ask, do not convene

**If the user's intent is ambiguous** — they paste a draft and say "what do you think?" — ask which they want: a verdict on it (`marketing-council`) or a rebuilt plan (this skill). One sentence, then proceed.

---

## How a session works

### Step 1: mode and context scan

Decide the mode, then scan.

- **BUILD** — no draft supplied. The council writes from the brief.
- **REBUILD** — a draft exists. Every seat is told to keep what works and to state explicitly what it changed and why. The final plan carries a "what we kept from your draft" line. Users disengage from a plan that silently discards their thinking, even when the replacement is better.

Then scan the workspace for material that makes the plan specific rather than generic. Two minutes, no more. You are looking for the handful of files that would change what the council writes:

- `AGENTS.md` / `CLAUDE.md` in the project root or workspace
- Any `memory/` folder — audience profiles, voice docs, settled decisions, past results
- Company profile, brand guidelines, tone-of-voice docs, pitch decks
- Revenue, pipeline, or analytics data; past campaign results
- Prior `cmo-council-*` or `marketing-council-*` transcripts, so the council does not re-argue settled ground or contradict a plan already in flight

Use `Glob` and quick `Read` calls. What you find enters the brief as **GIVEN** fact, and every given must be traceable to a file. If the workspace does not say it, it is not a given.

### Step 2: the clarifying round — one round, four questions, defaults attached

**This is the step that determines whether the plan is any good, and the step most likely to be done badly.** The failure mode is not asking too few questions. It is asking twelve, half of which the workspace already answered, none of them ranked, all of them arriving as a wall of text the user abandons.

The protocol in full is in `references/intake.md`. In short:

1. Fill all twelve brief slots from the user's message and the workspace scan. Never ask about a slot you already have or can responsibly infer.
2. Rank what is left by **plan-changing power** — how differently the council would write if the answer flipped. A budget of $2k versus $200k changes every section. A brand's preferred font changes nothing. Ask only about the top of that list.
3. Ask **at most four questions in one round** via `AskUserQuestion`, each with a recommended default already first in the list so the user can accept everything in a single pass.
4. **Hard cap: two rounds ever**, and the second only if an answer opened a genuinely new fork. Interrogation is not diligence.
5. Everything still unknown becomes an entry in the **Assumption Ledger**, passed to all six seats as a stated assumption, and printed in the final plan under "what this plan assumes" with a line on what changes if it is wrong.

**The three blockers.** Objective, audience, and offer cannot be assumed. Without a number-and-date objective, a describable person, and a thing being sold, six seats will each invent a different plan and the council produces confident noise. If those are still missing after two rounds, stop and say what you need.

### Step 3: assemble the council brief

Every seat receives the identical brief. No seat gets private information and no seat gets a nudge.

1. The mode (BUILD or REBUILD), and the draft in full if rebuilding
2. The twelve brief slots, each tagged GIVEN, INFERRED, or ASSUMED
3. The Assumption Ledger
4. Business context from the workspace scan, with sources named
5. The hard constraints — money, weeks, people, and anything explicitly off the table
6. What is at stake if this fails

Do not editorialize and do not signal a preferred direction. A steered brief produces six seats agreeing with you.

### Step 4: round one — the seats draft in parallel

Spawn all six (or seven) simultaneously. Sequential spawning wastes time and lets earlier drafts contaminate later ones.

Each seat returns this block, then its section:

```
MY SECTION        The actual draft content for my part of the plan.
                  Written to be pasted into the plan, not described.
THE ONE BET       The single most important call I am making, in one sentence.
NEEDS FROM OTHERS What I require from other seats for my section to work.
WHAT I'D REFUSE   The thing I will not sign off on, whatever the rest decide.
MY NUMBERS        Every number I used, each tagged GIVEN / BENCHMARK / ASSUMED.
CONFIDENCE        High / Medium / Low, and why.
```

**The number tag is the single most important mechanic in this skill.** A plan builder that invents plausible figures produces a document that reads authoritative and is structurally untrustworthy. Three tags, no exceptions:

- **GIVEN** — from the user or a workspace file. Cite which.
- **BENCHMARK** — a category norm. Stated as a range, never a point estimate, and named as a benchmark in the plan.
- **ASSUMED** — invented to make the section work. Goes straight into the Assumption Ledger.

An untagged number does not reach the plan. If a seat returns untagged numbers, send that seat back rather than cleaning up after it.

### Step 5: round two — the conflict round, anonymized

Collect the six sections. Relabel them **Section A through F with a freshly randomized mapping**, and strip self-identifying tells ("from a creative standpoint," "operationally speaking") before labeling.

Anonymity is load-bearing here for a specific reason: in a room of named marketing roles, Ops defers to Strategy and everyone defers to whoever sounds most senior. Blind reading is what lets the Ops seat say "the positioning section has committed us to a content volume nobody can produce" without it registering as insubordination.

Spawn six fresh sub-agents. Each reads all six sections and answers five questions:

1. **Which section, built as written, breaks mine?** Name the specific contradiction, not a general concern.
2. **Where does this plan double-count?** Two sections spending the same money, booking the same week, tasking the same person, or claiming credit for the same result.
3. **What is nobody owning?** The work that falls between sections is where plans die.
4. **The 60% test.** Budget and team are cut to 60%. What comes out, what survives, and what breaks that you did not expect?
5. **The riskiest assumption in the whole plan** — one, named, with what happens if it is false.

The 60% test is the highest-yield question in the pipeline. Abstract prioritization is easy and worthless; forced amputation reveals what each seat actually believes is load-bearing. Independent convergence here — three seats cutting the same line unprompted — is the strongest signal the council produces.

Prompts in `references/rounds.md`.

### Step 6: the CMO writes the plan

One final agent receives everything: the brief, the Assumption Ledger, all six sections de-anonymized, all six conflict reviews, all six 60% tests.

It does not summarize. It **rules**, in writing, on every conflict raised in round two, and it writes one coherent plan — not six sections stapled together behind a cover page.

Chairman prompt and the full plan structure: `references/rounds.md` and `assets/plan-template.md`.

### Step 7: deliver

Three files, in the working directory:

```
marketing-plan-[slug]-[YYYY-MM-DD].md    the plan — the actual deliverable
cmo-council-report-[YYYY-MM-DD].html     visual summary of the plan and the argument
cmo-council-transcript-[YYYY-MM-DD].md   full transcript
```

Open the HTML report. Send the plan with `SendUserFile` so it reaches the user wherever they are.

Then offer the chain, in one line: run `marketing-council` on the finished plan to have six adversarial advisors try to break it before any money moves.

---

## The five gates

These are hard rules on the CMO's output. Check them before the plan is written to disk. A plan that fails a gate is regenerated, not shipped with a caveat.

**1. The arithmetic gate.** The plan must show the math from the target backwards to the required inputs. "300 enrolments" is a wish. "300 enrolments ← 1,200 consultations at 25% ← 6,000 leads at 20% ← 150,000 reach at 4%" is a plan, and the moment it is written down someone can see which step is implausible. No backwards math, no plan.

**2. The capacity gate.** The plan must fit the team that actually exists, and schedule no more than roughly 70% of available hours. The remaining 30% is not slack, it is the reserve every real quarter consumes. Plans built at 100% capacity fail in week three, and they fail on the strategic work first, because the tactical work has deadlines.

**3. The ownership gate.** Every tactic carries an owner, a date, and a number. Any tactic that cannot get all three is not underspecified — it is unfunded, and it goes on the cut list where the user can see it was considered.

**4. The decision gate.** Where round two produced a genuine conflict, the plan states which side won and why. If it says "we will do both A and B" about a live A-versus-B argument, the synthesis failed. That is not a compromise, it is the CMO declining to do the one job it has.

**5. The traceability gate.** Every number in the finished plan carries its GIVEN / BENCHMARK / ASSUMED tag, and every strategic claim is traceable to a seat. If the CMO has started producing its own free-standing opinions, the session has collapsed back into a single perspective and the six seats bought nothing.

---

## Keeping the roster honest

**The pair most at risk of collapsing** is Brand Strategist and Creative Director. Hold the Strategist to *what we claim and refuse to claim*, and the Creative Director to *why anyone would look*. If their sections start reading alike, note it in the transcript as a roster failure — apparent agreement between two seats saying the same thing is one opinion, not two confirmations, and the CMO must be told so.

**The seat most often ignored** is Sales & Frontline. It is also the one that most reliably catches the fatal flaw, because it is the only seat that knows what happens after the click. When its section conflicts with the others, that conflict is usually the real plan.

**A council that agrees on everything has failed.** Six seats producing a frictionless plan means the tension was simulated, not structural. If round two surfaces no genuine contradiction, say so plainly in the report — it is a finding about the process, and the user should know the plan was never actually stress-tested.

---

Methodology adapted from [Andrej Karpathy's LLM Council](https://x.com/karpathy/status/1962263486196867115), by way of the Codex [llm-council skill](https://github.com/tenfoldmarc/llm-council-skill). Owner-seat roster, clarifying-question protocol, number tagging, the conflict round, the 60% test, and the five gates are additions specific to plan construction. Sibling skill: `marketing-council`, for evaluating a finished plan.
