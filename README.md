# CMO Council

Six marketing seats each draft their part of a plan, read each other's work blind, name every contradiction, and a CMO rules on all of it and writes the plan that survives.

Sibling to [`marketing-council`](https://github.com/zihadizisan/marketing-council), which evaluates a finished plan. This one builds it. They chain: build here, pressure-test there.

Adapted from [Andrej Karpathy's LLM Council](https://x.com/karpathy/status/1962263486196867115) methodology and the [llm-council skill](https://github.com/tenfoldmarc/llm-council-skill), turned from evaluation to construction.

---

## The problem

Ask any AI for a marketing plan and you get a plan-shaped object. Every heading is present and nothing in it conflicts, because one author never had to negotiate with anyone. No budget is contested. No week is oversubscribed. Sales never disagrees with brand.

Then someone tries to run it, and discovers that the content calendar needs four posts a week from a team of one, that two channels were quietly assigned the same money, and that nobody owns the follow-up call.

Real plans are the residue of an argument. This skill stages the argument on purpose.

## The roster

Six **owners**, not six critics. Every seat leaves with a section bearing its name, a budget line it defended, and a number it is accountable for. The tension is structural rather than assigned: they compete for one budget, one calendar, and one audience's attention.

| Seat | Owns | Fights with |
|---|---|---|
| **Insight Lead** | Audience, buying trigger, the core insight, the evidence | Sales Lead — research says X, the pipeline says Y |
| **Brand & Positioning Strategist** | Positioning, the claim, message hierarchy, the refusal list | Growth Lead — equity vs. this quarter |
| **Growth Lead** | Channel mix, budget split, funnel math, targets, kill criteria | Creative Director — proven formats vs. the swing |
| **Creative Director** | The big idea, platform, hooks, asset list | Marketing Ops — ambition vs. what ships |
| **Sales & Frontline Lead** | Conversion path, objections, follow-up, frontline capacity | Brand Strategist — what closes vs. what positions |
| **Marketing Ops** | Calendar, sequencing, owners, capacity math, dependencies | Everyone — they all want the same three weeks |

Plus **one optional swing seat** when the brief demands it — Partnerships, PR, Product Marketing, Compliance, Finance, or Community. At most one; a seventh seat added for thoroughness costs signal and buys nothing.

## What it does

1. **Mode + context scan** — BUILD from scratch, or REBUILD a draft while keeping what works. Pulls `AGENTS.md`, `CLAUDE.md`, `memory/`, company profiles, past results, prior council transcripts.
2. **The clarifying round** — fills twelve brief slots from what it already has, ranks the gaps by how much the plan changes if the answer flips, then asks **at most four questions in one round**, each with a recommended default so you can accept the whole thing in one pass. Two rounds maximum, ever.
3. **Six seats draft in parallel** — each writes its real section, names its one bet, states what it needs from others and what it will refuse to sign off.
4. **The conflict round, blind** — sections anonymized A–F with a randomized mapping. Each seat finds which section breaks its own, where the plan double-counts money or weeks or people, and what nobody owns.
5. **The 60% test** — budget and team cut to 60%, decide what dies. Forced amputation reveals what each seat actually believes is load-bearing. Convergence here is the strongest signal in the pipeline.
6. **The CMO rules and writes** — resolves every conflict explicitly, cuts to fit the real budget and the real team, sequences it into phases, and produces one coherent plan.

## The number tags

Every number in the finished plan carries its provenance:

- **GIVEN** — from you or a named file
- **BENCHMARK** — a category norm, stated as a range, never dressed up as data about your business
- **ASSUMED** — invented to make the section work, and listed in the assumption ledger

An untagged number does not reach the plan. A plan builder that quietly invents plausible figures produces a document that reads authoritative and is structurally untrustworthy — the tags are what make it safe to act on.

## The five gates

Hard rules on the output. A plan failing any one is regenerated, not shipped with a caveat.

1. **Arithmetic** — shows the chain from the target back to the inputs it needs. `300 enrolments ← 1,200 consultations at 25% ← 6,000 leads at 20%`. Written down, anyone can see which step is fantasy.
2. **Capacity** — fits the team that exists, at ~70% of available hours. The other 30% is reserve, not spare. Plans built at 100% fail in week three.
3. **Ownership** — every tactic has an owner, a date, and a number. Missing one means it goes on the cut list, visibly.
4. **Decision** — every conflict gets a ruling. "We'll do both" about a genuine either/or is the CMO declining to do its only job.
5. **Traceability** — every number tagged, every strategic claim traceable to a seat.

---

## Install

A plain Markdown skill for AI coding assistants with subagent support, such as Codex and Claude Code. There is no application to build or separate API key to configure for the skill; your assistant still needs its normal account access. A full council uses multiple agent calls.

For Codex, clone into your personal skills directory:

```bash
git clone https://github.com/zihadizisan/cmo-council.git ~/.agents/skills/cmo-council
```

For Claude Code:

```bash
git clone https://github.com/zihadizisan/cmo-council.git ~/.claude/skills/cmo-council
```

On Windows, replace `~` with your user directory, such as `$env:USERPROFILE` in PowerShell. For a project installation, use `.agents/skills/cmo-council` or `.claude/skills/cmo-council` inside that project. Start a new assistant session, then ask: **Use CMO Council to build my marketing plan.**

The skill's display name is **CMO Council**; its repository and folder are `cmo-council`. Assistants differ in tool names: use the host's equivalents for questions, subagents, file delivery, and opening HTML. Where concurrency is limited, run independent seats in batches without sharing drafts until the review round.

### Copy without Git

Use GitHub's **Code → Download ZIP**, extract it, and rename `cmo-council-main` to `cmo-council`. Copy the whole folder into the relevant skills directory. Keep `SKILL.md`, `references/`, `assets/`, and `agents/` together; copying SKILL.md alone leaves required prompts and templates behind.

| Host | Personal folder | Project folder | Invoke |
|---|---|---|---|
| Claude Code | `~/.claude/skills/cmo-council/` | `.claude/skills/cmo-council/` | `/cmo-council` |
| Codex | `~/.agents/skills/cmo-council/` | `.agents/skills/cmo-council/` | `$cmo-council` |

Windows PowerShell clone commands:

```powershell
# Choose the host you use:
git clone https://github.com/zihadizisan/cmo-council.git "$env:USERPROFILE/.claude/skills/cmo-council"
git clone https://github.com/zihadizisan/cmo-council.git "$env:USERPROFILE/.agents/skills/cmo-council"
```

Check that `SKILL.md` is directly inside `cmo-council`, not inside another nested folder. Start a new session if the skill is missing. For a safe installation check, invoke the skill and ask: "Confirm you can read references/intake.md and assets/plan-template.md; do not run the council yet."

The portable identifier is `cmo-council`. The heading and Codex UI display name remain **CMO Council**. Full council execution needs independent subagents; if your host does not expose them, the skill explains the limitation and offers a labeled single-agent walkthrough. Marketing Council is optional.

Installation conventions: [Claude Code skills documentation](https://code.claude.com/docs/en/skills) and [Codex skills documentation](https://developers.openai.com/codex/skills).

## Example

See [the fictional example brief](examples/brief.md) and [illustrative plan excerpt](examples/plan-excerpt.md). These explain the inputs, arithmetic, and conflict rulings; they are not a recorded council run or a client case study.

## Use

Trigger phrases:

- `cmo council`
- `build me a marketing plan`
- `write a marketing plan for [thing]`
- `I need a GTM plan`
- `plan my launch`
- `here's my draft plan — turn it into a real one`

Then give it whatever you have. Context, goals, constraints, a rough draft, or nothing but a goal. The clarifying round fills the rest with as few questions as it can get away with.

**Which council do I want?**

| You have | You want | Skill |
|---|---|---|
| A goal, some context | A plan | `cmo-council` |
| A rough draft | A rebuilt plan | `cmo-council` |
| A finished plan | A score and a go/no-go | `marketing-council` |
| A finished plan | Someone to try to break it | `marketing-council` |

The natural loop: build with `cmo-council`, pressure-test with `marketing-council`, revise, ship.

**Not for:** writing a single ad, post, email, or landing page; generic marketing questions; channel how-tos.

## Output

```
marketing-plan-[slug]-[DATE].md    the plan — the deliverable
cmo-council-report-[DATE].html     visual summary of the plan and the argument
cmo-council-transcript-[DATE].md   full record, including every 60% test answer
```

The plan is what you act on. The report is what you scan. The transcript is what you return to in three months when the budget actually does get cut and you want to know what the council thought was load-bearing.

---

## Files

```
SKILL.md                       the pipeline
agents/openai.yaml             Codex display name
references/intake.md           twelve brief slots, question protocol, assumption ledger
references/roster.md           all six seat prompts, swing bench, anti-drift check
references/rounds.md           conflict-round prompt, CMO prompt, standing rules
assets/plan-template.md        the plan structure the CMO writes into
assets/report-template.html    HTML report template
LICENSE                        MIT license
NOTICE                         attribution and original contributions
examples/                      fictional brief and illustrative plan excerpt
```

## Design notes

**Why owners rather than critics.** A critic can say "the timeline is unrealistic" and be done. An owner has to say what the timeline *is*, then defend it against five people who want its weeks. Evaluation councils get their signal from disagreement about quality; construction councils get it from competition over scarce resources.

**Why the 60% test is the best question in the skill.** Abstract prioritization is easy and worthless — every seat ranks its own work essential. Forced amputation is different, and it is fast. When three seats independently cut the same line without coordinating, that line is genuinely weak.

**Why anonymity is load-bearing here too.** In a named room of marketing roles, Ops defers to Strategy and everyone defers to whoever sounds most senior. Blind reading is what lets the Ops seat write "the positioning section commits us to a content volume nobody can produce" without it reading as insubordination.

**Why the clarifying round is capped at four questions.** The failure mode is not asking too few. It is asking twelve, half already answered by files in the workspace, none ranked, arriving as a wall of text the user abandons. Ask only where the plan changes if the answer flips; put everything else in the assumption ledger, where correcting a concrete document is far easier than answering abstract questions about your own business.

**Why the assumption ledger exists.** A plan built on unmarked assumptions is indistinguishable from one built on facts, right up until it fails and nobody can work out which link broke. The ledger turns invisible risk into a short checklist you can verify in an afternoon — usually the most useful page in the document.

## License and attribution

MIT — see [LICENSE](LICENSE) and [NOTICE](NOTICE). The council structure, blind review, and chairman synthesis are adapted from the linked LLM Council work. The owner seats, intake protocol, assumption ledger, conflict round, 60% test, and five gates specialize that approach for marketing plan construction.

## Limitations

A council produces a proposed plan, not evidence that its assumptions are true. Validate benchmarks, costs, conversion rates, and operational capacity before acting. The included examples are fictional and claim no business results. Outputs can vary between models and sessions.