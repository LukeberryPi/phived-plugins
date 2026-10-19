# phived for agents

Plugins that connect Cursor, Claude Code, and Codex to your
[phived](https://phived.com) canvas. Your agent can read your lists, add
tasks, check them off, and move them around, and every change shows up on
your canvas as it lands.

Each plugin adds phived's hosted MCP server (`https://phived.com/mcp`) and a
short skill that tells the agent when and how to use it. The first time the
agent calls phived, you approve access in your browser. Agents need
[phived PRO](https://phived.com/app?checkout=monthly).

[phived.com/connect](https://phived.com/connect) has a one-click install or a
command for each app, and [phived.com/llms.txt](https://phived.com/llms.txt)
tells an agent how to connect and what each tool does.

## Cursor

Click **Add to Cursor** on [phived.com/connect](https://phived.com/connect),
then sign in when Cursor asks.

Teams can import this repository as a team marketplace (Dashboard → Plugins &
MCPs → Add Marketplace → Import from Repo) to install the plugin with its
skill. To try it alone, copy `plugins/phived` to
`~/.cursor/plugins/local/phived` and reload Cursor.

## Claude Code

```sh
claude plugin install phived --marketplace LukeberryPi/phived-plugins
```

Then run `/mcp` in Claude Code, pick `plugin:phived:phived`, and sign in.
Without the plugin,
`claude mcp add --transport http --scope user phived https://phived.com/mcp`
adds the server alone.

## Codex

```sh
codex plugin marketplace add LukeberryPi/phived-plugins
codex plugin add phived@phived
codex mcp login phived
```

Without the plugin, `codex mcp add phived --url https://phived.com/mcp` adds
the server and signs you in.

## Claude, VS Code, and other apps

- Claude on the web, desktop, and mobile:
  [add phived as a connector](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=phived&connectorUrl=https%3A%2F%2Fphived.com%2Fmcp).
- VS Code: click **Add to VS Code** on
  [phived.com/connect](https://phived.com/connect), or run
  `code --add-mcp '{"name":"phived","type":"http","url":"https://phived.com/mcp"}'`.
- Anything else: add `https://phived.com/mcp` as a custom connector or
  remote MCP server.

Each app asks you to sign in to phived and allow access.

## MCP Registry

`server.json` lists the hosted server in the
[MCP Registry](https://registry.modelcontextprotocol.io) as
`io.github.LukeberryPi/phived`.

## The phived CLI

Agents that run shell commands can use phived with no setup beyond a sign-in.
Every MCP tool is a command:

```sh
npx -y phived@1 login
npx -y phived@1 create-list groceries milk eggs
npx -y phived@1 read-canvas --json
```

## Your data

Agents see only what you allow on the consent page, and Settings → Agents in
phived lists every agent you connected, what it changed, and a Disconnect
button. What an agent reads goes wherever that agent sends it, usually its
model provider. See the [privacy policy](https://phived.com/privacy).
