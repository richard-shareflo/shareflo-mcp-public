# Shareflo MCP Server

An OAuth-protected [MCP](https://modelcontextprotocol.io) server that exposes Shareflo's UK cap table data and actions to AI clients such as Claude Desktop and Claude.ai.

Shareflo is a UK cap table management platform for early-stage startups, covering equity instruments, stakeholder records, share/option events, vesting schedules, and Companies House compliance. Free for up to 20 stakeholders. Learn more at [shareflo.co.uk](https://www.shareflo.co.uk).

This repository documents the connector. It does not contain the server's source code — see [`server.json`](server.json) for the registry listing.

## Endpoint

```
https://mcp.shareflo.co.uk/mcp
```

Transport: `streamable-http`

## Connecting

1. In your MCP client (e.g. Claude Desktop or Claude.ai), add a new connector using the endpoint above.
2. You'll be redirected to log in to your Shareflo account via OAuth.
3. Once authorised, the client can call the tools below, scoped to your company's data.

No API keys or manual credentials are required — authentication happens through Shareflo's own login.

Step-by-step guide with screenshots: [Connecting Shareflo to Claude with the MCP connector](https://www.shareflo.co.uk/help-centre/connecting-shareflo-to-claude-with-the-mcp-connector).

## Example prompts

- "List every stakeholder and what they hold."
- "Show me all option holdings and the share class each one belongs to."
- "Create a new option class for our EMI scheme."
- "Add Sam Patel as a stakeholder and award them 10,000 options."
- "Who has access to manage our company account?"

## Tools

| Tool                  | Purpose                                                                                                                                       |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `get_instruments`     | Returns all share/option classes for your company                                                                                             |
| `create_instrument`   | Creates a new share class or option class                                                                                                     |
| `get_stakeholders`    | Returns all stakeholders for your company                                                                                                     |
| `create_stakeholder`  | Creates a new stakeholder                                                                                                                     |
| `get_holdings`        | Returns holdings (optionally filtered to a stakeholder)                                                                                       |
| `create_holding`      | Allots shares or awards options to a stakeholder                                                                                              |
| `get_representatives` | Returns representatives for a stakeholder or all company users                                                                                |
| `add_representative`  | Adds a new user to manage a stakeholder or company account                                                                                    |
| `unlock_shareflo`     | Internal initialization step called automatically by the client at the start of a session; returns the operating rules the other tools follow |

All data access is scoped to the authenticated user's company via Shareflo's own privacy rules — this connector does not add or bypass any access control.

## Registry

Published on the official [MCP Registry](https://registry.modelcontextprotocol.io) as `uk.co.shareflo/shareflo`.

## Support

Questions or issues: see the [Shareflo Help Centre](https://www.shareflo.co.uk/help-centre) or visit [shareflo.co.uk](https://www.shareflo.co.uk).

## License

MIT — see [LICENSE](LICENSE).
