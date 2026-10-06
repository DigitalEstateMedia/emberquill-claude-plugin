---
name: fill-knowledge-base
description: Use when the user wants Claude to fill or update their Emberquill Knowledge Base (business, products, markets, keywords, brand voice, SEO rules, authors), or to upload a document such as a price list or brand guide for review.
---

1. If the emberquill MCP server isn't connected/authenticated, tell the user to run `/mcp` and choose Authenticate for emberquill, then stop.
2. Call `list_projects`; if more than one, ask which project (show slug + name). Use the slug as `project` on every call.
3. Call `get_kb_score` to see what's missing.
4. For each section except guardrails (business, keywords, brand, seo, geo, eeat): call `get_config_section`, then `update_config_section` with facts from the conversation, the user's files in this folder, and the company website. Only facts you are confident in. Over MCP these arrive as suggestions the user confirms on the Knowledge Base page — nothing goes live by itself.
5. Put anything useful that fits no field into `business → knowledge_notes`.
6. If the user has a document worth keeping whole (a price list, service sheet, brand guide, brief or FAQ), call `upload_kb_document(project, filename, content_text | content_base64)`. Allowed types: pdf, docx, md, txt, csv, tsv, xlsx, up to 5 MB. Send `content_text` for text files and `content_base64` for binary ones. For individual facts, use `update_config_section` instead.
   - Upload one file per call, and only files the user named or clearly meant. Never sweep a whole folder.
   - The account has upload limits (about 10 an hour, 30 a day, 20 waiting for review). If the tool answers with an error, stop and tell the user what it said. Do not retry.
   - A "duplicate" answer means the file is already there. Say so and move on.
   - An upload changes nothing by itself. Emberquill turns it into suggestions a person reviews on Knowledge Base → Upload docs. Tell the user that.
7. Ask before guessing a price, a location, a credential or a policy.
8. Finish with `get_kb_score` again and tell the user what's still missing and that suggestions are waiting on the Knowledge Base page to confirm.