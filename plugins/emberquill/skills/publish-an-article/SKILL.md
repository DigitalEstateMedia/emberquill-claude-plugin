---
name: publish-an-article
description: Take an approved Emberquill article toward its live site through the emberquill MCP server (find it, check it is ready, put it on the publish calendar). Use when the user asks to publish, schedule or "make live" an article in Emberquill.
---

# Publish an article with Emberquill

Emberquill never publishes from chat directly: an approved article goes on the publish calendar,
and the calendar opens the pull request or WordPress post, runs its checks and takes it live.

1. If the emberquill tools are missing, tell the user to run `/mcp` and authenticate emberquill, then stop.
2. `list_projects` (or `whoami`) to confirm which project; ask if there is more than one.
3. `find_content` with a few distinctive words from the title. Several matches: list them with
   their status and ask which one.
4. Read its status:
   - Approved, not on the calendar: `queue_for_calendar` with the exact title. It lands on the
     calendar as "Ready to publish live"; the user picks a time on the Publish calendar page
     (or the project's auto-schedule does).
   - Drafted or reviewed: it needs a decision first. Use the `review-and-approve` skill.
   - Already scheduled, waiting for its pull request, or published: say so and stop.
   - Held or failed: use the `fix-a-failed-publish` skill.
5. Tell the user exactly what you did and what happens next. Never say an article is live unless
   its status says published.
