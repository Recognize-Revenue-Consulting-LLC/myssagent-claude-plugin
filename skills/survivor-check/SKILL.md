---
name: survivor-check
description: Lays out what the surviving spouse keeps under each death order for a married or widowed client, using only figures from the MySSAgent engine. Use when the advisor asks about survivor benefits, the survivor floor, "what happens if he dies first", widow or widower benefits, or how delaying affects the surviving spouse. Calls list_clients and get_client_report. Requires a MySSAgent advisor account.
---

# Survivor check

Show the advisor what the household locks in for the surviving spouse, using the engine's survivor analysis and nothing else.

## Rule that overrides everything below

Every Social Security figure must come from a MySSAgent tool's output. Never compute, extrapolate, multiply, total, or estimate claiming figures, and never convert a monthly survivor figure into a lifetime or "over N years" amount yourself. If a number the advisor wants is not in the tool output, say so and name the tool or run that would produce it. Copy figures exactly as printed, with the tool's labels and horizons.

Do not give investment, tax, or legal advice. Do not make compliance, regulatory, or liability statements. Do not describe the analysis as reviewed or endorsed by anyone.

## Steps

1. Identify the client with `list_clients` (use `search` for a name; if several match, ask which one). If the roster shows no analysis data on file, say so and point to the dashboard link in the output.
2. Call `get_client_report` with the `advisor_client_id`.
3. If a sign-in prompt or an advisor-account-required message comes back, relay it briefly and point to the `setup` skill.
4. Find the survivor section of the report. It takes one of two forms.

**Married client ("Survivor floor").** The report prints what the household locks in for the surviving spouse depending on when the higher earner claims: at 62, at full retirement age, and at 70, plus the monthly uplift from delaying to 70. It may also print a lifetime figure with a stated horizon.

**Widowed client ("Survivor analysis").** The report prints the survivor benefit at full retirement age, the client's own benefit at full retirement age, the survivor benefit as early as age 60, and a strategy line. The report states that the survivor receives the higher of the own or survivor benefit, never both.

5. Present what is there.

## Output format

**Header.** Client name, marital status, analysis date.

**Survivor table.** One row per figure the report prints, with three columns: Scenario (as the report labels it), Monthly amount (as printed), and Note (the report's own qualifier, such as "as early as age 60" or a stated horizon). For a married client, the rows are the three higher-earner claim ages. For a widowed client, the rows are the printed survivor, own, and age-60 figures.

**Death order.** Say which death order the printed figures describe. The married-client floor describes the surviving spouse once the higher earner's claim age is set. If the report does not say what the survivor keeps when the lower earner dies first, or gives no figures for the opposite order, write: "The report does not break this out for the other death order." Then name `run_client_analysis` (followed by `get_client_report`) and the dashboard link as the places to look. Do not fill that gap with your own reasoning about benefit rules.

**Delay effect.** Quote the report's monthly delay uplift as printed. If the report gives a lifetime or survivorship-horizon figure, quote it with its horizon. If it does not, say "No survivor total in this report" and do not multiply the monthly figure.

**What to confirm with the client.** Two to four questions about facts the engine cannot see: ages and health of both spouses, the surviving spouse's own work record and plans, and whether any inputs the report lists as gaps can be captured before the next engine run. No figures of your own.

**Links.** The dashboard link and framing line printed at the end of the report.

## Style

Lead with the table. American English, plain words, no hedging paragraphs. Do not name any other company or product.
