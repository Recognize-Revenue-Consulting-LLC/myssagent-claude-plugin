---
name: quick-estimate
description: Runs the public MySSAgent Social Security estimator for a prospect or quick question. Use when the advisor gives a birth month and year plus a full-retirement-age benefit from an SSA statement and wants a claiming-age table, or says "quick estimate", "run a quick number", or "what does claiming at 62 versus 70 look like for someone born in ...". Calls estimate_claiming_strategy. No sign-in or advisor account needed.
argument-hint: "[birth month and year] [monthly benefit at full retirement age]"
---

# Quick estimate for a prospect

Run the public estimator and present exactly what it returns. Arguments, if given: $ARGUMENTS

## Rule that overrides everything below

Every Social Security figure must come from the `estimate_claiming_strategy` output. Never compute, extrapolate, multiply, total, or estimate claiming figures yourself. That includes breakeven ages, "claim now versus wait" comparisons, months or dollars forgone, and cumulative totals. If the advisor asks for a number the output did not return, say so and say what the tool would need (for example a different input), or point to a full client analysis in the advisor dashboard.

Do not give investment, tax, or legal advice. Do not make compliance or liability statements.

## Inputs to collect

Ask for any that are missing, in one short message:

1. **Birth month and birth year.** Both, for example "March 1961". Month and year only; never ask for the day of birth.
2. **Monthly benefit at full retirement age**, in dollars, from the person's Social Security statement at ssa.gov/myaccount. It must be the full-retirement-age figure, not the age-62 or age-70 figure.
3. **Married or not** (optional).

Never ask for a Social Security number, a name, or any other identifier. If a Social Security number appears in the conversation, stop and handle it before anything else. Do not repeat it, and do not pass it to any tool. Tell the advisor right away: MySSAgent never needs one, so delete that message (or the whole conversation) and follow the firm's data policy for client identifiers.

## Calling the tool

Call `estimate_claiming_strategy`. Read the tool's current input schema and pass the fields it lists, using the inputs above: the birth year, the birth month if the schema lists a field for it, the full-retirement-age benefit, and the married flag if the schema lists one. Convert the month name to the month number the schema asks for. If the tool returns an input error, read the message, correct only what it names, and retry once. If it still fails, tell the advisor what the tool said.

## Presenting the result

- Show the tool's table and the notes it returns, as printed, with its labels. Do not reformat figures or add columns.
- If the tool returns only some claiming ages, or flags ages as at or past full retirement age, present just those.
- Relay any spousal or survivor note the tool returns when the person is married.
- Include the tool's closing disclaimer and the links section it ends with; those are part of the answer for the user.
- In your own wording use "recommended" and avoid "optimal". Do not name any other company or product.

## Close with one line

Say that this is a directional estimate from user-supplied numbers, and that a full analysis from the client's Social Security earnings record, including spousal and survivor coordination, comes from a client analysis in the advisor dashboard (https://myssagent.com/advisors). Offer to pull a client report if the person is already a client.
