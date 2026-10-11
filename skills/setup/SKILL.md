---
name: setup
description: Explains how to connect and sign in to the MySSAgent connector, what needs a MySSAgent advisor account, and what works without one. Use when the advisor asks how to get started, how to sign in or connect, why advisor tools are not working, why a sign-in or "advisor account required" message appeared, or what the plugin can do. No Social Security figures involved.
---

# Setup: connecting the MySSAgent connector

Walk the advisor through connecting, signing in, and testing. Keep it short and practical. Do not state or estimate any Social Security figures in this skill.

## What the plugin includes

The plugin bundles a connector called `myssagent` (https://myssagent.com/api/mcp) and these skills: meeting-prep, survivor-check, client-explainer, quick-estimate, and this setup guide. The connector is declared in the plugin, so installing the plugin adds it. There is nothing to paste or configure.

## Two lanes

**Public estimator (no account).** The `estimate_claiming_strategy` tool works without signing in. It takes a birth month and year plus the full-retirement-age benefit from a Social Security statement, and returns an estimate. Use the `quick-estimate` skill for it. Nothing about the person is stored.

**Advisor tools (advisor account required).** `list_clients`, `get_client_report`, and `run_client_analysis` require a MySSAgent advisor account. They work only with the advisor's own clients.

## Signing in

1. In Claude Code, run `/mcp`, choose `myssagent`, and choose to authenticate. In Cowork or claude.ai, use the Connect button that appears the first time an advisor tool is called.
2. A browser window opens. Sign in with the myssagent.com account used for the advisor dashboard and approve access.
3. Return to Claude and repeat the request. The advisor tools then run.

## If something does not work

- **Signed in but told an advisor account is required.** The sign-in worked, but that login is not linked to a MySSAgent advisor account. The message includes the link to the advisor options. The public estimator keeps working in the meantime.
- **"No clients found."** Clients are added, and their Social Security statements ingested, in the advisor dashboard at https://myssagent.com/advisor. The connector reads what is already there and cannot add clients or ingest statements.
- **A client shows no analysis data on file.** Finish that client's setup in the dashboard first.
- **Hourly limits.** The advisor tools have per-hour usage limits. If one is hit, the tool says so, and waiting is the fix.
- **Sign-in loop.** Disconnect the `myssagent` connector from `/mcp` and authenticate again.

## Test it

After signing in, ask: "List my clients." A roster table means the advisor tools are working. If the roster is empty or a message appears, relay it using the lines above.

## Privacy

The plugin and connector never ask for a Social Security number. Nothing typed into the public estimator is stored. Advisor tools return only the advisor's own clients, and client records are added in the dashboard, not through chat. Tell advisors never to type a client's Social Security number, full date of birth, or account number into the chat; none of them are needed. If a Social Security number appears in the conversation, stop and handle it before anything else. Do not repeat it, and do not pass it to any tool. Tell the advisor right away: MySSAgent never needs one, so delete that message (or the whole conversation) and follow the firm's data policy for client identifiers. Details: https://myssagent.com/privacy

## What to avoid saying

Do not describe the connector or plugin as certified, compliant, or reviewed by anyone. Do not quote prices; point to https://myssagent.com/advisors for advisor account options. Do not make claims about regulatory or liability protection.
