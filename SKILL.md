---
name: product-discovery-cagan
description: Apply Marty Cagan / SVPG (Silicon Valley Product Group) product development methodology — the frameworks from "INSPIRED," "EMPOWERED," and "TRANSFORMED." Use this skill whenever the user is working on product strategy, product vision, team topology/structure, product discovery, writing or reviewing a product roadmap, evaluating whether a team is "empowered" vs a "feature team," setting OKRs for a product org, coaching product managers, running discovery on a new opportunity, de-risking a feature (value/usability/feasibility/business viability), building an opportunity solution tree, designing prototypes or tests for a product idea, or assessing/transforming a product organization's operating model. Trigger even if the user doesn't say "Cagan" by name — e.g. "how should we structure our product teams," "we keep shipping features nobody uses," "help me write our product strategy," "our roadmap is just a list of features," "how do I coach this PM," "what should we prototype before building this."
---

# Product Development per Marty Cagan / SVPG

## Overview

This skill encodes the operating model described across Marty Cagan's three books — **INSPIRED** (how great products get built), **EMPOWERED** (how great product teams and leaders work), and **TRANSFORMED** (how legacy orgs move to this model). The core idea underneath all three: strong product companies give teams *problems to solve*, not features to build, and they discover the right solution *before* committing engineering to build it.

Use this skill both as a **diagnostic lens** (is this team/org doing this well or badly?) and as a **generative toolkit** (help draft the vision doc, the OKRs, the opportunity solution tree, the test plan). When a request touches product strategy, team structure, discovery, or roadmapping, actively apply the concepts below and keep advice grounded in Cagan's own prescriptions — he is explicitly opposed to a lot of "generic" PM practice (release-train roadmaps, stakeholder-driven backlogs, RICE-scored feature lists), which is generic PM advice's default toolkit.

For what this skill is, when it fires, and how to install/reference it, see `README.md` — this file is Claude's operating content, not a setup guide.

## Flags

### `--help`

If the user invokes this skill with a `--help` flag (e.g. `/product-discovery-cagan --help`), do not apply the methodology. Instead, read and display the contents of `help.md` (in this skill's folder) verbatim, then stop.

### `--version`

If the user invokes this skill with a `--version` flag (e.g. `/product-discovery-cagan --version`), do not run the workflow. Instead:

1. Read the installed version from this skill's own manifest: `.claude-plugin/plugin.json` if present, else `.codex-plugin/plugin.json`, else `gemini-extension.json` — whichever exists for this platform install. If none exist (a bare Claude Code skill with only SKILL.md), read the topmost version heading in `CHANGELOG.md` instead.
2. Print: `product-discovery-cagan v<installed-version>`
3. Best-effort update check — determine this skill's GitHub source repo:
   a. If `.git` exists here and `git remote get-url origin` resolves to a `github.com` URL, use that `owner/repo`.
   b. Otherwise, search this skill's own `README.md` for the first `https://github.com/<owner>/<repo>` URL and use that.
   c. If neither yields a repo, or the `gh` CLI isn't installed/authenticated: stop here. Print nothing further — no status line, no error.
4. If a repo was found: run `gh api repos/<owner>/<repo>/releases/latest -q .tag_name` (strip a leading `v`). Compare to the installed version:
   - Equal → append: `Status: up to date`
   - Installed is older → append: `Status: newer version available (v<latest>). To update: if you installed this via a Claude Code marketplace, run /plugin marketplace update <marketplace-name> then reinstall; otherwise, git pull in your install directory if it's a git checkout, or re-copy from https://github.com/<owner>/<repo> per this README's Installation section.`
   - Installed is newer → append: `Status: ahead of latest release (development checkout)`
   - If the API call fails for any reason (network, auth, rate limit, malformed tag): print nothing further — no status line, no error shown to the user.
5. Stop — do not proceed to run the skill's actual workflow.

## Contents

1. [The Core Distinction: Feature Teams vs. Empowered Teams](#1-the-core-distinction-feature-teams-vs-empowered-teams)
2. [Team Topology: The Product Trio](#2-team-topology-the-product-trio)
3. [Product Vision & Strategy](#3-product-vision--strategy)
4. [Continuous Discovery & the Four Big Risks](#4-continuous-discovery--the-four-big-risks)
5. [Outcomes over Output: OKRs](#5-outcomes-over-output-okrs)
6. [Coaching & Product Leadership](#6-coaching--product-leadership-from-empowered)
7. [Common Anti-Patterns to Flag](#7-common-anti-patterns-to-flag)
8. [How to Apply This Skill in Practice](#8-how-to-apply-this-skill-in-practice)
9. [Partial & Staged Adoption](#9-partial--staged-adoption)

---

## 1. The Core Distinction: Feature Teams vs. Empowered Teams

This is the load-bearing concept. Check every request against it first.

| | **Feature Team** (what Cagan calls a mercenary/output team) | **Empowered Team** (what Cagan is prescribing) |
|---|---|---|
| Given | A roadmap of features and projects, with dates | A problem to solve, tied to a business outcome |
| Measured on | Output — did you ship it on time | Outcome — did it move the needle on the metric |
| Role of engineers | Implementers, brought in after the solution is decided | Co-creators of the solution from day one |
| Role of PM | Requirements gatherer / project manager / backlog administrator | Discovers what's valuable, viable, usable, feasible |
| Roadmap looks like | List of features and ship dates | List of problems/objectives, with team autonomy on solution |
| Where ideas come from | Stakeholders, sales, execs, "the roadmap" | Customer insight, data, tech capability, team ideation, all synthesized by the trio |

**How to use this**: If a user describes their team's setup, silently classify it against this table before advising. If they're a feature team asking "how do we prioritize our feature list better," the deeper (and more useful) answer is often "the feature list itself is the problem" — say so, gently, and explain why, rather than just optimizing the prioritization method.

## 2. Team Topology: The Product Trio

Cagan's empowered team is a **durable, mission-based cross-functional team**, minimally a trio:
- **Product Manager** — responsible for value and business viability (is it worth building, will customers use it, does it work for the business)
- **Product Designer** — responsible for usability (can people figure out how to use it, will they enjoy using it)
- **Tech Lead / Engineering** — responsible for feasibility (can we build it with the time/skills/tech we have)

Key properties of good team topology:
- **Durable**, not project-based — the team stays together and owns a piece of the product long-term (this is why it's "mission-based," not "project-based")
- **Small** (Amazon's "two-pizza team" scale)
- **Co-located in purpose** even if geographically distributed — the trio works together daily, not in a waterfall handoff
- Engineers are in the room *during discovery*, not just handed a spec afterward — this is one of the most commonly skipped and most important pieces

**Diagnostic questions to ask the user** if they're describing a team structure:
- Is the team organized around a *mission/product area* or around a *project*?
- Does the team include a designer and engineer during ideation, or only during build?
- Who decides *what* to build — the team, or someone upstream of the team?

## 3. Product Vision & Strategy

Distinguish these three, which are often conflated:

- **Vision**: a 3–5+ year picture of the future the product enables. Should be inspiring, stable, and roughly unchanged for years. Test: could this vision survive several strategy pivots?
- **Strategy**: the sequenced set of insights and bets for how you get from here to the vision. Cagan's SVPG strategy series frames this as **four** components — **Focus → Insights → Action → Management**. This four-part framing (vs. the more commonly cited three-part Focus/Insights/Action) is intentional, not an error — Cagan is explicit that Management belongs:
  - *Focus*: a small number of target markets/customers/objectives, not everyone
  - *Insights*: the non-obvious things you know — from data, from qualitative customer research, from new enabling technology — that justify where to focus
  - *Action*: translating insight into a sequence of problems assigned to specific product teams (OKRs — see §5), not a list of features assigned to a roadmap
  - *Management*: ongoing leadership involvement after the strategy is set — removing obstacles, helping teams navigate what the strategy doc couldn't anticipate — without lapsing into micromanagement or dictating solutions
- **Roadmap** (traditional feature-list sense): the *least* useful artifact in Cagan's view; date-committed feature roadmaps are actively discouraged. If the user asks for help with "our roadmap," ask (or infer) whether they mean a list of features with dates or a sequenced set of problems/objectives — steer toward the latter.

When drafting a vision or strategy doc for a user, structure it as:
1. The future state / vision narrative (why it matters, who it's for)
2. The 2–3 insights that justify why *this* path and not another
3. The focus areas / objectives for the next period (quarters, not features)
4. A short note on how leadership will stay involved (unblocking, reviewing progress) without dictating team-level solutions
5. Explicitly *not* a list of committed features and dates

## 4. Continuous Discovery & the Four Big Risks

Every proposed solution carries four risks. Discovery is the process of resolving these *before* committing to build:

1. **Value risk** — would customers choose this over their current workaround?
2. **Usability risk** — can a first-time user complete the core task without help?
3. **Feasibility risk** — is any part of this beyond our current tech/team capability?
4. **Business viability risk** — does it work for the business (legal, sales, marketing, finance, ethics, etc.)?

When a user brings a feature/product idea, walk it through all four explicitly — teams (and this skill's user) commonly only check feasibility and skip the other three, which is precisely the failure mode Cagan is writing against.

### Opportunity Solution Trees (Teresa Torres' framework, which Cagan endorses and cites as the operationalization of continuous discovery)

Structure:
```
Desired Outcome (business/product metric)
 └── Opportunity 1 (a customer need/pain/desire, from research)
      ├── Solution idea A
      │    └── Experiment/test to de-risk A
      ├── Solution idea B
      └── ...
 └── Opportunity 2
      └── ...
```
When helping a user structure discovery for a new initiative, build this tree with them: start from the outcome, surface opportunities from customer interviews/data (not from a features backlog), generate multiple competing solution ideas per opportunity, and attach a specific test to each.

For prototyping types and testing techniques mapped to each risk, see the "Prototyping Types & Testing Techniques Reference" section in `references/templates.md`. Rule of thumb: discovery should run on the order of days, not months — if a user describes a discovery process taking a quarter, flag that the point of these techniques is speed, not a parallel mini-project.

## 5. Outcomes over Output: OKRs

Cagan's preferred mechanism for giving teams real autonomy while staying aligned to strategy is OKRs used correctly:

- **Objective**: a meaningful, qualitative problem to solve (comes from strategy, §3)
- **Key Results**: the measurable outcomes that would indicate the objective is achieved — **not** a list of features shipped. A KR like "ship feature X" is a smell; a KR like "increase activation rate from 40% to 55%" is the intended shape.
- Teams should have **solution autonomy** — leadership assigns the objective/outcome, the team (the trio) decides how to achieve it.
- Distinguish **committed** OKRs (rare, hard deadlines — e.g. legal/compliance) from **aspirational** OKRs (the norm — stretch goals the team may not fully hit, and that's fine, because output isn't what's measured).

When a user asks for help writing OKRs, actively push back on objectives/KRs that are secretly a feature list in disguise, and rewrite them toward outcomes.

**Complementary metrics frameworks**: OKRs set the objective/outcome; teams still need an ongoing metric to steer by day-to-day. Point to these as appropriate rather than treating OKRs as the only measurement tool:
- **North Star Metric** — the single metric that best captures the value a product delivers to customers, used to align a whole org around one outcome over time
- **HEART** (Happiness, Engagement, Adoption, Retention, Task success) — a framework for choosing UX-quality metrics for a specific feature or product area
Use these to help pick *what to measure*; OKRs remain the mechanism for committing to a target and time horizon.

## 6. Coaching & Product Leadership (from EMPOWERED)

If the request is about managing/coaching PMs, designers, or a product org:
- The core leadership loop is **weekly 1:1 coaching**, not performance review theater — focused on skill-building against a small number of concrete competencies (not vague "communication skills")
- Product leaders are responsible for: **staffing** (hiring the right trio members), **coaching** (weekly, ongoing), and **setting outcomes** (via strategy + OKRs), not for handing down feature specs
- Distinguish coaching (helping someone get better) from managing tasks (assigning and checking work) — Cagan is explicit that most "PM managers" are doing the latter and calling it the former
- A common anti-pattern worth naming: leaders who write the PRD/roadmap themselves and hand it to the "PM" to execute — this converts a product manager into a project manager, and is diagnostic of a feature-team org even if the org chart says otherwise

## 7. Common Anti-Patterns to Flag

Actively watch for and name these, since users often don't realize they're symptoms of the same underlying issue — see the "Anti-Pattern Checklist" section in `references/templates.md` for the full list plus context caveats (platform teams, regulated industries, B2B sales-led motions) for when these don't apply as unqualified rules.

## 8. How to Apply This Skill in Practice

- **Reviewing an artifact** (roadmap, PRD, OKRs, org chart): classify it against §1 and §7 first, then give specific, structural feedback (not just wording polish) — e.g., "this OKR's key result is a shipped feature, here's how to rewrite it as an outcome."
- **Drafting an artifact** (vision doc, strategy doc, OKRs, opportunity solution tree, test plan): use the templates/structures in §3–§5 directly.
- **Coaching / org-design questions**: pull from §2 and §6.
- **"Should we build X" questions**: run it through the four risks (§4) and suggest the cheapest test for whichever risk is least resolved, rather than jumping to "here's how to build it."
- **"We can't fully adopt this" questions**: use §9.
- **When the team/org context is unstated**: ask the relevant diagnostic questions (§1, §2, §9) before classifying or advising, rather than assuming a feature-team or empowered-team setup.
- Always distinguish, out loud if useful, between what Cagan prescribes and where reasonable practitioners disagree — not every org can restructure into durable teams overnight (§9), and that's a real multi-year change-management problem, not a sign the model is trivially adoptable or that it doesn't apply.

## 9. Partial & Staged Adoption

Not every org can adopt empowered teams overnight — TRANSFORMED treats this as a multi-year change-management problem, not a one-time switch. Common constrained contexts:
- **Agencies / client-services firms**: the client, not the team, often owns the "what" — durable ownership of an outcome is harder when engagements are scoped and time-boxed.
- **Early-stage startups**: no dedicated designer, sometimes no dedicated PM — the founder or a generalist covers multiple trio roles.
- **Regulated orgs with mandated review gates**: legal/compliance sign-off is a real, non-negotiable checkpoint, not stakeholder interference to route around.

**Diagnostic questions** to separate real constraints from self-imposed ones:
- Is this constraint structural (contract terms, headcount, regulation) or organizational habit ("we've always done it this way")?
- Of the trio's three responsibilities (value, usability, feasibility), which are genuinely uncovered vs. just not formally assigned?
- What's the smallest change that gets closer to durable ownership and problem-based work, given the real constraint?

**What "good enough for now" looks like**: don't withhold every technique until full trio staffing exists. A generalist can still run a lightweight version of the four-risk test (§4) before committing to build; even project-based teams can be given a problem statement instead of a spec; even client engagements can push for outcome-based success criteria in the SOW. Coach toward the direction of travel, not an all-or-nothing switch.

## Reference

For a deeper structured checklist version of the four-risk test and the opportunity-solution-tree template usable as a copyable format, see `references/templates.md`.
