---
name: meeting-prep
description: Builds a one-page Social Security brief for an advisor's client meeting. Use when the advisor names a client and asks for meeting prep, a pre-meeting brief, a claiming summary, or "what should I know about [client] before we meet". Calls the MySSAgent list_clients and get_client_report tools and reports only what they return. Requires a MySSAgent advisor account.
---

# Meeting prep: one-page Social Security brief

Produce a one-page brief the advisor can read in two minutes before a client meeting.

## Rule that overrides everything below

Every Social Security figure in the brief must come from a MySSAgent tool's output. Never compute, extrapolate, multiply, total, or estimate claiming figures yourself, even when the arithmetic looks trivial. If the advisor wants a number that is not in the tool output, say so plainly and name the tool or run that would produce it (for example, "get_client_report did not return a survivor total; run_client_analysis, then call get_client_report again, or open the dashboard link"). Copy figures exactly as the tool printed them, with the tool's own labels and time horizons.

Do not give investment, tax, or legal advice. Do not make compliance, regulatory, or liability statements. Do not describe the analysis as reviewed or endorsed by anyone. The output is decision support for the advisor's professional judgment.

If a Social Security number appears in the conversation, stop and handle it before anything else. Do not repeat it, and do not pass it to any tool. Tell the advisor right away: MySSAgent never needs one, so delete that message (or the whole conversation) and follow the firm's data policy for client identifiers.

## Steps

1. Identify the client. If the advisor gave a name, call `list_clients` with `search` set to that name. If more than one client matches, list the matches (name and status only) and ask which one. If none match, say so and stop.
2. Check the roster row. If "Analysis data on file" is "no", say the client has no analysis data yet and point to the advisor dashboard link the tool printed. Stop.
3. Call `get_client_report` with the `advisor_client_id` from step 1.
4. If either tool returns a sign-in prompt or a message that an advisor account is required, relay it in one or two sentences and point the advisor to the `setup` skill. Do not try to work around it.
5. If the report is older than the advisor expects, or the advisor says the client's circumstances changed, offer to call `run_client_analysis`. That tool overwrites the client's stored analysis, so ask for a clear yes first and never run it unprompted. After it runs, call `get_client_report` again and use the new output.
6. Write the brief using only the report text.

## Brief format

Keep it to one page. Use these headings in this order. If the report has nothing for a heading, write "not in the report" under it.

**Header.** Client name, marital status, and analysis date, as printed in the report.

**Recommended claiming.** Lead with the report's "Recommended claiming age" line, including the spouse's age if the report gives one. Then give the monthly benefit and lifetime value the report prints for that age, with the horizon the report states (for example "to age 85"). Use the word "Recommended" in your own wording and avoid the word "optimal". If the report's table marks a row with an engine flag, describe it as "the row the engine flags as highest lifetime value" and quote the figures as printed. If the report prints a cost-of-claiming-at-62 figure, include it as printed.

**Benefit by claiming age.** Reproduce the report's table rows as printed. Do not add rows, interpolate ages, or add columns.

**Spousal and survivor points.** Restate only what the report's survivor section says: the survivor floor figures, the delay uplift, or the widowed-case figures and strategy line. Quote the figures and any stated horizon. If the report has no survivor section, write "No survivor analysis in this report" and name `run_client_analysis` and the dashboard link as the way to get one. Do not infer spousal benefits the report does not print.

**Assumed versus supplied.** List the "Input gaps" the report names, if any, as items the engine had to assume or leave open. If the report lists no gaps, write "The report lists no input gaps" and do not claim that every input was verified. Mention that figures are estimates computed from the earnings data on file.

**Risk flags.** List the report's risk flags with their severity and impact amounts exactly as printed. If none, say "none on file".

**Questions to ask in the meeting.** Offer five to seven open questions that fill the gaps above and surface what the engine cannot know: health and family longevity, the client's and spouse's work and income plans, other retirement income, the spouse's intentions and timing, any input gaps the advisor can capture before the engine runs again, and the client's own priorities. Questions must not contain Social Security figures of your own.

**Links.** The dashboard link printed in the report, and the framing line the report ends with.

## Style

Plain, direct, and scannable. American English. Short sentences. No hedging paragraphs. Do not name any other company or product.
