# Cut the Yup

A personal agent skill for concise, professional replies in high-level bullets.

Inspired by [Caveman](https://github.com/JuliusBrussee/caveman). Independently maintained; not affiliated with its authors.

## Style

- Lead with the result, answer, or recommendation.
- Default to a few short, flat bullets with natural grammar.
- Keep useful caveats, evidence, and next actions.
- Expand when the user requests detail or the task needs it.

This is a standalone presentation skill with no runtime, proxy, hooks, model
router, or service dependencies. Token savings are an intent, not a measured claim.

## Use in Codex

Install from this private repository while authenticated to GitHub:

```sh
npx skills add savelieve/cut-the-yup --skill cut-the-yup -g
```

While the initial implementation is under review, use the task branch:

```sh
npx skills add https://github.com/savelieve/cut-the-yup/tree/feature/professional-bullet-replies --skill cut-the-yup -g
```

Activate with `$cut-the-yup`. Say "normal replies" to stop using the style in
the current chat. Explicit requests for another format or more detail win.
Automatic selection depends on the host; installation does not enforce a global
style. A new chat may be needed for discovery.

## Examples

Completed task:

> - Fixed the expired-session redirect loop.
> - Focused tests passed; browser verification remains pending.
> - PR is open for review.

Recommendation:

> - Keep the existing component and add an optional compact layout.
> - This reuses current styles and avoids maintaining a second component.

Blocker:

> - Deployment is blocked by missing staging credentials.
> - Provide staging access so the deployment check can run.

## Validation

Validate the skill with the skill-creator `quick_validate.py` helper. Review
these cases when changing it; they are review cases, not automated behavior tests.

| Request | Expected behavior |
| --- | --- |
| "What changed?" | Result first; short bullets; brief verification evidence. |
| "Did it pass?" when tests were not run | State that it is untested. |
| "Explain the tradeoffs in detail" | Give the requested depth and relevant alternatives. |
| "Write the full document" | Deliver the complete document in its appropriate format. |
| "Give me the command" | Keep the exact command in a runnable code block. |
| "List all 12 findings" | Include every finding despite the default bullet count. |
| "Normal replies" | Stop applying the style in the current chat. |

## Attribution

Adapted from [Caveman's skill](https://github.com/JuliusBrussee/caveman/blob/9b243662ff98d392bc0a95b865a554583d71be75/skills/caveman/SKILL.md),
reviewed at commit `9b243662ff98d392bc0a95b865a554583d71be75`.
Rewritten for professional bullets, flexible depth, and accurate status reporting.

Licensed under Apache-2.0. Relevant upstream attribution is preserved in NOTICE;
the upstream MIT notice is retained in LICENSE-MIT.
