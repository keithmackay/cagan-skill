# cagan-skill

A Claude Code skill that encodes Marty Cagan / SVPG product development methodology — the frameworks from *INSPIRED*, *EMPOWERED*, and *TRANSFORMED* — so Claude can act as a diagnostic lens and generative toolkit for product strategy, team topology, discovery, and OKRs.

## Highlights

- **Diagnostic lens** — classifies a described team/org against Cagan's feature-team vs. empowered-team distinction before giving advice
- **Generative toolkit** — drafts vision docs, strategy docs, OKRs, opportunity solution trees, and test plans using Cagan's structures, not generic PM templates
- **Broad, implicit triggering** — fires on product-strategy language even when the user doesn't say "Cagan" (e.g. "our roadmap is just a list of features," "how do I coach this PM")
- **Copyable templates** — a Four Risks checklist and Opportunity Solution Tree template in `references/templates.md`, pulled in only when needed
- **Staged-adoption aware** — coaches orgs that can't fully adopt empowered teams (agencies, early-stage startups, regulated industries) rather than treating the model as all-or-nothing

## Getting Started

This is a Claude Code skill, not a program you build or run — there's no install step beyond making it available to Claude Code.

**Prerequisites**: [Claude Code](https://docs.claude.com/claude-code) with skill support.

**Installation**: place this directory where Claude Code loads skills from (e.g. as a project-level skill under `.claude/skills/`, or as a personal skill under `~/.claude/skills/`), keeping `SKILL.md` and `references/templates.md` together.

```bash
cp -r cagan-skill ~/.claude/skills/product-discovery-cagan
```

## Usage

Once installed, the skill activates automatically whenever a request touches product strategy, team structure, discovery, or roadmapping — no explicit invocation syntax is needed. Examples that trigger it:

```
"How should we structure our product teams?"
"We keep shipping features nobody uses — what's going wrong?"
"Help me write our product strategy for next quarter."
"Rewrite these OKRs — they're really just a feature list."
"What should we prototype before building this?"
```

Claude will apply the relevant section of `SKILL.md` (team topology, the four discovery risks, OKR construction, anti-pattern detection, etc.) and pull structured templates from `references/templates.md` when drafting an artifact.

## Contents

`SKILL.md` covers, in order: the feature-team vs. empowered-team distinction, team topology (the product trio), vision & strategy, continuous discovery & the four big risks, OKRs, coaching & product leadership, common anti-patterns, how to apply the skill, and partial/staged adoption for constrained orgs. See its own table of contents for section links.

`references/templates.md` holds copyable templates (Four Risks checklist, Opportunity Solution Tree, OKR rewrite pattern, vision/strategy doc skeleton) that Claude loads on demand rather than keeping inline in `SKILL.md`.

## Development

This is a documentation/prompt-content project — no build, test, or lint tooling. Changes are made directly to `SKILL.md` and `references/templates.md`. Review changes are tracked under `docs/reviews/`, implementation plans under `docs/plans/`.

## Contributing

This is a personal skill project; feel free to fork and adapt it for your own use. If proposing changes, keep the source-of-truth split intact: operating instructions in `SKILL.md`, situational reference material in `references/`.

## License

[MIT](LICENSE)
