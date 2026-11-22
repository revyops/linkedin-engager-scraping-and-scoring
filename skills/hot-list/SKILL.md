---
name: hot-list
description: Step 8 of LinkedIn engager scoring. Builds and reads the hot list, a saved view of engagers sorted by score with competitors, do-not-contact people and existing customers left out. Gives a short daily read of who is new at the top and why. Use for "show me my hot list", "who are my top engagers today", or "who should I reach out to".
---

# Hot list (step 8 of 9)

## What this does

One list, highest score first, of people who engaged and are safe to contact. It is the list you call from, and the list step 9 feeds from.

## Build it once (in RevyOps)

Make a saved view of people with:

- a LinkedIn comment or reaction in the last 90 days (yours or a competitor's)
- **left out:** do not contact, enemy companies, existing customers, anyone already in an open deal, anyone contacted in the last 90 days
- sorted by score, highest first
- columns: name, title, company, score, last engagement, Builder or Buyer

Name it plainly, for example "LI Engagers · Hot List".

For outreach, save a second view on top: **2 or more comments in 90 days**, same exclusions. Two comments is a person who keeps showing up.

## The daily read

When the user asks for the hot list, give:

1. The top 10, with one line each: who they are and what they engaged with.
2. Who is **new** in the top 10 since last time, and why.
3. Anyone who **commented twice** this week.

Keep it short. The user should read it in a minute.

## Rules

- The view does the filtering. Never hand-pick people out of it. If someone shouldn't be there, fix the rule.
- Never message anyone from this skill.
