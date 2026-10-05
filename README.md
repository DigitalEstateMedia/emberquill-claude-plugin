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
