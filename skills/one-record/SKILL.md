---
name: one-record
description: Step 4 of LinkedIn engager scoring. Loads engager rows into RevyOps as one person per human, matched on the LinkedIn URL, with each comment or reaction logged as its own activity and tagged with UTMs. Use for "load my engagers", "put these engagers in the CRM", or after steps 1 to 3.
---

# One record per person (step 4 of 9)

## What this does

The same person comments on your post on Monday and reacts to a competitor's post on Thursday. That is one person with two activities, not two leads. This skill makes sure of it.

## What you need

- A RevyOps workspace (the free plan covers this) with the RevyOps connector added to Claude Code. Docs: https://docs.revyops.com
- The LinkedIn comment and reaction activities switched on in RevyOps.

## Steps

1. **Clean the URL.** Lower case, `https://www.linkedin.com/in/<slug>/`, no query string. Never use a coded `/in/ACoAA...` link (step 3 resolves those).
2. **Find the person** by LinkedIn URL. If there is none, create one by URL, with first name, last name and headline.
3. **Log one activity per engagement**: comment or reaction, with the post link, post id, post date, reaction type or comment text, the headline at the time, and the date.
4. **Tag it.** Add tracking tags (UTMs) to each activity, so later you can tell which pond a person came from:
   - source `linkedin`, medium `social`
   - campaign `linkedin-organic-post-engagers` (your posts) or `linkedin-competitor-post-engagers` (theirs)
   - content = the post id, term = `comment` or `reaction`
5. **Save the headline on the person.** Step 6 needs it.
6. **Fill fields from step 3** only where they are blank.
7. **Check it.** For one recent post, the number of comment activities in RevyOps must equal LinkedIn's comment count. Open one known commenter: the activity is on their timeline with the post link.

## Rules

- One human, one person. Two LinkedIn URLs that are plainly the same human get joined, not loaded twice.
- A re-run adds nothing: activity ids are built from post + person + type, so the same event is never stored twice.
- A company page is never a person. Count it and skip it.

## Without RevyOps

You can keep a CSV keyed on LinkedIn URL with one line per engagement. It works for a list. It won't score, fade or start outreach, which is what steps 7 to 9 need.
