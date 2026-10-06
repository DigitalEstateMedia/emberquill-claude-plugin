---
name: review-and-approve
description: Review an Emberquill draft and approve it, reject it, or send it back with notes through the emberquill MCP server. Use when the user asks to approve, reject, review or request changes to an article in Emberquill.
---

# Review and approve a draft

1. `find_content` to get the exact title and status. Only drafted or reviewed articles take a
   decision; anything already approved or publishing cannot be approved again.
2. Before approving, tell the user what they are approving: the title, its review score if shown,
   and any review notes. For an edit of a live page, say that approving replaces the live page
   once it publishes.
3. Call `submit_approval` with the exact title and:
   - `approve` — it moves on to pre-publish checks, then can go on the calendar;
   - `reject` — it is dropped (a live page keeps the version it serves);
   - `revise` — notes are required and must say exactly what to change ("add the 2025 price
     table", not "make it better"). Ask the user for them if they did not give any.
4. Approving never publishes by itself. To take it live afterwards, use the `publish-an-article`
   skill.

## Gotchas
- Do not approve on the user's behalf because a score is high; approval is their decision.
- If the draft adds statistics or claims with no source, point them out before the user approves.
