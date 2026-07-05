# Example Prompt

```text
Use github-prs-to-glean-changelog.

Repo: MSW-Digital/my-app
Glean Feed workspace: Cake Day

Review merged PRs since the latest published changelog entry. Ignore chores, dependency bumps, CI-only changes, tests-only changes, and internal refactors with no customer-visible behavior.

Group the remaining PRs into logical changelog entries, show me the full proposed title and body for each entry, and wait for approval before creating drafts. Do not publish unless I explicitly say to publish after reviewing the full text.
```
