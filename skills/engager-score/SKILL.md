---
name: engager-score
description: Step 7 of LinkedIn engager scoring. Sets up scoring rules in RevyOps so each comment and reaction adds points that fade over time, a comment counts more than a reaction, competitor-post engagement counts more than your own, and a comment counts once per post. Use for "score my engagers", "set up engagement scoring", or "why is this person scored so high".
---

# Engager score (step 7 of 9)

## What this does

Gives every person one number that says how warm they are *now*. Points come from activities and fade with time, so last month's fan drops below this morning's commenter.

## Suggested starting scores

Change these to fit. Write the final version in `engagers/scores.md` so you remember why.

| Activity | Points | Loses half its points after |
|---|---|---|
| Comment on your post | 10 | 30 days |
| Reaction on your post | 3 | 14 days |
| Comment on a competitor's post | 12 | 21 days |
| Reaction on a competitor's post | 4 | 10 days |

Why competitor posts count more: the person is looking at a product like yours right now. Why comments fade slower: they take effort, so they say more.

## Steps (in RevyOps)

1. Open scoring settings. Add one rule per activity above, with its points and its fade.
2. **A comment counts once per post.** Five replies in one thread are one comment's worth of interest, not five.
3. **Other signals stack.** Website visits, email replies and form fills in RevyOps add to the same score, so a commenter who also visits your pricing page rises fast.
4. **Check it.** Pick three people you know: a fan, a stranger who commented once, a competitor's engager. Their order in step 8's list should match your gut. If not, change the points, not the list.

## Rules

- Change a score, and everyone is re-scored. Tell the user before a big change.
- When you move from custom activities to built-in ones, keep the old rule on until the old activities are moved, so nobody loses points.
