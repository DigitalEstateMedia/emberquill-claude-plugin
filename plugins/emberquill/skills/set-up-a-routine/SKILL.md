---
name: set-up-a-routine
description: Set up an Emberquill routine, a recurring goal Emberquill works toward on its own, through the emberquill MCP server. Use when the user wants Emberquill to keep doing something on a schedule, such as publishing N articles a month, watching competitors, fixing slipping pages, or refreshing keyword research.
---

# Set up a routine

1. If the emberquill MCP server isn't connected or authenticated, tell the user to run `/mcp`, choose Authenticate for emberquill, then stop.
2. `list_projects`; if there is more than one, ask which project (show slug + name). Use the slug as `project` on every call. Over MCP every change needs the project admin role. If the user is an editor, they can look but not create: tell them to ask an admin or use the Routines page in the dashboard.
3. `list_routines` first. If a routine already covers the goal, say so and offer to leave it or pause it instead of making a duplicate.
4. Ask at most two questions, and skip any the user already answered:
   - What monthly credit budget should it stay within?
   - How should drafts go live: ask first, go on the Action Checklist, or go automatically through the publish calendar?
5. `propose_routine` with the goal and those answers. It writes nothing. Show the plan card in plain words: when it runs, the steps in order, and the credits per run and per month.
6. Only on a clear yes, call `create_routine`. It asks the user to confirm again; that is expected.
7. Offer `test_run_routine`. A test run is a dry run and spends no credits. Explain its notes in plain words (what it would do, what it skipped and why). A real run does spend credits.
8. Tell them how to manage it later:
   - `pause_routine` and `resume_routine` stop and restart it.
   - `list_routine_runs` shows what each run did.
   - Routines are deleted only on the dashboard, by an admin.

## Gotchas
- Nothing goes live by itself. Even on "automatically", publishing goes through the publish calendar's checks.
- Do not create a routine from a vague goal. Ask what "done" looks like (how many, how often) if it is unclear.
- Never raise the budget to make a plan fit; show the numbers and let the user decide.
