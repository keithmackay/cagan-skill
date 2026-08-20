# Copyable Templates

## Four Risks Checklist (run for any proposed feature/solution)

```
Solution: ___________________________

VALUE RISK
- Who specifically has this need? (name a segment, not "users")
- What evidence do we have they'd choose this over their current workaround?
- Cheapest test to run: [ ] fake door  [ ] concierge  [ ] Wizard of Oz  [ ] other: ___

USABILITY RISK
- Can a first-time user complete the core task without help?
- Test: [ ] 5-user hallway test  [ ] moderated usability test  [ ] other: ___

FEASIBILITY RISK
- Any part of this beyond our current tech/team capability?
- Test: [ ] engineering spike  [ ] feasibility prototype  [ ] other: ___

BUSINESS VIABILITY RISK
- Legal/compliance sign-off needed? [ ] yes [ ] no
- Sales/marketing/finance/exec stakeholders who need to weigh in: ___________
- Ethical/reputational concerns: ___________
```

## Opportunity Solution Tree Template

```
OUTCOME: [the measurable business/product metric this work should move]

OPPORTUNITY A: [a customer need/pain, sourced from interviews/data, not from a backlog]
  Evidence for this opportunity: ___________
  - Solution idea A1: ___________ → Test: ___________
  - Solution idea A2: ___________ → Test: ___________

OPPORTUNITY B: [another distinct need]
  Evidence for this opportunity: ___________
  - Solution idea B1: ___________ → Test: ___________
```

Tips:
- Source opportunities from customer interviews, support tickets, usage data, and sales calls — each one should be backed by that kind of evidence, not by a solution you already wanted to build.
- Generate at least 2 competing solution ideas per opportunity before picking one; a tree with one solution per opportunity is a sign you stopped ideating too early.
- Prune branches once tested and disconfirmed — the tree should shrink as you learn, not just grow.

## OKR Rewrite Pattern (feature → outcome)

```
BEFORE (feature-shaped, avoid):
  Objective: Improve onboarding
  KR: Ship new onboarding flow by Q3

AFTER (outcome-shaped, prefer):
  Objective: Improve onboarding
  KR: Increase Day-7 activation rate from 32% → 45%
  KR: Reduce time-to-first-value from 6 days → 2 days
```
The team retains autonomy over *how* (new flow, better emails, in-product nudges, etc.) — the KR only fixes *what outcome* counts as success.

## Vision / Strategy Doc Skeleton

```
1. VISION (stable for years)
   - The future state this product enables, and for whom
   - Why this matters — the change in the world, not the product's feature list

2. INSIGHTS (the non-obvious things we know)
   - From data: ___________
   - From qualitative/customer research: ___________
   - From technology: ___________
   - From market/competitive landscape: ___________

3. FOCUS (this period only — quarters, not features)
   - Target customer/segment we are prioritizing: ___________
   - Objective(s) for this period: ___________

4. MANAGEMENT (how leadership stays engaged after this is set)
   - Cadence for checking in with teams: ___________
   - What leadership will and won't weigh in on (outcomes yes, team's chosen
     solution no): ___________

5. EXPLICITLY NOT INCLUDED HERE
   - A committed list of features and ship dates (that belongs to teams' own
     discovery/delivery process, not to the strategy doc)
```

## Prototyping Types & Testing Techniques Reference

**Prototyping types** (for testing before building):
- **Feasibility prototype** — engineer-built, answers "can this be built"
- **User prototype** — low-fidelity (paper, Figma), tests usability with real users, cheap to iterate
- **Live-data prototype** — looks real, wired to real or realistic data, used for stakeholder/business viability tests and deeper usability tests
- **Hybrid prototype** — combination, used for higher-stakes or more complex validation

**Testing techniques** (mapped to the four risks):
- Value/demand testing: **fake door / smoke test**, **concierge test** (manually deliver the "product" to a few users), **Wizard of Oz test** (looks automated, isn't)
- Usability testing: 5-user hallway/guerrilla tests are usually enough to find major issues (Nielsen's finding, which Cagan cites approvingly)
- Feasibility: engineering spikes, technical prototypes
- Business viability: run the idea past legal/finance/sales/marketing/exec stakeholders *early*, in discovery — not at launch review

**Rule of thumb to apply**: discovery should run on the order of days, not months. If a user describes a discovery process taking a quarter, flag that the point of these techniques is speed — cheap, fast, disconfirming tests, not a parallel mini-project.

## Anti-Pattern Checklist

Actively watch for and name these, since users often don't realize they're symptoms of the same underlying issue:
- Roadmaps that are lists of features with ship dates ("date-driven roadmap")
- Sales-driven or stakeholder-driven backlogs ("just build what the biggest customer/loudest exec asked for")
- Engineers brought in only after the spec is "done"
- PMs functioning as requirement-gatherers / Jira administrators rather than discoverers of value
- Success measured by "did we ship X" rather than "did metric Y move"
- Discovery skipped entirely, or done as a slow, heavyweight, months-long parallel project rather than fast/cheap/continuous
- Reorgs around projects instead of durable missions (project teams disbanded after shipping, so no one owns outcomes)
- RICE/weighted-scoring prioritization applied to a features list, when the deeper fix is to stop generating a features list at all and instead assign problems

**Context matters — don't apply these as unqualified rules:**
- **Platform/infrastructure teams** have no direct external customer; treat other internal teams and their APIs/systems as "the customer" for value and usability risk, rather than concluding discovery doesn't apply.
- **Regulated industries** (healthcare, finance, etc.) legitimately have more **committed** OKRs and mandatory compliance gates than the norm — business viability risk dominates there by design, not as a sign of dysfunction.
- **B2B/enterprise sales-led motions**: healthy input from sales (a real prospect's blocking requirement, a pattern across many deals) is not the same anti-pattern as "build whatever the loudest exec/biggest customer asked for." Distinguish the two before flagging a stakeholder-driven backlog.
