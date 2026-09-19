<div align="center">

<img src="assets/cover.png" alt="Trendyol through HeyMetra's MCP server" width="100%">

# Trendyol &times; HeyMetra

**Marketplace orders, listings and what Trendyol deducted.**

Your orders live in Trendyol. What you spent to win them lives in your ad accounts. One question, both answers.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-trendyol-1f6feb)](https://heymetra.com/connectors/trendyol/)

```
https://mcp.heymetra.com/mcp
```

</div>

---

## Ask it things like

> How many orders came in this week, and how many are still unshipped?

> Which listings are out of stock right now?

> What did Trendyol deduct in commission last month?

> How much of last month's sales came back as returns?

No dashboard, no export, no query language. You ask in the assistant you already use and the answer comes back with the account it came from.

## Connect Trendyol

**1. Open Integration Information in the Seller panel**

Sign in at partner.trendyol.com, open the account menu at the top right and choose Account Information, then Integration Information. The page lists your store's API credentials together.

> It is the Seller (Partner) panel, not the Trendyol app or the shopping site — the same login does not reach it unless the account is a seller account.

**2. Copy the Seller ID**

It is the short number at the top of that page, usually six digits. Trendyol also calls it Supplier ID in its own documentation; they are the same number.

> This one is not a secret. It travels on every request as part of the identifier Trendyol requires, so HeyMetra keeps it beside the connection rather than in the vault.

**3. Copy the API Key and the API Secret**

Two separate values on the same page, one under the other. Copy them into the two separate boxes in HeyMetra, in the order the panel shows them.

> They look alike — both are twenty characters of letters and digits — and swapping them produces a login failure with nothing on screen to say which way round they went.

**4. Paste all three in HeyMetra and save**

Choose Trendyol on the Connections screen, fill the three boxes and save. HeyMetra joins the key and the secret the way Trendyol's API expects, so there is nothing to encode yourself. Saving checks the credential against Trendyol immediately: a green connection means the store answered.

**5. Add HeyMetra to the assistant you use**

Claude, ChatGPT, Cursor or Codex — HeyMetra gives you the address and the key to paste. The Trendyol tools appear in that assistant once it connects.

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans only an owner can add it, under Organization settings._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — Settings → Security and login → Developer mode, then chatgpt.com/plugins</summary>

Paste the address above into Settings → Security and login → Developer mode, then chatgpt.com/plugins.

_The endpoint has to include its /mcp path here._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_XAI calls this “bring your own MCP”._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Settings → Connectors → Custom connector → Remote</summary>

Paste the address above into Settings → Connectors → Custom connector → Remote.

_Perplexity documents it as a Pro, Max and Enterprise feature._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_Or a .mcp.json in the project root; /mcp inside a session shows what connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Under an [mcp_servers.<name>] section, then codex mcp login._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Leave the static OAuth fields empty — they exist for servers that cannot register themselves._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_The key is serverUrl, not url — the one every other JSON client spells differently._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Trendyol is a read-only source — HeyMetra reads it to answer questions and never changes the account.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Orders** | Read orders, statuses, and shipments — Trendyol keeps three months of orders. Older periods are refused rather than answered as if nothing was sold in them — settlements reach further back.. | No, read only |
| **Listings** | Read listings, stock, and prices — Approved listings only. A listing still awaiting approval is not on sale, so it is not counted here.. | No, read only |
| **Finance** | Read settlements, commission, and payouts — Settlement lines, not a total: Trendyol reports each sale, return, coupon and commission separately and HeyMetra does not add them up for you.. | No, read only |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Reads how many orders each connected store took in a period and what they came to, with the status of each store's orders. Reported per store.
- Reads what is listed for sale in each connected store: titles, SKUs or barcodes, prices and stock levels.
- Reads what each connected account took in a period — payments, store sales, marketplace settlements — reported per account and never added together.
</details>

## When something goes wrong

<details>
<summary>Saving fails with a login error and the credentials look right.</summary>

**Why:** The API Key and the API Secret are in each other's boxes. They are the same length and the same alphabet, and the panel shows them one under the other.

**Fix:** Swap the two values and save again. Nothing was stored, so there is nothing to undo.

</details>

<details>
<summary>Saving fails and the Integration Information page shows no API Key at all.</summary>

**Why:** Trendyol issues marketplace API credentials per store and a newly opened store does not have them until the store is approved and open for sales.

**Fix:** Wait until the store is open, then reopen the page. If the store is open and the values are still missing, Trendyol seller support issues them.

</details>

<details>
<summary>The connection saves, and an assistant is told there were no orders in a month you know you sold in.</summary>

**Why:** Trendyol's order service keeps three months and answers an empty list beyond it rather than an error.

**Fix:** Ask about a period inside the last three months. HeyMetra refuses an older one by name rather than reporting it as quiet — settlements reach further back if what you need is the money.

</details>

<details>
<summary>An assistant reports fewer listings than the panel shows.</summary>

**Why:** Only approved listings are on sale, and only those are counted. A listing still in review is not yet a product anyone can buy.

**Fix:** Check the listing's approval state in the panel. The difference between the two numbers is what is waiting.

</details>

## What HeyMetra reads from Trendyol

Connect the seller account with the token from the Trendyol panel and your MCP client gets three tools: orders for a period with status, items and shipment details; listings with barcodes, prices, stock and whether each is on sale; and settlement lines — sales, returns, discounts and commission. Trendyol serves two weeks at a time and keeps orders for three months; the orders tool handles both internally, so a quarter is one question. Read-only: no tool changes a listing, a price or an order. Finance can be switched off for a team that should see volume but not payouts.

<details>
<summary>About Trendyol</summary>

Trendyol is Turkey’s largest e-commerce marketplace, where sellers list products and fulfil orders at scale. It’s a custom HeyMetra connector built on Trendyol’s Seller (Marketplace) API.
</details>

## One connection, not seven

The reason to read Trendyol through HeyMetra rather than through a server that only knows Trendyol is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://heymetra.com/connectors/google-ads/) · [Meta](https://heymetra.com/connectors/meta-ads/)

**Analytics** — [Google Analytics 4](https://heymetra.com/connectors/google-analytics-4/) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp)

**Ecommerce** — [Shopify](https://heymetra.com/connectors/shopify/) · **Trendyol** · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://heymetra.com/connectors/stripe/) · [HubSpot](https://heymetra.com/connectors/hubspot/) · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · [RevenueCat](https://heymetra.com/connectors/revenuecat/) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [Trendyol connector page](https://heymetra.com/connectors/trendyol/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with Trendyol. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>
