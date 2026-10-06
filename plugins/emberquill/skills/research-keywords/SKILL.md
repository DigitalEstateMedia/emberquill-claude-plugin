---
name: research-keywords
description: Find, check, group and target keywords for an Emberquill project through the emberquill MCP server. Use when the user pastes or proposes a keyword list, asks which keywords to add, wants keywords grouped into clusters, or wants to pick keywords the team should win.
---

# Research and organise keywords

1. If the emberquill MCP server isn't connected or authenticated, tell the user to run `/mcp`, choose Authenticate for emberquill, then stop.
2. `list_projects`; if there is more than one, ask which project (show slug + name). Use the slug as `project` on every call. Reading works for everyone; every change needs the project admin role. If the user is an editor, tell them to ask an admin or use the dashboard.
3. Run `check_keywords` on the pasted or proposed list before anything else. Report each keyword by its result:
   - `in_list` or `covered`: already there or already written about. Never add it again.
   - `ranking`: the site already gets impressions for it. Worth targeting or improving the page, not a new article.
   - `rejected`: it was turned down before. Say so and only revisit if the user insists.
   - `new`: free to add.
4. Show the grouped result and ask which `new` keywords to add. Call `add_keywords` with only the ones the user picks.
5. For demand, use `get_keyword_volumes` and `list_keywords`. Give volumes as rough monthly searches, and say when there is no number.
6. To organise, propose clusters and an intent for each keyword, then after a yes call `set_keyword_fields` (cluster / intent).
7. Ask which keywords the team wants to win, then call `set_target_keywords` with exactly those.
8. Report progress with `get_target_summary` (how many are targeted, how many are ranking or covered).

## Gotchas
- Ask before adding or targeting anything; never add the whole list by default.
- Targeting a keyword does not publish anything. Articles still go through review and the publish calendar.
