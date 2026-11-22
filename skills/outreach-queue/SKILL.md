---
name: outreach-queue
description: Step 9 of LinkedIn engager scoring. Sends new people from the hot list into a LinkedIn outreach campaign (HeyReach) through a RevyOps workflow, once per person, with their personal link, and logs each add. Never starts a campaign or messages anyone itself. Use for "queue my engagers for outreach", "add the hot list to HeyReach", or "set up engager outreach".
---

# Outreach queue (step 9 of 9)

## What this does

Every day, people who cross the line on your hot list go into a LinkedIn campaign, once each, without you copying a list.

## What you need

- RevyOps with the HeyReach integration connected.
- A HeyReach campaign, built and left as a draft for the user to start. Suggested first message for people who engaged with your posts: a short thank-you that names what they commented on. Never a pitch.

## Set it up

1. **The trigger is the view.** Use the outreach view from step 8 (2+ comments, all exclusions).
2. **Make a workflow in RevyOps:** when a person enters that view, add them to the HeyReach campaign with first name, last name, title, company and a personal link (a link that carries their RevyOps person id, so a click is tied to them).
3. **Test it** on one person. Ask the user before turning the workflow on: it really sends.
4. **The user starts the campaign** in HeyReach. Claude never starts, pauses or changes it.

## Every run

1. Read the workflow's recent runs. For each person added, check an "added to campaign" activity exists in RevyOps. Log the ones missing.
2. Name any failed add (person and error) in the report.
3. **Count check:** HeyReach's lead count for the campaign must equal the number of "added" activities in RevyOps. If not, say so.

## Rules

- One person, one campaign. Never add someone who is already in another one.
- Someone who asked you for something (a download, a demo) gets that follow-up, not this one. Take them out.
- Claude drafts and queues. It never sends a message.
