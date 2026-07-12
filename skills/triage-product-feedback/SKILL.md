---
name: triage-product-feedback
description: Feedback triage across Glean Feed requests. Use when the user asks to group recent feedback, identify themes or duplicates, separate bugs from requests, or recommend product follow-up.
---

# Triage product feedback

Turn an inbox into a decision surface. Preserve the customer's underlying problem while separating duplicate wording, request type, and recommended action.

## 1. Bound the inbox

Resolve the Glean Feed workspace and select a concrete request window by date, stage, board, search, or count. Require `feedback:read`; use `roadmap:read`, `changelog:read`, and repository access when available to check planned or shipped overlap.

Completion: the workspace, filters, pagination limit, and available evidence sources are explicit.

## 2. Read the requests

List every request in the window and follow pagination to the agreed bound. Read the full request and comments when its intent, severity, or relationship to another request is unclear.

For each request, capture id, title, stage, problem, affected task, type, engagement signals, specificity, and missing context. Use one primary type: bug, feature request, usability problem, support question, documentation gap, or unclear.

Completion: every request is classified or marked uninspected with a reason.

## 3. Form themes and duplicate sets

Read [triage-rubric.md](references/triage-rubric.md). Group requests by shared underlying problem, not repeated words. A request may support one primary theme and additional related themes.

Mark duplicates only when the desired outcome and affected context match. Assign High, Medium, or Low confidence and name the evidence; keep near-neighbors separate.

Completion: every inspected request belongs to a primary theme, and every duplicate candidate has a target, confidence, and rationale.

## 4. Compare current work

Check matching roadmap items, published updates, and current repository behavior when access exists. Distinguish unresolved demand from work that is planned, in progress, shipped but undiscovered, or no longer aligned.

Completion: each theme has an overlap status supported by an item id, entry id, repository path, or explicit unknown.

## 5. Recommend the queue

Recommend one next action per request or duplicate set: investigate, ask a follow-up, merge candidate, plan, monitor, document, respond with an existing solution, or close with rationale. Rank actions using problem severity, reach, recurrence, strategic fit, and confidence; votes alone cannot determine order.

Completion: every inspected request has a next action and no workspace data has been changed.

## 6. Report

Return:

1. Coverage and filters
2. Theme summary
3. Duplicate candidates
4. Bugs and urgent reliability signals
5. Requests needing follow-up
6. Roadmap, changelog, or code overlap
7. Recommended queue
8. Uninspected items and evidence gaps

Keep mutations outside this skill. If the user wants merges, stage changes, comments, or roadmap writes, present the proposed ids and actions as a separate approval-ready plan.

Completion: the report accounts for every request in the bounded inbox by id.
