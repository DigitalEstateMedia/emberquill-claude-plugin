---
name: fix-a-failed-publish
description: Find out why an Emberquill article did not publish (held, failed, stuck on the calendar, CI or site build red, address taken) and give the one next step, using the emberquill MCP tools. Use when the user asks why an Emberquill publish failed, is stuck or did not go live.
---

# Publish troubleshooting

1. Find the item with `find_content` and read its calendar sentence and status. Quote the reason the
   platform gives, in its own words, before saying anything else. Never retry blindly.
2. Match the reason to one case below and give that one next step. If the reason is a short code or a
   sentence you don't recognise, load the reference `references/failure-reasons.md` and use its row.

## Cases

- **Held for re-review**: the publish PR changes more than expected. Say what was flagged (the card
  shows the passages). Use `release_publish_hold` only if the user agrees after hearing that.
- **Address already taken (a collision)**: revising can't fix it. Change the slug or Destination URL in
  the item's panel on /pages (only before a PR is open), or publish it as a revision of the page that
  already has that address.
- **Wrong address**: fix the Destination URL in the item's panel on /pages, only before a PR is open.
  After a PR is open, reject the article to close the PR first.
- **The writing model returned nothing, too much, or changed nothing**: `submit_approval` with action
  revise and notes that say exactly what to change.
- **CI or a site build failed** (Cloudflare Pages, Vercel, Netlify), or the PR merged but the URL never
  verified: the fix is in that build, so pass on the link to its log. Once fixed, Publish live on /pages.
  It never fixes itself; publish repair tries twice on its own and then stops.
- **Stuck on the calendar**: `unschedule_article`, then reschedule on /publish-calendar.
- **Failed three times and no longer retried** (the message starts with "[attempt 3]"): the hourly
  publish stops picking it up. Fix the cause above, then publish it once by hand from /pages.

## Gotchas

- A row can say "published" while the live page did not change (an update that changed only a date).
  If the user says the page looks the same, open the merged PR and check what it changed.
- Approving or rejecting is the user's decision. In AI Chat it is a card the user must Apply, so never say it
  is done; over MCP `submit_approval` acts at once, so confirm with the user before calling it.