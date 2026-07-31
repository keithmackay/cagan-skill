# Implementation Plan — cagan-skill improvements

Source: docs/reviews/2026-07-31-improve-this.md
Scope: `SKILL.md`, `references/templates.md`

## Phase 1 — High-impact content gaps

1. **Add "Partial / Staged Adoption" guidance** (addresses #1)
   - New subsection under §8 (or new §9) covering coaching guidance for orgs that can't fully adopt empowered teams: agencies/client-services, early-stage startups without a dedicated designer, regulated orgs with mandated review gates.
   - Draw from TRANSFORMED's staged-adoption / change-management material.
   - Include diagnostic questions to help identify which constraints are real vs. self-imposed, and what a "good enough for now" interim structure looks like.

2. **Add metrics/measurement framework note** (addresses #2)
   - Extend §5 (OKRs) with a short subsection on complementary metrics frameworks (e.g., North Star Metric, HEART) and when to reach for them alongside/instead of OKRs.
   - Keep it brief — a pointer/summary, not a full new methodology.

## Phase 2 — Edge case & structural improvements

3. **Add edge-case adaptation notes** (addresses #3)
   - Add brief guidance for: platform/infra teams (no direct external customer — internal customers/APIs as the "user"), regulated industries (business viability risk dominates; compliance gates are legitimately committed OKRs), B2B/enterprise sales-led motions (distinguish healthy sales input from "biggest customer drives backlog" anti-pattern).
   - Likely lands in §7 (Anti-Patterns) as caveats, or a new short subsection.

4. **Add a table of contents to SKILL.md** (addresses #4)
   - Insert a short linked TOC after the Overview section, one line per §1–§8 (plus any new sections from Phase 1/2).

## Phase 3 — Consistency & polish

5. **Reconcile Four Risks phrasing** (addresses #5)
   - Diff the risk descriptions in SKILL.md §4 against templates.md's checklist; align wording so templates.md is a strict superset/format-conversion of §4, not an independent restatement.

6. **Add source caveat to Focus/Insights/Action/Management** (addresses #6)
   - One-line note in §3 flagging this as Cagan's SVPG strategy series framing, distinguishing it from the more commonly cited 3-part version, so users/maintainers know it's intentional, not an error.

7. **Tighten dense prose in §3 and §8** (addresses #7)
   - Convert applicable paragraphs to bullet lists where it doesn't lose nuance; keep narrative prose only where the connective reasoning matters.

## Phase 4 — Token efficiency & progressive disclosure

8. **Extract usage info to README.md** (addresses #8)
   - Run the `/readme` skill to generate a `README.md` for this project covering setup/usage: what the skill does, when it triggers, how to install/reference it, and any other content that's only needed when a human is getting oriented rather than when the skill is actively firing.
   - Once README.md exists, trim SKILL.md down to the operating content Claude needs at invocation time, and add a single pointer line to README.md for anyone wanting the "how to use/install this" context.
   - Apply the same progressive-disclosure lens to the rest of SKILL.md: anything that's reference material used only situationally (e.g. deep template detail already covered by `references/templates.md`) should stay out of the default-loaded SKILL.md and be referenced on demand, not duplicated inline.

9. **Run `/plsfix` on the skill documents** (addresses #9)
   - After Phases 1–3 land (so the pass reviews final content, not content about to change), run `/plsfix` over `SKILL.md` and `references/templates.md` to tighten clarity and token efficiency — cut redundant phrasing, sharpen ambiguous instructions, and shorten without losing meaning.

## Sequencing notes

- Phases 1–2 are content additions and can be done independently of Phase 3.
- Phase 3 item 5 should be done after any Phase 1/2 edits to §4 content (if any) to avoid re-diffing.
- Phase 4 runs last: item 8 (README extraction) reshapes SKILL.md's structure, and item 9 (`/plsfix`) should be the final pass over the finished content so it isn't immediately invalidated by later edits.
- No code/tests involved — this is a pure documentation/prompt-content skill; validation is manual read-through plus (optionally) a test run of the skill against a few sample prompts (e.g., "review our roadmap," "help me write OKRs," "we're an agency, can we do this") to confirm the new sections are picked up appropriately, and that trimming SKILL.md for Phase 4 didn't remove content Claude needs at invocation time.
