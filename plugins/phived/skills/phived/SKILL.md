---
name: phived
description: Use when the user mentions phived, their todo canvas, or asks to read, add, check off, edit, move, or restore tasks or lists in phived.
---

# phived

phived is the user's todo canvas. Each list has a tag (its name) and tasks;
habit lists reset daily, weekly, or monthly. Every change shows up on the
user's canvas as it lands.

## With the phived MCP tools

- Call `read_canvas` before changing anything, then name lists by tag and
  tasks by their full text. When two match, phived answers with short ids;
  pass the id instead.
- `complete_tasks` moves regular tasks to history. `restore_task` brings one
  back, and `read_history` lists them.
- Agents cannot delete lists. `merge_lists` folds one list into another, and
  the user can undo it in phived.

## When a call fails

- **Not signed in:** the user approves access in their browser once. In
  Claude Code that is `/mcp`, then phived, then Authenticate; in Cursor, the
  Connect button on the phived tool card; in Codex, `codex mcp login phived`.
- **`not_entitled`:** agents need phived PRO. Give the user the checkout link
  from the error instead of retrying.
- **`rate_limited`:** wait a minute before the next change.

## Without MCP: the phived CLI

Every tool is also a command, named like the tool in kebab case, with the
same arguments and results. Keep the `@1`: older versions are a placeholder
that exits 0 without doing anything.

```sh
npx -y phived@1 login                     # once, in the browser
npx -y phived@1 create-list groceries milk eggs
npx -y phived@1 read-canvas --json
npx -y phived@1 tools --json              # every command with its JSON Schema
```

Exit codes: `0` done, `1` refused (stderr says why), `2` usage, `3` signed
out (run `npx -y phived@1 login`), `4` needs phived PRO, `5` rate limited.
