---
name: competitor-engagers
description: Step 2 of LinkedIn engager scoring. Pulls last week's posts from a list of competitor LinkedIn profiles through Apify, with their comments and reactions, and saves one row per engagement. Keeps every commenter; reactors are filtered in step 5. Use for "who engaged with my competitors' posts", "pull competitor engagers", or the weekly competitor run.
---

# Competitor engagers (step 2 of 9)

## What this does

Your competitors' posts are a bigger pond than yours. The people who comment there are often shopping. This skill pulls them once a week.

## What you need

- The Apify token in `~/.config/apify.key`.
- A list of competitor profiles in `engagers/competitors.json`:
  `[{ "name": "Acme CRM", "profile": "https://www.linkedin.com/in/acme-founder/", "company_page": "acme-crm", "domain": "acmecrm.com", "active": true }]`
  Use the founders and the company page: founders' posts usually get far more engagement than the brand's.

## Set it up

Ask the user for up to ten competitors. For each one, ask for the founder's profile and the company page. Add `aliases` for names people write in headlines ("Acme", "AcmeCRM"). If a name is a common word ("Copper", "Zero"), match only the full name or the domain, never the bare word.

## Steps

1. **Check spend** as in step 1. Ask for a per-run cap the first time and save it.
2. **Pull** with `harvestapi/linkedin-profile-posts`: `targetUrls` = the active profiles, `postedLimitDate` = 7 days ago, up to 10 posts a profile, `includeReposts: false`, comments up to 1000 and reactions up to 300 a post.
3. **Save the raw pull** in `engagers/raw/<date>-competitors.json`.
4. **Build rows** the same way as step 1, plus `competitor: <name>`.
5. **Keep every commenter.** Reactors are many and cheap to give, so step 5 (buyer-filter) decides which reactors stay before anyone pays for a lookup.
6. **Mark competitor staff.** If a headline says the person works at a watched competitor ("Head of Sales at Acme CRM"), set `staff: true` on the row. Step 6 puts them on do not contact.
7. **Report** posts per competitor, comments, reactions, rows kept, spend. If a profile returned no posts, say so: they may have stopped posting, or the run hit its cap.

## Rules

- Never use the user's own LinkedIn account. If the scraper fails, report it. Do not fall back to the browser.
- Never raise the spend cap without the user's yes.
- If you stop on the cap, never trim profiles or reactions to fit. Report it and let the user decide.
