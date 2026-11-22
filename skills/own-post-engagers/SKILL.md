---
name: own-post-engagers
description: Step 1 of LinkedIn engager scoring. Pulls every comment and reaction on the user's own LinkedIn posts from the last 14 days through Apify (never through the user's own LinkedIn login), checks no comment was missed, and saves one row per engagement. Use for "pull the engagers from my posts", "who commented on my posts this week", or the daily engager run.
---

# Own-post engagers (step 1 of 9)

## What this does

Reads who reacted to and commented on the user's own LinkedIn posts, and saves one row per engagement. It runs daily. It never acts on LinkedIn.

## What you need

- An Apify account. The token is in `~/.config/apify.key` (one line). Never print it, log it or paste it anywhere.
- The user's LinkedIn profile URL. Ask once and save it in `engagers/config.json` as `"me"`.

## Steps

1. **Check spend first.** Read this month's Apify usage (`GET https://api.apify.com/v2/users/me/usage/monthly`). If it is near the user's limit, stop and tell them. Ask the user for a monthly cap the first time and save it in `config.json` as `"apify_cap_usd"`.
2. **Pull the posts.** Run the Apify actor `harvestapi/linkedin-profile-posts` with:
   - `targetUrls`: the user's profile URL
   - `postedLimitDate`: 14 days ago (`YYYY-MM-DD`)
   - `includeReposts`: false, `includeQuotePosts`: true
   - `scrapeComments`: true, `maxComments`: 1000
   - `scrapeReactions`: true, `maxReactions`: 1000
   - Set a spend limit on every run (`maxTotalChargeUsd`). Start the run, then check back until it ends. Big pulls take longer than 5 minutes, so don't wait on one open request.
3. **Save the raw pull** in `engagers/raw/<date>-own.json` before doing anything else. Raw data lets you rebuild later without paying again.
4. **Build rows.** One row per reaction and per comment:
   `{ post_id, post_url, post_date, type: "comment" | "reaction", reaction_type, comment_text, comment_date, linkedin_url, name, headline }`
   - Comments carry their own date. Reactions have no date, so use today.
   - Skip the user's own comments.
   - Skip company pages and private members. Count them in the report.
5. **Never miss a comment.** For each post, compare the comments you read with LinkedIn's comment count. If they differ, name the post in the report. If a post shows engagement on LinkedIn but the pull found nobody, don't load it. The scraper may have changed.
6. **Late comments.** Once a week, also pull comments only (`scrapeReactions: false`) for posts 8 to 30 days old.
7. **Save** the rows to `engagers/rows/<date>-own.json` and hand them to step 3 (engager-lookup) or straight to step 4 (one-record).

## Coded profile links

Reactors often come back with a coded link (`linkedin.com/in/ACoAA...`) instead of a public one. Step 3 turns these into public links. Never load a coded link as if it were a person.

## Report

Posts checked, comments read vs LinkedIn's count per post, reactions, new people, company pages and private members skipped, Apify spend this month.

## Rules

- Never open LinkedIn in the user's browser for this. Never like, comment, message or connect.
- A re-run must store nothing twice. Give each row an id made from post id + person + type (+ comment id), and skip ids you already have.
