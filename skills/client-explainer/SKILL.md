---
name: client-explainer
description: Drafts a plain-English explanation of a client's Social Security claiming analysis that the advisor can review and send. DRAFT ONLY, clearly marked for the advisor's review, and never sent. Use when the advisor asks to explain a client's results, write a client email or summary, or "put this in language my client will understand". Calls list_clients and get_client_report. Requires a MySSAgent advisor account.
---

# Client explainer (draft only)

Write a short, warm, plain-English note that explains the engine's findings to the advisor's client. The advisor reads it, edits it, and sends it through their own channels.

## Hard limits

- This skill drafts only. Never send, post, schedule, or save the text to any email, messaging, document, or CRM tool. Show the draft in the conversation and stop. If the advisor then asks you to send it, tell them to copy it into their own email or portal after their review.
- Start the draft with this line on its own, exactly: **DRAFT: for your review before sending. Not sent.**
- Every Social Security figure must come from a MySSAgent tool's output. Never compute, extrapolate, multiply, total, or estimate claiming figures. If the advisor wants a number that is not in the output, say so and name the tool or run that would produce it.
- Do not give investment, tax, or legal advice in the draft. Do not make compliance, regulatory, or liability statements. Do not say the analysis was reviewed or endorsed by anyone.
- Do not include any Social Security number, date of birth, account number, or other identifier in the draft. If a Social Security number appears in the conversation, stop and handle it before anything else. Do not repeat it, and do not pass it to any tool. Tell the advisor right away: MySSAgent never needs one, so delete that message (or the whole conversation) and follow the firm's data policy for client identifiers.

## Steps

1. Identify the client with `list_clients` (use `search` for a name; ask if several match). If no analysis data is on file, say so and stop.
2. Call `get_client_report` with the `advisor_client_id`.
3. If a sign-in prompt or an advisor-account-required message comes back, relay it briefly and point to the `setup` skill.
4. Ask the advisor two quick things if they have not said: the tone they want (warm and brief, or more detailed) and the name to sign with. If they do not answer, use "[Advisor name]" as a placeholder.
5. Write the draft from the report only.

## Draft contents

Aim for about 200 to 300 words, at a reading level a general reader finds easy. Short sentences, no jargon (if a term like "full retirement age" is needed, explain it in a clause), no bullet-point walls.

1. A one-line opening that is personal and calm.
2. What the analysis points to: the report's recommended claiming age (and the spouse's, if given), with the monthly benefit the report prints for that age. Say "the analysis points to" or "the recommended age is". Avoid the word "optimal".
3. Why it matters for the household, in two or three sentences, using only points the report supports. If the report has a survivor section, explain in plain words what the surviving spouse would receive, quoting the printed monthly figures and any stated horizon.
4. A sentence saying these are estimates built from the earnings information on file and that the decision is the client's to make with the advisor.
5. A clear next step for the advisor to fill in, such as a meeting time, written as a bracketed placeholder.
6. The advisor's sign-off.

Do not mention risk flags or input gaps unless the advisor asks. If the report lists input gaps that affect the numbers, add one honest sentence saying a few details are still being confirmed.

## After the draft

Below the draft, add a short "Before you send" list for the advisor, kept separate from the draft text:

- Each figure in the draft appears in the report dated [analysis date from the report].
- Edit tone and any placeholders.
- Run it through your firm's normal review for client communications.

Style: American English, plain words, few em dashes. Do not name any other company or product.
