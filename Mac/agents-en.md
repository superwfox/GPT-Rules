# Global User Collaboration Guidelines

## Execute Clear Tasks by Default

- When the goal, scope, and expected outcome are clear and there is no ambiguity or barrier to understanding, complete the task directly without asking the user for confirmation again.
- Do not use an approval-based workflow for such clear tasks. Do not require approval of the plan, execution, or testing before beginning implementation.
- Explain the situation and wait for user confirmation only when the request is ambiguous, requires expanding the business scope, changes an already confirmed design direction, or creates a new external impact.

## Strictly Align With the Scope

- Do not independently expand business functionality, change the product direction, or make design decisions on the user's behalf based on vague context.
- If implementation reveals a need to expand the business scope, change an already confirmed design direction, or create a new external impact, pause and realign with the user.

## Complete Directly Related Work

- Once the scope is clear, independently complete directly related dependencies, completeness measures, security safeguards, error handling, and release protections.
- This related work should be limited to preventing production failures, security issues, or unusable states caused by omitted requirements. The user does not need to specify each item individually.
- On completion, clearly state which related items were added independently and why, but do not use this as a reason to implement unrelated business functionality or expand the confirmed product scope.

## Default Delivery Pace

- A task is complete when the implementation is complete and the logic is correct. Unless the user explicitly requests testing, do not run tests, so the work can be delivered as quickly as possible.
- For interface changes, perform any necessary basic visual checks. Unless the user explicitly requests otherwise, do not expand this into full automated testing, compatibility testing, or additional acceptance procedures.
- Do not adapt web pages for mobile by default. Handle mobile requirements only when the user explicitly requests them.

## Mandatory Pre-Deployment Verification

- Before any commit, merge, or push that triggers deployment, run the project's complete test suite, type checks, and server-side tests. Prefer the project's aggregate verification command when one exists.
- For `lingkun-web`, run at least `npm run test:all` before deployment and confirm that the unit tests, `vue-tsc` type checks, and `go test ./...` all pass.
- If any pre-deployment check fails, do not proceed with deployment or pushing. Fix the failure and rerun the complete verification until it passes.
