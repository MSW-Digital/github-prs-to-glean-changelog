---
name: github-prs-to-glean-changelog
description: Changelog drafting from merged GitHub pull requests into Glean Feed. Use when the user wants to turn a GitHub release window into customer-facing changelog drafts or publish approved drafts.
---

# GitHub PRs to Glean Feed changelog

Build a release map before writing. Draft in Glean Feed only after the user reviews the exact customer-facing copy; publish only after a separate, explicit approval.

## 1. Resolve the boundary

Identify the GitHub repository, Glean Feed workspace, and release window. Prefer an explicit range, release, or tag comparison. Otherwise use the latest published Glean Feed entry as a clue, state the inferred start time, and ask only when the inference could omit work.

Require GitHub read access and `changelog:read` for the evidence pass. Require `changelog:write` only when the user approves creating or publishing entries. Use `feedback:read` and `roadmap:read` when available to find related customer requests and completed work.

Completion: the repository, workspace, start, end, and available scopes are explicit.

## 2. Inventory the release

Read every merged PR in the window, following pagination. Collect its title, body, labels, merge time, URL, and changed-file summary when available. Read existing published entries and drafts far enough back to detect matching source work or customer outcomes.

Classify each PR as feature, improvement, bug fix, reliability, security, API or SDK, documentation, internal-only, revert, or duplicate. Keep customer-visible behavior; account for internal-only work in the skipped list.

Completion: every PR in the window is kept, skipped, or marked uninspected with a reason.

## 3. Build the release map

Group kept PRs by customer outcome. One outcome may combine several PRs; one PR may justify multiple entries only when it creates independently understandable outcomes. Search Glean Feed for closely related feedback and roadmap work when those scopes are available. Link only confident matches.

Completion: every kept PR belongs to a proposed entry, and every proposed feedback or roadmap link has stated evidence.

## 4. Draft the entries

Read [changelog-forms.md](references/changelog-forms.md) before drafting and apply the form matching each entry's dominant change type. Write the public body from verified behavior. Keep GitHub URLs and internal evidence in the review notes; include a source link in public copy only when the user requests it and the URL is intended for customers.

Completion: each entry has a title, complete body, optional version, proposed tags, proposed linked feedback ids, and no unsupported claim.

## 5. Review before writing

Show, for each proposed entry:

- exact title and body
- change type and customer outcome
- source PRs, separately from the public body
- proposed version, tags, and linked feedback ids
- assumptions or evidence gaps

Then show skipped PRs with reasons and any uninspected work. Ask the user to revise, skip, or create specific drafts.

Completion: the user has reviewed the exact text and named which drafts to create.

## 6. Create approved drafts

Call `create_changelog_entry` only for approved entries. Pass confident `postIds` and `tagIds`, and use an idempotency key when supported. A request to “publish” at this stage creates drafts first and returns them for a final review.

Completion: every approved entry has a draft id or a reported tool failure; nothing is published.

## 7. Publish on final approval

Show the exact stored title and body for each draft selected for publication. Explain that first publication can notify subscribed customers. Call `publish_changelog_entry` only after the user explicitly says to publish the named drafts after this review. Treat “looks good” as draft approval.

Completion: every selected draft is published with its id, or the failure is reported; all other drafts remain unpublished.

## Final report

Report the release window, drafts created, entries published, linked feedback, skipped PRs, and uninspected work.
