# Emberquill for Claude Code

Connect Claude Code to your Emberquill account and fill your Knowledge Base with `/fill-knowledge-base`. Claude's answers arrive as suggestions you confirm on the Knowledge Base page. Nothing reaches your agents until you confirm it.

## Install

In Claude Code:

```
/plugin marketplace add DigitalEstateMedia/emberquill-claude-plugin
/plugin install emberquill@emberquill
```

Then type `/mcp`, pick **emberquill** and choose **Authenticate**. Sign in to Emberquill and approve.

Then run `/fill-knowledge-base`.

## Without the plugin

```
claude mcp add --transport http emberquill https://api.emberquill.ai/mcp
```

## Skills

- **fill-knowledge-base** — Fill or update your Emberquill Knowledge Base from conversation context, files, and the company website. Suggestions wait for your confirmation on the Knowledge Base page.
- **publish-an-article** — Take an approved article toward its live site through the emberquill MCP server (find it, check readiness, queue it on the publish calendar).
- **review-and-approve** — Review an Emberquill draft and approve, reject, or request changes through the emberquill MCP server.
- **fix-a-failed-publish** — Diagnose why an article did not publish (held, failed, stuck, CI/site build red, address collision) and give the one next step using emberquill MCP tools.
