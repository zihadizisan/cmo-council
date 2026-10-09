# The Plan Template

The structure the CMO writes into. Save as `marketing-plan-[slug]-[YYYY-MM-DD].md` in the working directory.

Write it as a document someone will hand to a colleague and act on — not as a report about a council meeting. The argument lives in section 11; everything before it is the plan.

Delete any section that genuinely does not apply to this business, but do not delete a section because it was hard to fill. A section that is hard to fill is usually the one carrying the risk.

Every number carries its tag: **[GIVEN: source]**, **[BENCHMARK: range]**, **[ASSUMED]**.

---

```markdown
# Marketing Plan — {{PLAN NAME}}
{{Objective in one line}} · {{Period}} · Prepared {{DATE}}

---

## 0. The bet

One page. If someone reads only this, they should be able to repeat the plan
back correctly.

**What we are doing:** {{one paragraph}}

**Who it is for:** {{the audience in a sentence — a person in a situation}}

**What we want them to believe:** {{the primary claim}}

**Why we think it will work:** {{the insight, in a sentence}}

**What it costs:** {{budget and person-hours}}

**What success is:** {{the number and the date}}

**The bet:** This plan bets that {{the single assumption everything rests on}}.
If that is wrong, {{what happens}}.

[REBUILD MODE ONLY]
**What we kept from your draft:** {{the specific things carried forward, named.
Then what changed and why — briefly, without relitigating.}}

---

## 1. Objective and success metrics

**Primary objective:** {{outcome, number, date}}

**Baseline today:** {{current number}} [tag]

**The arithmetic:**

    {{objective}}
      <- {{stage 3}} at {{rate}} [tag]
      <- {{stage 2}} at {{rate}} [tag]
      <- {{stage 1}} at {{rate}} [tag]

**The weakest link in that chain:** {{which rate is least defensible, and what
would have to be true}}

**How we will know, and when:**

| Metric | Type | Checked | Target |
|---|---|---|---|
| {{leading indicator}} | Leading | Weekly | {{number}} |
| {{intermediate}} | Lagging | Day 30 | {{number}} |
| {{primary}} | Lagging | Day 90 | {{number}} |

**Kill criteria:** If {{specific metric}} is below {{number}} by {{date}}, stop
{{what}} and {{do what instead}}.

---

## 2. Audience and insight

**Primary audience:** {{person, situation, trigger, current alternative}}

**The decision unit:** {{who wants it, who pays, who can veto, whose opinion is
asked}} — and which of them this plan is actually addressing.

**The insight:** {{the non-obvious true thing this plan is built on}}

**Evidence:** {{what supports it, and what is still unverified}}

**Who this plan is NOT for:** {{explicitly excluded, and why}}

---

## 3. Positioning and message

**Primary claim:** {{the one thing they must come to believe}}

**Why a competitor could not say this:** {{one line — if they could, the claim
is not finished}}

**Message hierarchy:**

1. {{primary claim}}
   - Support: {{claim}} — Proof: {{evidence}}
   - Support: {{claim}} — Proof: {{evidence}}

**What this brand will not say:** {{at least two refused claims, and why}}

---

## 4. The offer and the conversion path

**The offer:** {{what they are asked to do, price, terms, what they get}}

**The path, step by step:**

| Step | What happens | Who | Within |
|---|---|---|---|
| 1 | {{action}} | {{owner}} | {{time}} |
| 2 | {{action}} | {{owner}} | {{time}} |

**The objections, in their words, and our answers:**

| They say | We answer | Where this lives |
|---|---|---|
| {{objection}} | {{answer}} | {{page / call script / email}} |

**Frontline capacity:** {{conversations per person per day}} [tag] — which caps
useful lead volume at {{number}} per week.

---

## 5. Creative platform

**The idea:** {{the organizing idea, concrete enough to brief a designer from}}

**Why anyone stops:** {{what earns the attention}}

**Campaign or format:** {{which — and if a campaign, what it leaves behind}}

**Hooks:**
1. {{hook}}
2. {{hook}}
3. {{hook}}

**Asset list:** {{what must be produced, quantity, by when, by whom}}

---

## 6. Channels and budget

| Channel | Job in the funnel | Spend | Effort/wk | Target metric | Owner |
|---|---|---|---|---|---|
| {{channel}} | {{reach / convert / nurture / close}} | {{amount}} | {{hours}} | {{metric}} | {{who}} |

**Total:** {{money}} [tag] · {{hours/week}} [tag]

**Split:** roughly {{X}}% building something that outlasts this plan,
{{Y}}% converting now. This split is deliberate because {{reason}}.

**Where each channel stops being cheap:** {{saturation point per channel}}

**Payback period:** {{how long until the money comes back}} [tag]

---

## 7. The 90 days

Phased, and each phase feeds the next.

### Phase 1 — {{name}} · {{weeks}}
**Purpose:** {{what this phase learns or establishes}}
**Must exist before it starts:** {{dependencies}}

| Week | Activity | Owner | Hours | Success number |
|---|---|---|---|---|
| {{n}} | {{activity}} | {{who}} | {{h}} | {{number}} |

**Gate to phase 2:** {{what must be true to proceed, or what changes if not}}

### Phase 2 — {{name}} · {{weeks}}
{{same shape}}

### Phase 3 — {{name}} · {{weeks}}
{{same shape}}

**Capacity check:** {{scheduled hours}} of {{available hours}} = {{percentage}}.
The remaining {{percentage}} is reserve, not spare.

---

## 8. Review cadence

- **Weekly, {{day}}, {{duration}}:** {{what gets looked at, who is there}}
- **Day 30:** {{decision to be made}}
- **Day 60:** {{decision to be made}}
- **Day 90:** {{the retrospective, against section 1}}

---

## 9. Risks and assumptions

**The assumption ledger**, largest blast radius first:

| # | Assumption | Basis | If wrong | Verify by |
|---|---|---|---|---|
| 1 | {{assumption}} | {{basis}} | {{what breaks}} | {{how, and when}} |

**Confirm assumption #1 before spending anything.** {{One line on how.}}

**Risks:**

| Risk | Likelihood | If it happens | Mitigation |
|---|---|---|---|

---

## 10. What we did not do

Considered by the council and deliberately cut. This is the backlog, not a list
of oversights.

| Cut | Why | Revisit when |
|---|---|---|
| {{idea}} | {{reason — capacity, budget, sequencing, evidence}} | {{trigger}} |

---

## 11. Decision log

Where the council disagreed, and how it was settled.

**{{Conflict}}**
- {{Seat}} argued {{position}}
- {{Seat}} argued {{position}}
- **Ruling:** {{decision}} — because {{reasoning}}
- **Revisit if:** {{condition}}

{{Repeat for every conflict raised in round two. If a seat was overruled on
something it said it would refuse to sign off, say so explicitly here.}}

**The 60% test:** if budget and team were cut to 60%, the council would keep
{{what}} and cut {{what}} — {{n}} of {{n}} seats independently agreed on
{{the convergent cut}}.

---

## 12. Open questions

Things the council could not settle without you.

1. {{question}} — {{what it changes}}
2. {{question}} — {{what it changes}}

---

*Built by the CMO Council: Insight Lead, Brand & Positioning Strategist, Growth
Lead, Creative Director, Sales & Frontline Lead, Marketing Ops{{, swing seat}}.
Full transcript: `cmo-council-transcript-{{DATE}}.md`*
```

---

## Notes on filling it

**Section 0 is the one that gets read.** Everything else is reference material for whoever executes. If section 0 does not survive on its own, the plan does not exist yet.

**Section 10 does more work than it looks like it should.** A plan that shows what was rejected reads as considered rather than generated, gives the user a backlog instead of a dead end, and pre-empts the question every reader has ("but what about…") before they ask it.

**Section 11 is the proof the council happened.** A decision log with no disagreements in it means the roster collapsed, and that should be said plainly rather than hidden behind a tidy document.

**Do not pad tables to look complete.** Three well-owned tactics beat nine with placeholder owners, and the ownership gate exists to enforce exactly that.
