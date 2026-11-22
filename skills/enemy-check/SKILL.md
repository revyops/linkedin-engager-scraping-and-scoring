---
name: enemy-check
description: Step 6 of LinkedIn engager scoring. Keeps competitor staff and software vendors out of outreach. Links people with no company record to the competitor their headline names, marks every competitor and its staff as do not contact, and never excludes freelancers or consultants. Use for "check for competitors in my list", "make sure we don't message a competitor", or before any outreach.
---

# Enemy check (step 6 of 9)

## What this does

Competitors watch each other's posts. Without this step, your outreach thanks a rival's head of sales for their interest. This skill throws them back.

## Why the obvious way fails

Most suppression lists drop people by their *company*. But most commenters arrive with no company record at all, so a competitor's founder walks straight through. The fix is to read the headline.

## Steps

1. **Make each competitor a company** in RevyOps with an enemy status (or your own word for it), from `competitors.json`.
2. **Staff from step 2:** link each one to their competitor's company.
3. **People with no company:** read the headline. If it says they work at a known competitor ("Founder of Acme", "@ Acme CRM"), link them to that company. Its status then keeps them out of every list.
4. **Vendors not on your list:** if the headline clearly says they found or sell a sales-software product ("CEO at Widgetly, the AI dialer platform"), leave them out of outreach and list them in the report. You decide whether to add that company.
5. **Do not contact.** Mark every person on an enemy company as do not contact.
6. **Everyone else passes:** freelancers, consultants, engineers, agencies with no software product, unclear or empty headlines.

## Rules

- **Enemy is a company status, never a person status.** It follows the company, so a person who changes jobs leaves it behind.
- **A wrong enemy costs more than a missed one.** A missed vendor costs one message. A wrong enemy loses a buyer for good, and can break a filter for everyone like them.
- Some brands are claimed on profiles by people who don't work there ("Certified Acme Partner", "Acme Expert"). Never link from those words. For those brands, use the company's own employee list instead.
- Never unlink or mark anyone because of a match you doubt. Note it for the user.
