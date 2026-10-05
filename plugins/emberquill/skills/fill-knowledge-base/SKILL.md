---
name: fill-knowledge-base
description: Use when the user wants Claude to fill or update their Emberquill Knowledge Base (business, products, markets, keywords, brand voice, SEO rules, authors).
---

1. If the emberquill MCP server isn't connected/authenticated, tell the user to run `/mcp` and choose Authenticate for emberquill, then stop.
2. Call `list_projects`; if more than one, ask which project (show slug + name). Use the slug as `project` on every call.
3. Call `get_kb_score` to see what's missing.
4. For each section except guardrails (business, keywords, brand, seo, geo, eeat): call `get_config_section`, then `update_config_section` with facts from the conversation, the user's files in this folder, and the company website. Only facts you are confident in. Over MCP these arrive as suggestions the user confirms on the Knowledge Base page — nothing goes live by itself.
5. Put anything useful that fits no field into `business → knowledge_notes`.
6. Ask before guessing a price, a location, a credential or a policy.
7. Finish with `get_kb_score` again and tell the user what's still missing and that suggestions are waiting on the Knowledge Base page to confirm.