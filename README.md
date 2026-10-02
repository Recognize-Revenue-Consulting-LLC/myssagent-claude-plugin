# MySSAgent for Financial Advisors

A Claude plugin that brings Social Security claiming support into an advisor's day: client meeting briefs, survivor checks, plain-English client drafts, and a quick estimator for prospects. It connects to the MySSAgent connector, so every figure comes from the MySSAgent engine.

Status: v0.1.0, local build. Not published and not submitted anywhere.

## What it does

| Skill | Use it to |
|---|---|
| `meeting-prep` | Turn a client's stored analysis into a one-page brief: recommended claiming, spousal and survivor points, what was assumed versus supplied, questions to ask. |
| `survivor-check` | Lay out what the surviving spouse keeps, using the survivor figures the engine returns. |
| `client-explainer` | Draft a plain-English note for a client. Draft only, marked for your review, never sent. |
| `quick-estimate` | Run the public estimator for a prospect from a birth month and year plus the full-retirement-age benefit on their SSA statement. |
| `setup` | Connect, sign in, and troubleshoot. |

## Install

For local testing in Claude Code:

```
claude --plugin-dir C:\myssagent-claude-plugin
```

Skills appear as `/myssagent-for-financial-advisors:meeting-prep` and so on. The plugin declares the MySSAgent connector (`myssagent`, https://myssagent.com/api/mcp) in `.mcp.json`, so there is nothing else to configure. Run the `setup` skill for sign-in steps.

## Accounts

- The public estimator works without an account.
- `list_clients`, `get_client_report`, and `run_client_analysis` require a MySSAgent advisor account. Sign in with your myssagent.com account the first time an advisor tool is used.

## The no-math invariant

Every Social Security figure in any output must come from a MySSAgent tool's output. The skills tell Claude never to compute, extrapolate, multiply, total, or estimate claiming figures, even when the arithmetic is simple. When a number you want is not in the tool output, the skill says so and names the tool or run that would produce it. This is deliberate: the engine is deterministic and the model is not, so the model reports and explains and never calculates.

The skills also never give investment, tax, or legal advice, and they present results as decision support for your professional judgment.

## Privacy

- No Social Security number is collected, requested, or needed. The skills tell Claude not to repeat one if it is pasted.
- The public estimator uses only a birth month and year and a benefit amount, and stores nothing.
- Advisor tools return only your own clients. Clients are added and their statements ingested in the advisor dashboard (https://myssagent.com/advisor), not through chat.
- `run_client_analysis` overwrites a client's stored analysis. The skills ask for a clear yes before calling it.
- Privacy policy: https://myssagent.com/privacy

## Layout

```
.claude-plugin/plugin.json   manifest
.mcp.json                    the remote MySSAgent connector (HTTP, OAuth discovery)
skills/<name>/SKILL.md       one folder per skill
```

## Open items before any public release

- Choose a license and add a LICENSE file.
- A public GitHub repository is required for directory submission. Not created yet.
- The connector listing must be live first.
