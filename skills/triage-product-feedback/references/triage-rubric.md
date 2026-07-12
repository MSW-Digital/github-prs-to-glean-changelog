# Feedback triage rubric

## Primary types

- **Bug:** observed behavior contradicts intended or previously working behavior.
- **Feature request:** asks for a capability the product does not currently provide.
- **Usability problem:** the capability exists, but customers cannot complete or discover the task reliably.
- **Support question:** the product supports the task and the request primarily needs guidance.
- **Documentation gap:** public instructions are missing, inaccurate, or insufficient for the task.
- **Unclear:** the desired outcome or affected context cannot be determined from the request and comments.

## Theme test

Put requests in the same primary theme when they share:

1. the customer job or affected task,
2. the obstacle preventing that job, and
3. a substantially similar successful outcome.

Shared nouns without a shared obstacle are not a theme.

## Duplicate confidence

- **High:** same desired outcome, affected surface, and relevant constraints; merging would preserve both requests' meaning.
- **Medium:** same core outcome with a meaningful difference in role, plan, platform, or workflow that should be retained.
- **Low:** similar language or adjacent needs, but merging could erase a distinct problem.

Recommend merge candidates only at High confidence. Present Medium and Low matches as related requests.

## Priority signals

Consider together:

- severity of the blocked or degraded customer task
- number and diversity of affected customers or use cases
- recurrence over time
- availability and quality of workarounds
- roadmap and product fit
- confidence in the diagnosis
- delivery and maintenance implications when repository evidence exists

An urgent reliability or data-loss signal can outrank a more popular convenience request. A highly voted request with an unclear problem stays in investigation until the problem is understood.

## Follow-up quality

Ask for the smallest missing fact that would change classification or action: reproduction conditions, affected role or platform, frequency, current workaround, or desired outcome. Tie each question to the request id.
