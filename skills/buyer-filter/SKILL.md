---
name: buyer-filter
description: Step 5 of LinkedIn engager scoring. Decides which engagers are worth keeping. Keeps every commenter, keeps reactors whose headline shows a buyer title, drops students, job seekers and the user's own anti-ICP, and grades each person Builder, Buyer or Unknown. Use for "filter my engagers", "which of these are buyers", or before paying for lookups.
---

# Buyer filter (step 5 of 9)

## What this does

A comment takes effort. A like takes one tap. So every commenter stays, and reactors stay only if their headline looks like someone who buys.

## Set it up once

Ask the user three questions and save the answers in `engagers/filter.json`:

1. **Who buys from you?** Titles that sign or decide. A typical B2B start: founder, co-founder, owner, CEO, president, managing director or partner, CRO, CMO, VP / head / director of sales, marketing, growth or revenue, RevOps, sales operations, business development manager.
2. **Who never buys?** The anti-ICP. Always: student, intern, retired, seeking or open to work, recruiter. Add the user's own: for example agencies that resell what you sell, or people who build it themselves.
3. **Who is a competitor?** That list lives in step 2's `competitors.json`. Step 6 handles them.

## Steps

1. **Commenters:** keep all of them.
2. **Reactors:** keep if the headline matches a buyer title and does not match a never-buys word. Match whole words, case-insensitive.
3. **Competitor staff** (from step 2): keep them for now. Step 6 needs them, to put them on do not contact.
4. **Grade each kept person**, only where the field is blank. Never overwrite it:
   - **Builder:** builds sales or CRM systems for themselves or clients (engineers, technical founders of agencies, "I build with Claude / n8n / Zapier").
   - **Buyer:** runs sales or a business and buys tools to do it.
   - **Unknown:** not enough to tell.
   Add a reason of 25 words or fewer naming the evidence. The grade never removes anyone. It tells you how to talk to them.
5. **Report** kept and dropped, by reason.

## Rules

- When unsure, keep. A missed buyer costs a sale. A wrong keep costs one message.
- The filter works on what the headline says, not on guesses about the person.
