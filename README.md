# phived for agents

Plugins that connect Cursor, Claude Code, and Codex to your
[phived](https://phived.com) canvas. Your agent can read your lists, add
tasks, check them off, and move them around, and every change shows up on
your canvas as it lands.

Each plugin adds phived's hosted MCP server (`https://phived.com/mcp`) and a
short skill that tells the agent when and how to use it. The first time the
agent calls phived, you approve access in your browser. Agents need
[phived PRO](https://phived.com/app?checkout=monthly).

## Cursor

Open phived → Settings → Agents and click **Add to Cursor**, or install the
plugin from Cursor's chat:

```text
/add-plugin phived@https://github.com/LukeberryPi/phived-plugins
```

## Claude Code

```sh
claude plugin marketplace add LukeberryPi/phived-plugins
claude plugin install phived@phived
```

Then run `/mcp` in Claude Code, pick phived, and authenticate. Without the
plugin, `claude mcp add --transport http --scope user phived https://phived.com/mcp`
adds the server alone.

## Codex

```sh
codex plugin marketplace add LukeberryPi/phived-plugins
```

Then install phived from `/plugins`. Without the plugin,
`codex mcp add phived --url https://phived.com/mcp` adds the server alone.

## Claude, ChatGPT, VS Code, and other apps

Add `https://phived.com/mcp` as a custom connector or remote MCP server. The
app asks you to sign in to phived and allow access.

## The phived CLI

Agents that run shell commands can use phived with no setup beyond a sign-in.
Every MCP tool is a command:

```sh
npx phived login
npx phived create-list groceries milk eggs
npx phived read-canvas --json
```

## Your data

Agents see only what you allow on the consent page, and Settings → Agents in
phived lists every agent you connected, what it changed, and a Disconnect
button. What an agent reads goes wherever that agent sends it, usually its
model provider. See the [privacy policy](https://phived.com/privacy).
