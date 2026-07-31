# improve-this Review — cagan-skill

Date: 2026-07-31
Scope: Full project (`SKILL.md`, `references/templates.md`)
Project type: Claude Code skill (prompt/knowledge collection) — Marty Cagan/SVPG product development methodology

## Priority List

```
#1  [Impact: High | Confidence: High]    Completeness — No de-risking guidance for "partial adoption" / non-empowered orgs
#2  [Impact: Medium | Confidence: High]  Completeness — Missing metrics/measurement framework detail (North Star, HEART, etc.) beyond OKRs
#3  [Impact: Medium | Confidence: Medium] Edge Case Coverage — No guidance for platform/infra teams, B2B/enterprise, or regulated industries where Cagan's model needs adaptation
#4  [Impact: Medium | Confidence: Medium] Navigability & Structure — No quick-reference index/TOC despite 8 numbered sections
#5  [Impact: Low | Confidence: High]     Redundancy — Four Risks Checklist duplicated in spirit between SKILL.md §4 and templates.md
#6  [Impact: Low | Confidence: Medium]   Accuracy & Consistency — "Focus → Insights → Action → Management" framing could use citation/version caveat
#7  [Impact: Low | Confidence: Low]      Clarity & Simplification — Some sections (§3, §8) are dense paragraphs that could be tightened to bullets
#8  [Impact: Medium | Confidence: High]  Token Efficiency & Progressive Disclosure — Usage/setup info should live in a separate README.md, not always-loaded SKILL.md
#9  [Impact: Low | Confidence: High]     Clarity & Simplification — A dedicated /plsfix pass would tighten wording and token efficiency across both docs
```

## Categorized Breakdown

### Clarity & Simplification
- §3 and §8 mix long explanatory prose with prescriptive instructions ("How to use this," "Diagnostic questions") in dense paragraphs rather than scannable bullets, slightly slowing an LLM's ability to extract the actionable instruction at inference time. Impact: Low, Confidence: Low — the current prose is not unclear, just denser than it needs to be.

### Completeness
- No content addresses the common real-world situation: an org that *can't* fully adopt empowered teams (regulatory constraints, agency/client-services model, early-stage startup with no dedicated designer). TRANSFORMED explicitly covers partial/staged adoption, but the skill only gestures at this in one line (§8) without concrete coaching guidance for that gray zone. Impact: High, Confidence: High.
- Metrics/measurement is covered only via OKRs (§5); there's no mention of complementary frameworks Cagan references (e.g., product metrics/KPI trees, North Star metric) that often come up alongside OKR-writing requests. Impact: Medium, Confidence: High.

### Accuracy & Consistency
- The "Management" as a fourth strategy component (§3) is a correct but less commonly cited framing; a one-line pointer to source would help future maintainers verify and would resist confidently-stated inaccuracy. Impact: Low, Confidence: Medium.

### Navigability & Structure
- 8 top-level sections plus a references file, but no table of contents or section index at the top of SKILL.md. For a skill this length (149 lines), a TOC would help both humans skimming and future edits. Impact: Medium, Confidence: Medium.

### Redundancy
- The Four Risks are explained narratively in SKILL.md §4 and then re-expressed as a checklist in templates.md — intentional (reference doc pattern) but the checklist's risk descriptions slightly diverge in phrasing from §4's list, which could drift further out of sync over time if one is edited without the other. Impact: Low, Confidence: High.

### Edge Case Coverage
- No explicit guidance for team types Cagan's frameworks don't map cleanly onto: platform/infrastructure teams (no direct "customer"), heavily regulated industries (healthcare/finance) where business-viability risk dominates, or B2B/enterprise sales-led motions where "stakeholder-driven" isn't purely an anti-pattern. §7 currently treats "sales-driven backlog" as unambiguously bad without nuance for legitimate enterprise sales input. Impact: Medium, Confidence: Medium.

### Token Efficiency & Progressive Disclosure
- SKILL.md is loaded in full on every invocation, but it currently mixes operating instructions (what Claude needs at inference time) with content that's really "how to use/install this skill" — material a human reader wants once, not content Claude needs re-loaded on every product-strategy question. Splitting that out into a `README.md` (via the `/readme` skill) and referencing it only when relevant would reduce the default token footprint without losing anything. Impact: Medium, Confidence: High.
- More generally, any content in SKILL.md that's situational reference material duplicating what's already in `references/templates.md` should be trimmed from the always-loaded file and pulled in on demand, consistent with the existing SKILL.md → references/ split for the Four Risks checklist and Opportunity Solution Tree. Impact: Medium, Confidence: Medium.

### Clarity & Simplification (token-efficiency pass)
- A dedicated `/plsfix` pass over `SKILL.md` and `references/templates.md` — after the content changes above land — would independently catch redundant phrasing and ambiguous instructions and tighten wording, complementing (not overlapping) the structural bullet-conversion suggested in finding #7. Impact: Low, Confidence: High.
