# LeanCTX Wiring

LeanCTX is the context-efficiency layer for Claude Code, Codex, Cursor, and Copilot sessions.

## Repo Rule

When LeanCTX MCP tools are available, prefer:

- `ctx_search` for code discovery
- `ctx_tree` for directory maps
- `ctx_read` before full native file reads
- `ctx_shell` for verbose command output

Native tools are still fine for edits/writes and when LeanCTX is unavailable.

## Machine Setup

Run this on each local machine, VPS, or coding box where Claude/Codex runs:

```bash
curl -fsSL https://leanctx.com/install.sh | sh
lean-ctx setup
lean-ctx doctor
lean-ctx gain
```

Restart the shell, IDE, and coding agent after setup.

## Session Prompt

```txt
Read CLAUDE.md, docs/AI_MEMORY.md, and docs/LEAN_CTX.md first.
If LeanCTX MCP tools are available, use ctx_search, ctx_tree, ctx_read, and ctx_shell before native search/read/shell tools.
Do not scan the whole repo. Find the smallest relevant files first.
```
