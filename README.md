# QRStuff Claude Code Plugins

A [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces) that lets you install and configure the **QRStuff MCP server** in Claude with a couple of commands — no manual JSON editing required.

## What's in here

This repository is a Claude Code marketplace (`qrstuff-cc-plugins`) that distributes a single plugin:

| Plugin               | Description                                                                                                                                                      |
| :------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `qrstuff-mcp-server` | Adds the QRStuff [MCP server](https://mcp.qrstuff.ai/mcp) to Claude Code, giving Claude access to the QRStuff platform for QR code generation and related tools. |

When you install the plugin, Claude Code registers the remote MCP server at `https://mcp.qrstuff.ai/mcp` for you.

## Requirements

- [Claude Code](https://code.claude.com/docs) installed and signed in.

## Installation

You can add the marketplace and install the plugin either from within an interactive Claude Code session (using `/plugin` slash commands) or from your terminal (using `claude plugin` subcommands).

### From within Claude Code

1. Add this marketplace:

```text
/plugin marketplace add qrstuff/claude-code-plugins
```

2. Install the plugin:

```text
/plugin install qrstuff-mcp-server@qrstuff-cc-plugins
```

### From the terminal

```bash
claude plugin marketplace add qrstuff/claude-code-plugins
claude plugin install qrstuff-mcp-server@qrstuff-cc-plugins
```

> The `qrstuff/claude-code-plugins` shorthand resolves to this GitHub repository (`https://github.com/qrstuff/claude-code-plugins`). You can also pass the full URL:
>
> ```bash
> claude plugin marketplace add https://github.com/qrstuff/claude-code-plugins.git
> ```

## Usage

Once the plugin is installed, the QRStuff MCP server is available to Claude automatically. Start (or restart) a Claude Code session and the `qrstuff` MCP server will be connected.

You can then ask Claude to use QRStuff in natural language, for example:

> "Generate a QR code for https://qrstuff.com using QRStuff."

To confirm the server is connected, list the active MCP servers:

```text
/mcp
```

You should see `qrstuff` in the list of connected servers.

## Updating

When a new version of the plugin or marketplace is published, refresh your local copy:

```text
/plugin marketplace update qrstuff-cc-plugins
```

Or from the terminal:

```bash
claude plugin marketplace update qrstuff-cc-plugins
```

## Uninstalling

Remove the plugin:

```text
/plugin uninstall qrstuff-mcp-server@qrstuff-cc-plugins
```

Remove the marketplace entirely:

```text
/plugin marketplace remove qrstuff-cc-plugins
```

## Repository structure

```
.
├── .claude-plugin/
│   └── marketplace.json          # Marketplace catalog (lists the plugins)
└── plugins/
    └── qrstuff-mcp-server/
        ├── .claude-plugin/
        │   └── plugin.json       # Plugin manifest
        └── .mcp.json             # MCP server configuration
```

## Troubleshooting

- **Marketplace not found**: make sure you ran `/plugin marketplace add qrstuff/claude-code-plugins` and that you have network access to GitHub.
- **`qrstuff` server not listed in `/mcp`**: restart your Claude Code session after installing, then run `/mcp` again.
- **Plugin not updating**: versions are pinned via `.claude-plugin/plugin.json`. Run `/plugin marketplace update qrstuff-cc-plugins` to fetch the latest catalog.

For more on how marketplaces and plugins work, see the official [Claude Code plugin marketplace documentation](https://code.claude.com/docs/en/plugin-marketplaces).

With ❤️ From [QRStuff](https://www.qrstuff.com/)
