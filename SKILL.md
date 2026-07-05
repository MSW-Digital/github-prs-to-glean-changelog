---
name: github-prs-to-glean-changelog
description: Draft Glean Feed changelog entries from merged GitHub pull requests when the user asks to turn PRs, releases, commits, or recent GitHub work into changelog drafts.
---

# GitHub PRs to Glean Feed Changelog

Turn merged GitHub pull requests into Glean Feed changelog drafts. Draft by default; publish only after the user approves the full text in chat.

## Requirements

Before writing to Glean Feed, confirm both are available:

- GitHub tools or GitHub MCP for reading pull requests.
- Glean Feed MCP connected to the target workspace with `changelog:read` and `changelog:write`.

If either is missing, stop with the exact missing setup. Do not invent PRs or changelog history.

## Flow

1. Resolve the target repo and Glean Feed workspace.
   Completion: the repo and workspace are explicit, or the user has answered the missing value.

2. Choose the PR window.
   Default to merged PRs after the latest published Glean Feed changelog entry. If no published entry exists, or dates cannot be compared confidently, ask for the date range.
   Completion: the window has a concrete start and end.

3. Read existing Glean Feed changelog entries.
   Check published entries and drafts for source PR links or matching titles so the run does not create duplicate drafts.
   Completion: likely duplicates are identified, or changelog history access is reported as unavailable.

4. Read merged PRs in that window.
   Include title, body, labels, merge date, author, URL, and changed-file summary when available.
   Completion: every merged PR in the window has been considered, or the tool limit is stated.

5. Filter noise and duplicates.
   Skip chores, dependency bumps, CI-only changes, formatting, tests-only work, internal refactors with no customer-visible behavior, and revert-only PRs. Keep security, reliability, UX, API, SDK, billing, integration, portal, widget, and docs changes when customer-visible.
   Completion: each kept PR has a user-visible reason; each skipped or duplicate PR has a short reason.

6. Group by customer outcome.
   Combine related PRs into one changelog entry. Split only when outcomes would be confusing together. Do not force one entry per PR.
   Completion: every kept PR is assigned to one proposed entry.

7. Propose entries in chat before writing.
   Show the full title and body for each entry, plus source PR links. Ask whether to create drafts, revise, skip entries, or publish.
   Completion: the user has seen the full text and responded.

8. Create drafts after approval.
   Use `create_changelog_entry` with source PR links in the body. Never publish from this step.
   Completion: each approved entry has a created draft id or a reported failure.

9. Publish only on explicit publish approval.
   Approval must come after the user saw the full text and must name publish intent, such as "publish these", "publish all", or "publish entry 1". "Looks good" approves draft creation only.
   Completion: published entries are listed with ids; otherwise state that nothing was published.

## Changelog Style

- Write for customers, not engineers.
- Lead with outcome, not implementation.
- Keep titles short and specific.
- Prefer one or two concise paragraphs.
- Mention GitHub PR numbers only in the source links, not the title.
- Do not expose internal branch names, stack traces, or private customer data.

## Final Response

End with:

- Drafts created.
- Entries published, if any.
- PRs skipped with reasons.
- Any PRs not inspected because of tool limits or missing access.
