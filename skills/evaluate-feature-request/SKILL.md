---
name: evaluate-feature-request
description: Feature-request evaluation against repository and Glean Feed evidence. Use when the user asks whether a product request is worth pursuing, fits the current codebase, or overlaps existing feedback and roadmap work.
---

# Evaluate a feature request

Treat the request as a decision, not a specification. Build an evidence trail across customer demand, current product behavior, roadmap commitments, and implementation cost.

## 1. Frame the decision

Capture the requested outcome, affected users, stated problem, and decision horizon. Resolve the product repository and Glean Feed workspace. Record which of repository access, `feedback:read`, `roadmap:read`, `changelog:read`, and `workspace:read` are available; continue with an explicit evidence gap when access is missing.

Completion: the request is restated as a customer problem and every evidence source is available or marked missing.

## 2. Inspect customer evidence

Search Glean Feed with the request's language and plausible synonyms. Read matching requests and relevant comments, following pagination far enough to distinguish one-off wording from a recurring problem. Check the roadmap and changelog for planned, shipped, or abandoned overlap.

Capture request ids, stages, counts, dates, distinct use cases, workarounds, and contradictions. Treat votes as one signal rather than the verdict.

Completion: every claimed demand signal cites a Glean Feed item, or the report states that no supporting item was found.

## 3. Inspect product reality

Read the repository's product intent, current implementation, tests, public interfaces, and nearby dependencies. Determine whether the capability already exists fully or partially, which surfaces would change, and which security, data, migration, compatibility, or operational constraints apply.

Prefer executable behavior and current code over plans. Cite file paths for material claims.

Completion: current behavior, overlap, affected surfaces, and material constraints are each supported by repository evidence or marked unknown.

## 4. Make the decision

Read [decision-rubric.md](references/decision-rubric.md), score each dimension with the available evidence, and choose exactly one verdict:

- Pursue now
- Validate first
- Defer
- Decline
- Already addressed

Use confidence High only when both customer and repository evidence are direct; use Medium when one side relies on inference; use Low when a missing source could reverse the verdict.

Completion: one verdict and confidence level follow from the scored evidence, and the strongest counterargument is addressed.

## 5. Report

Return these headings:

1. Verdict and confidence
2. Customer problem
3. Evidence from Glean Feed
4. Current product and code behavior
5. Roadmap or changelog overlap
6. Expected value
7. Implementation and maintenance cost
8. Risks and unknowns
9. Recommended next step
10. Evidence that would change the decision

End after the recommendation. Treat roadmap creation, feedback stage changes, and customer replies as separate write workflows requiring a new user request.

Completion: every factual claim has a request id, roadmap item id, changelog entry id, repository path, or an explicit inference label.
