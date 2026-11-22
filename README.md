# Hyperdash Data MCP server

Live and historical Hyperliquid data for AI agents: markets, wallets, liquidations and analytics.

Hyperdash Data is a hosted MCP server. Connect Claude, ChatGPT, Claude Code, Codex or Cursor to it and ask about any Hyperliquid market, wallet or trader:

- Prices, funding, open interest and order books, including the order-level L4 book (Growth plan and up)
- Liquidations and liquidation heatmaps
- Wallet fills, ledgers and completed trades with realized PnL
- PnL leaderboards, trader screening and cohort positioning
- Perps, spot, HIP-3 stock and commodity markets, and HIP-4 outcomes

Every tool is read-only, one per [Hyperdash Data API](https://hyperdash.com/products/data/api) endpoint. There is nothing to install: sign in with OAuth, or use an API key in your client's settings.

```text
https://data.hyperdash.com/mcp
```

Plans start at $20 a month, and every plan runs at 99.99% uptime. See [pricing](https://hyperdash.com/pricing).

## Connect your agent

### Claude

1. Open **Settings**, then **Connectors**, and select **Add custom connector**.
2. Name it **Hyperdash Data** and paste `https://data.hyperdash.com/mcp`.
3. Select **Connect** and sign in with your Hyperdash account.
4. Choose the project and the scopes, then select **Approve access**.

The connector is saved to your Claude account, so it works on web, desktop and mobile.

### ChatGPT

1. Open **Plugins**, select **+**, then **Add custom MCP server**.
2. Paste `https://data.hyperdash.com/mcp` and choose OAuth authentication.
3. Sign in with your Hyperdash account.
4. Choose the project and the scopes, then select **Approve access**.

### Claude Code

With your key saved as `HYPERDASH_API_KEY`:

```bash
claude mcp add --transport http --scope user hyperdash-data https://data.hyperdash.com/mcp --header "Authorization: Bearer $HYPERDASH_API_KEY"
```

To sign in with OAuth instead, leave out `--header`, then run `/mcp` in Claude Code, pick `hyperdash-data` and choose **Authenticate**.

### Codex

With your key saved as `HYPERDASH_API_KEY`:

```bash
codex mcp add hyperdash-data --url https://data.hyperdash.com/mcp --bearer-token-env-var HYPERDASH_API_KEY
```

To sign in with OAuth instead, leave out `--bearer-token-env-var HYPERDASH_API_KEY`, then run `codex mcp login hyperdash-data`.

### Cursor

Add this to `~/.cursor/mcp.json`, or to `.cursor/mcp.json` in one project:

```json
{
  "mcpServers": {
    "hyperdash-data": {
      "url": "https://data.hyperdash.com/mcp",
      "headers": {
        "Authorization": "Bearer ${env:HYPERDASH_API_KEY}"
      }
    }
  }
}
```

To sign in with OAuth instead, leave out `headers`, then open **Cursor Settings**, then **MCP**, and select **Connect** next to `hyperdash-data`.

### Other clients

Add a remote MCP server with the URL `https://data.hyperdash.com/mcp`. If the client supports MCP OAuth, sign in when it opens the console. Otherwise set the `Authorization: Bearer` header in the client's configuration.

## Try it

Open a new chat and ask:

```text
Which markets had the most liquidations in the last 24 hours?
```

For better results, have the agent read the [Data skill](https://docs.hyperdash.com/skills/data) first.

## Credits and limits

Every MCP call uses your workspace's credits. To keep an agent inside a budget, open **Settings**, then **Security**, then **Connected apps** in the console, edit the connection and set a credit budget per day or month. The console's **Logs** page shows what each request used. See [Credits](https://docs.hyperdash.com/data-api/credits).

## Links

- Docs: https://docs.hyperdash.com/data-api/mcp
- Data API: https://hyperdash.com/products/data/api
- Pricing: https://hyperdash.com/pricing
- Need a feed or dataset that is not in the public API? Hyperdash's integration team can add it to any plan: sales@hyperdash.com
- Official MCP Registry name: `com.hyperdash/data`
