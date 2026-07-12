# Changelog forms

Choose the form that matches the dominant customer outcome. Combine forms only when the entry stays easy to scan.

## Shared editorial bar

- Lead with the changed customer experience.
- Explain why it matters with concrete, verified language.
- Name the affected surface when the title would otherwise be ambiguous.
- Use a short title and one or two compact paragraphs; use bullets when a release contains several parallel outcomes.
- Match the scope of every claim to the evidence. Qualify platform, plan, role, or circumstance when relevant.
- Keep implementation vocabulary, branch names, ticket numbers, private repository links, stack traces, and private customer data in the review notes.
- Prefer direct openings over announcement filler.

## Feature

Use this order:

1. New capability.
2. Customer problem it resolves.
3. Where or how to use it, when that is not obvious.

Example:

> **Schedule product updates**
>
> Prepare an update now and choose when it should go live. Scheduled entries keep their draft status until the selected time, so you can coordinate announcements without returning to publish manually.

## Improvement

Use this order:

1. Previous friction.
2. Improved behavior.
3. Practical benefit.

Example:

> **Faster feedback triage**
>
> Feedback filters now stay in place as you review requests. You can move between items and return to the same queue without rebuilding your view.

## Bug fix

Use this order:

1. User-observable symptom or affected task.
2. Corrected behavior.
3. Scope qualifier or workaround removal when verified.

Make the corrected experience the headline. Describe the symptom narrowly enough that every affected case is supported by the source work.

Example:

> **Reliable custom-domain verification**
>
> Domain checks now recognize valid DNS records after they propagate, instead of leaving some verified domains pending. Workspaces affected by delayed verification can retry normally from domain settings.

## Reliability or performance

State the observable improvement and the conditions under which it applies. Use measurements only when the source provides them. Avoid promising universal speed or availability from an internal refactor.

Example:

> **More dependable widget loading**
>
> The feedback widget now recovers when its first network request is interrupted, reducing cases where the launcher remained unavailable until a page refresh.

## Security

Explain the protection or safer default without publishing exploit steps, sensitive architecture, or unverified impact. Coordinate disclosure language with the user when the source suggests an active vulnerability or embargo.

## API, SDK, or integration

Name the affected interface, compatibility impact, and required customer action. Distinguish additive changes from breaking changes. Include migration instructions or a documentation link only when verified and customer-accessible.

## Documentation-only

Publish documentation work only when it materially changes a customer's ability to adopt or use the product. Describe the newly supported task, not the act of editing documentation.

## Mixed release

Use one short outcome-led introduction followed by a compact list. Keep unrelated outcomes in separate entries when a shared title would become generic.
