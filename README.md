# Glean Feed Agent Skills

Optional Agent Skills for working with customer feedback, roadmap decisions, and product updates through the [Glean Feed MCP server](https://gleanfeed.com/docs/api/mcp).

The skills run inside your coding agent. Glean Feed does not receive repository credentials or read your codebase directly; your agent uses the repository and MCP connections you approve.

## Included skills

| Skill | Use it to |
| --- | --- |
| `github-prs-to-glean-changelog` | Turn merged GitHub pull requests into reviewed Glean Feed changelog drafts. |
| `evaluate-feature-request` | Judge a proposed feature using repository, feedback, and roadmap evidence. |
| `triage-product-feedback` | Group feedback into themes, identify duplicate candidates, and recommend next actions. |

The evaluation and triage skills are read-only. The changelog skill proposes exact copy before creating drafts and requires a separate explicit approval before publishing.

## Requirements

- An agent that supports Agent Skills.
- Glean Feed connected over MCP to the target workspace.
- A GitHub tool, GitHub MCP connection, or local repository access for workflows that inspect code.

Connect Glean Feed at:

```text
https://app.gleanfeed.com/api/mcp
```

## Install

Choose skills interactively:

```bash
npx skills add MSW-Digital/github-prs-to-glean-changelog
```

Or install one directly:

```bash
npx skills add MSW-Digital/github-prs-to-glean-changelog --skill github-prs-to-glean-changelog
npx skills add MSW-Digital/github-prs-to-glean-changelog --skill evaluate-feature-request
npx skills add MSW-Digital/github-prs-to-glean-changelog --skill triage-product-feedback
```

Review the requested Glean Feed scopes before authorizing the MCP connection. Start with read scopes and add the specific write scope only when a workflow needs it.

## Example requests

```text
Review merged PRs since our last release and propose customer-facing Glean Feed changelog drafts. Show me the exact copy before creating anything.
```

```text
Evaluate whether this feature request is worth pursuing. Compare it with our repository, related Glean Feed feedback, and existing roadmap work.
```

```text
Triage the 50 most recent Glean Feed requests. Group them by customer problem, identify high-confidence duplicates, and recommend the next action for each request. Do not change anything.
```

## Safety

- Analysis works with read-only Glean Feed scopes.
- Changelog entries are created as drafts after review.
- Publishing requires explicit approval after the stored draft is shown.
- Feedback merges, stage changes, replies, and roadmap writes stay outside the read-only evaluation and triage skills.

## License

MIT
