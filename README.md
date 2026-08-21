# cagan-skill

A Claude Code skill that encodes Marty Cagan / SVPG product development methodology — the frameworks from *INSPIRED*, *EMPOWERED*, and *TRANSFORMED* — so Claude can act as a diagnostic lens and generative toolkit for product strategy, team topology, discovery, and OKRs.

## Highlights

- **Diagnostic lens** — classifies a described team/org against Cagan's feature-team vs. empowered-team distinction before giving advice
- **Generative toolkit** — drafts vision docs, strategy docs, OKRs, opportunity solution trees, and test plans using Cagan's structures, not generic PM templates
- **Broad, implicit triggering** — fires on product-strategy language even when the user doesn't say "Cagan" (e.g. "our roadmap is just a list of features," "how do I coach this PM")
- **Copyable templates** — a Four Risks checklist and Opportunity Solution Tree template in `references/templates.md`, pulled in only when needed
- **Staged-adoption aware** — coaches orgs that can't fully adopt empowered teams (agencies, early-stage startups, regulated industries) rather than treating the model as all-or-nothing

## Installation

### Claude Code

```bash
cp -r /path/to/cagan-skill/ ~/.claude/skills/product-discovery-cagan/
```

Or symlink:
```bash
ln -s /path/to/cagan-skill/ ~/.claude/skills/product-discovery-cagan
```

Then invoke by describing product-strategy, team-structure, discovery, or roadmap work — no explicit `/` command is needed; see Usage below.

### Codex

Place the plugin directory where Codex can find it, then add an entry to your marketplace:

**`~/.agents/plugins/marketplace.json`** (create if absent):
```json
{
  "name": "personal",
  "interface": { "displayName": "Personal Plugins" },
  "plugins": [
    {
      "name": "product-discovery-cagan",
      "source": { "source": "local", "path": "/path/to/cagan-skill/" },
      "policy": { "installation": "AVAILABLE", "authentication": "ON_INSTALL" },
      "category": "Productivity"
    }
  ]
}
```

### Antigravity

**Global install** (all workspaces):
```bash
cp -r /path/to/cagan-skill/ ~/.gemini/antigravity/skills/product-discovery-cagan/
```

**Workspace install** (current project only):
```bash
cp -r /path/to/cagan-skill/ .agents/skills/product-discovery-cagan/
```

The root `SKILL.md` has no Claude Code-specific metadata, so it is used as-is — no separate Antigravity variant is needed.

Skills are auto-discovered. You can also mention the skill by name to force activation.

### Gemini CLI

Gemini CLI installs extensions directly from GitHub:

```bash
gemini extensions install https://github.com/keithmackay/cagan-skill
```

To update:
```bash
gemini extensions update product-discovery-cagan
```

The skill is auto-discovered from `GEMINI.md` after installation.

## Compatibility

| Feature | Claude Code | Codex | Antigravity | Gemini CLI |
|---------|:-----------:|:-----:|:-----------:|:----------:|
| Core skill | ✅ | ✅ | ✅ | ✅ |
| Sub-documents (`references/`) | ✅ | ✅ | ✅ | ✅ |

No Claude Code-specific frontmatter (`metadata`, `retrieval`, `tags`) or subagent dispatch is used by this skill, so there are no platform gaps to document — it ports cleanly to all four platforms.

Legend: ✅ Supported · ❌ Not supported

## References

- **Claude Code Skills:** https://code.claude.com/docs/en/skills
- **Claude Code Complete Guide (PDF):** https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf
- **Codex Plugins:** https://developers.openai.com/codex/plugins/build
- **Antigravity Skills:** https://antigravity.google/docs/skills
- **Gemini CLI Extensions:** https://github.com/google-gemini/gemini-cli/blob/main/docs/extension.md
- **Agent Skills open standard:** https://agentskills.io/home

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

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release history.

## License

[MIT](LICENSE)
