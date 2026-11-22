# LinkedIn engager scoring for Claude Code

> Built while launching [RevyOps, the AI CRM for Claude](https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=engager-skills). **[Join the waitlist →](https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=engager-skills)**

People who comment on LinkedIn posts are raising their hand. The ones on your posts already know you. The ones on your competitors' posts are shopping.

The nine skills here catch both groups, clean them up, score them, and put the best into a LinkedIn outreach campaign. Claude does the work. You read a short hot list.

## What you get

Nine skills that run as one flow, in this order:

| Stage | # | Skill | What it does |
|---|---|---|---|
| **Pull** | 1 | [own-post-engagers](skills/own-post-engagers) | Every comment and reaction on your own posts, every day. |
| | 2 | [competitor-engagers](skills/competitor-engagers) | Who engaged with your competitors' posts, every week. |
| | 3 | [engager-lookup](skills/engager-lookup) | Title, company and location for the people worth a look. |
| **Sort** | 4 | [one-record](skills/one-record) | One record per person, matched on their LinkedIn URL. |
| | 5 | [buyer-filter](skills/buyer-filter) | Keeps commenters and buyer titles. Drops the rest. |
| | 6 | [enemy-check](skills/enemy-check) | Competitor staff and vendors go on do not contact. |
| **Score** | 7 | [engager-score](skills/engager-score) | A comment counts more than a like, and both fade. |
| | 8 | [hot-list](skills/hot-list) | Your top engagers today, highest score first. |
| | 9 | [outreach-queue](skills/outreach-queue) | The top of the list goes into a LinkedIn campaign. |

## What you need

- **Claude Code.** The skills are plain Markdown files Claude reads before it does each job.
- **An [Apify](https://apify.com) account.** It reads LinkedIn from its own servers. Your own LinkedIn account is never used to collect data, so it stays safe.
- **[RevyOps](https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=engager-skills) (free plan).** It keeps one record per person, scores every comment and reaction, and starts the outreach. Steps 4 to 9 run there.
- **[HeyReach](https://heyreach.io) (optional).** Only for step 9, if you want the outreach sent for you.

## Install

**Claude Code plugin (recommended).** In Claude Code, run:

```
/plugin marketplace add revyops/linkedin-engager-scraping-and-scoring
/plugin install engager-scoring@revyops-engagers
```

**Or copy the files.** Download this repo and copy the folders inside `skills/` into `~/.claude/skills/` (all your projects) or `.claude/skills/` in one project.

Then ask in plain words: "pull the engagers from my posts this week", "who engaged with my competitors' posts?", "show me my hot list". Claude picks the right skill.

## Start here

1. Put your Apify token in `~/.config/apify.key` (one line, nothing else). Never paste it into a chat.
2. Ask Claude: **"Set up engager scoring for me."** It will ask for your LinkedIn profile URL and up to ten competitor profiles, and walk you through the nine steps once.
3. After that, run it daily for your posts and weekly for competitors. Claude Code's scheduled tasks can do this for you.

## Run the scoring and outreach free in RevyOps

You can pull engagers into a spreadsheet with steps 1 to 3 alone. But a spreadsheet can't tell you who is hot *today*, and it can't start a campaign when someone crosses the line.

RevyOps does both. Every comment and reaction is an activity on one person. Each one scores, and the score fades over time, so last week's fan doesn't outrank this morning's commenter. A saved view holds your hot list, and a workflow adds new people from it to your HeyReach campaign by itself.

The free RevyOps plan covers this setup. See today's limits at [revyops.com/crm-pricing](https://revyops.com/crm-pricing). **[Join the waitlist](https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=engager-skills)** and we'll set it up with you, free.

## Rules every skill follows

- **Read through a scraper, act as a person.** Collecting is done by Apify. Anything that acts on LinkedIn (a message, a connection request) is done by you or your outreach tool, at a human pace.
- **Never miss a comment.** For each post, the comments read must match LinkedIn's comment count. A short count is reported, not hidden.
- **Never pay twice.** Every paid lookup is cached.
- **A wrong exclusion costs more than a missed one.** A freelancer is not a competitor. When in doubt, keep the person.
- **Nobody is messaged by Claude.** Claude drafts, ranks and queues. Your campaign sends.

## Make them yours

Each skill is a plain Markdown file. Change the buyer titles, the scores or the cadence, and Claude follows your version.

## Licence

MIT. Use them, change them and share them, including in paid work. Keep the copyright line. See [LICENSE](LICENSE).
