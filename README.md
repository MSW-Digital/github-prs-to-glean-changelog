# GitHub PRs to Glean Feed Changelog

An Agent Skill that turns merged GitHub pull requests into Glean Feed changelog drafts.

The skill uses your agent's GitHub tools to read PRs and the Glean Feed MCP server to create changelog drafts. Glean Feed does not connect to GitHub, store GitHub tokens, or run a background sync.

## What it does

- Reads merged pull requests from a repo and date range.
- Checks existing Glean Feed entries to avoid duplicate drafts.
- Skips internal/noisy work.
- Groups user-visible changes into logical changelog entries.
- Shows the full proposed changelog text before writing.
- Creates drafts in Glean Feed after approval.
- Publishes only if you explicitly approve publishing after seeing the full text.

## Requirements

- An agent that supports Agent Skills.
- GitHub tools or GitHub MCP connected in that agent.
- Glean Feed MCP connected with `changelog:read` and `changelog:write`.

Glean Feed MCP endpoint:

```text
https://app.gleanfeed.com/api/mcp
```

## Install

Install with the skills CLI:

```bash
npx skills add MSW-Digital/github-prs-to-glean-changelog --skill github-prs-to-glean-changelog
```

Or clone this repo and place or symlink the folder into your agent's skills directory. Most skill-compatible agents expect a folder containing `SKILL.md`.

## Use

Example:

```text
Use github-prs-to-glean-changelog.

Review merged PRs in MSW-Digital/my-app since the last published Glean Feed changelog entry. Group customer-visible changes into logical changelog entries. Show me the full proposed text before creating drafts. Do not publish unless I explicitly approve publishing.
```

## Safety

The skill is draft-first. It treats "looks good" as approval to create drafts only. Publishing requires explicit publish intent, such as "publish all" or "publish entry 1", after the full text is shown in chat.

## License

MIT
