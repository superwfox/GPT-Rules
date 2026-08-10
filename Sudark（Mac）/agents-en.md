# Global User Collaboration Guidelines

## Execute Clear Tasks by Default

- When the goal, scope, and expected outcome are clear and there is no ambiguity or barrier to understanding, complete the task directly without asking the user for confirmation again.
- Do not use an approval-based workflow for such clear tasks. Do not require approval of the plan, execution, or testing before beginning implementation.
- Explain the situation and wait for user confirmation only when the request is ambiguous, requires expanding the business scope, requires an architectural change not explicitly requested by the user, changes an already confirmed design direction, creates a new external impact, or requires adding a new production dependency.

## Strictly Align With the Scope

- Do not independently expand business functionality, change the product direction, or make design decisions on the user's behalf based on vague context.
- If implementation reveals a need to expand the business scope, change an already confirmed design direction, or create a new external impact, pause and realign with the user.

## Production Dependency Authorization Boundary

- Ask for confirmation before adding any new production dependency. First explain why it is necessary, its impact, and the available alternatives, then obtain the user's confirmation. Do not interpret "Complete Directly Related Work" as permission to introduce a new production dependency autonomously.

## Complete Directly Related Work

- Once the scope is clear, independently complete directly related configuration of existing dependencies, completeness measures, security safeguards, error handling, and release protections. Adding a new production dependency is not an item that may be completed autonomously.
- This related work should be limited to preventing production failures, security issues, or unusable states caused by omitted requirements. The user does not need to specify each item individually.
- On completion, clearly state which related items were added independently and why, but do not use this as a reason to implement unrelated business functionality or expand the confirmed product scope.

## Default Delivery Pace

- A task is complete when the implementation is complete and the logic is correct. Unless the user explicitly requests testing, do not run tests, so the work can be delivered as quickly as possible.
- For Web interface changes, you must perform the necessary basic visual checks. Unless the user explicitly requests otherwise, do not expand this into full automated testing, compatibility testing, or additional acceptance procedures.
- Do not adapt web pages for mobile by default. Handle mobile requirements only when the user explicitly requests them.

## Safe Spacing for Web Text Controls

- Text controls with a background or border, including buttons and labels, must preserve explicit and stable horizontal and vertical safe padding. Text and icons must not touch the edges, be clipped, overflow, or overlap one another.
- Link-style buttons, including `a` and `RouterLink`, must be checked for their final computed padding and CSS specificity. Global link reset styles must not override button-component spacing.
- Basic Web visual checks must use the interface's actual longest copy to verify surrounding whitespace and text-icon spacing. When a shared style causes the same problem across components, fix the shared root cause instead of adding a patch for only one page.

## Git Commit Message Format

- All commit messages must use the following fixed format. Do not use Conventional Commits prefixes such as `fix:` or `feat:` unless the user explicitly requests otherwise:

```text
中文摘要 ｜ eng brief :

details | 要点：
1. xxx
2. xxx
```

- The first line must contain both a Chinese summary and a brief English description, separated by the full-width `｜` character, and must end with an ASCII colon `:`.
- Keep one blank line between the summary and the details. The details heading must be exactly `details | 要点：`.
- Use a `1. 2. 3.` numbered list to describe the actual changes in the commit. Each item must be specific and complete rather than vague.

## Mandatory Pre-Deployment Verification

- Before any commit, merge, or push that triggers deployment, run the project's complete test suite, type checks, and server-side tests. Prefer the project's aggregate verification command when one exists.
- For `lingkun-web`, run at least `npm run test:all` before deployment and confirm that the unit tests, `vue-tsc` type checks, and `go test ./...` all pass.
- If any pre-deployment check fails, do not proceed with deployment or pushing. Fix the failure and rerun the complete verification until it passes.
