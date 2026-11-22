# Jobkit plugins

Connect Claude, ChatGPT and Codex to [Jobkit](https://jobkit.cz): find jobs and
customers, create work and plan visits in the company you sign in to.

The plugin adds the Jobkit connection and a short workflow guide for the
assistant. It contains no credentials and runs nothing on your machine. Every
call is authorized by Jobkit against your membership, permissions and the tools
your company has enabled.

## Install

### Claude web and desktop

1. Download [jobkit-claude.zip](https://github.com/struo-ai/jobkit-plugins/releases/latest/download/jobkit-claude.zip).
2. Open **Customize → Plugins → Add → Upload plugin** and upload it.
3. Open the plugin's **Connectors** tab, connect Jobkit, sign in and choose your company.

On Team and Enterprise plans an owner may need to add the plugin first.

### Claude Code

```sh
claude plugin marketplace add struo-ai/jobkit-plugins
claude plugin install jobkit@jobkit
```

Run `/mcp`, sign in to Jobkit and choose your company.

### Codex and ChatGPT desktop

```sh
codex plugin marketplace add struo-ai/jobkit-plugins
```

Install Jobkit from that source in the plugin list, then sign in.

### Without a plugin

Any client that supports remote MCP servers can connect directly. This gives the
assistant the tools without the workflow guide.

| Client | Server URL |
| --- | --- |
| Claude: **Customize → Connectors → Add custom connector** | `https://app.jobkit.cz/mcp` |
| ChatGPT: **Plugins → + → Add custom MCP server** | `https://app.jobkit.cz/mcp/chatgpt` |

Remove a direct connection before enabling the plugin, or the same tools appear twice.

## First request

> Show which Jobkit company I connected, then list my latest jobs.

If the company is wrong, reconnect and choose another one.

## Troubleshooting

- **Sign-in required or 401:** reconnect Jobkit in the client.
- **Access denied:** your membership, permissions, billing or enabled tools changed in Jobkit.
- **Missing or outdated tools:** refresh the connection and start a new conversation.

Removing the plugin does not revoke access; disconnect Jobkit in the client as
well. Never paste tokens into a conversation or a support message.

[Support](https://jobkit.cz/kontakt) · [Privacy](https://jobkit.cz/soukromi)

## Development

One directory, `plugins/jobkit`, serves both ecosystems: Claude reads
`.claude-plugin/plugin.json` and `.mcp.json`, OpenAI clients read `plugin.json`
and `mcp.json`, and both load `skills/`. The two marketplace catalogs at the
repository root point at it.

To release, bump `version` in both manifests, merge, then push a
matching `v<version>` tag. The release workflow attaches the Claude upload
archive and its checksum.
