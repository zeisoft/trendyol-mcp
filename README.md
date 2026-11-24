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

> It is the Seller (Partner) panel, not the Trendyol app or the shopping site. The same login does not reach it unless the account is a seller account.

**2. Copy the Seller ID**

It is the short number at the top of that page, usually six digits. Trendyol also calls it Supplier ID in its own documentation; they are the same number.

> This one is not a secret. It identifies your store, so it is shown on the connection rather than hidden like the key and the secret.

**3. Copy the API Key and the API Secret**

Two separate values on the same page, one under the other. Copy them into the two separate boxes in HeyMetra, in the order the panel shows them.

> They look alike: both are twenty characters of letters and digits. Swapping them produces a login failure with nothing on screen to say which way round they went.

**4. Paste all three in HeyMetra and save**

Choose Trendyol on the Connections screen, fill the three boxes and save. HeyMetra joins the key and the secret the way Trendyol's API expects, so there is nothing to encode yourself. Saving checks the credential against Trendyol immediately: a green connection means the store answered.

**5. Add HeyMetra to the assistant you use**

Claude, ChatGPT, Grok, Perplexity, Claude Code, Codex, Cursor or Antigravity. You paste one address and sign in once, and Trendyol answers in that assistant once it connects.

The same steps are on the docs page: [Trendyol setup guide](https://heymetra.com/docs/trendyol/).

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

### One command

```bash
npx add-mcp https://mcp.heymetra.com/mcp
```

[`add-mcp`](https://www.npmjs.com/package/add-mcp) is a third-party installer that writes the configuration for Claude Code, Codex, Cursor, Antigravity, VS Code and seventeen other agents. It infers the name from the address, so the server lands as `heymetra`. Run against this endpoint before it was written here.

### Or by hand

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans, an owner adds the connector for the whole organization under Organization settings → Connectors, and each member then connects to it._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — chatgpt.com/plugins → + → Add custom MCP server</summary>

Paste the address above into chatgpt.com/plugins → + → Add custom MCP server.

_Add it on chatgpt.com in a browser, because the mobile app cannot add one. Every ChatGPT plan can, Free included. In a Business, Enterprise or Edu workspace, an admin or owner decides whether members can add custom MCP servers. ChatGPT needs the full address, including /mcp at the end._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_On Grok Business and Enterprise, a team admin has to provision the connector in xAI's cloud console before members can use it._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Plugins → Add custom → Connector → Add MCP connector → Remote</summary>

Paste the address above into Plugins → Add custom → Connector → Add MCP connector → Remote.

_In an organization, members can add a custom connector only after an admin turns on Allow members to add custom connectors, which is off by default._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_You can also add the server to a .mcp.json file at the project root. Run /mcp in a session to sign in and to check that it connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Codex reads the server from an [mcp_servers.<name>] section in config.toml, and you sign in with codex mcp login <name>._

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

_Cursor signs in to HeyMetra without a client ID or secret, so the server entry needs no auth block._

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

_Antigravity's documented key for the address is serverUrl, though it also accepts url._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Full account access** | Lets your assistant read anything in this account to answer your questions. The figures are the provider's own, not ones HeyMetra has checked. It can also propose changes: none is applied until you approve it, and HeyMetra cannot undo one afterwards — Trendyol keeps three months of orders. Older periods are refused rather than answered as if nothing was sold in them. Settlements reach further back; Approved listings only. A listing still awaiting approval is not on sale, so it is not counted here; Settlement lines, not a total: Trendyol reports each sale, return, coupon and commission separately and HeyMetra does not add them up for you. | Yes — every change waits for your approval |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Ask anything about this account and get the answer from its live data. Reads only, and the figures are the provider's own rather than ones HeyMetra has checked.
- Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.
</details>

Anything that would change something comes back as a proposal you approve, inside bounds that live in code rather than in a prompt: ±50% on a budget, 5 campaigns per action and 20 changes a rolling day, and an approval that expires after 30 minutes. [How that works](https://heymetra.com/security/).

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

**Fix:** Ask about a period inside the last three months. HeyMetra says an older one is out of reach rather than reporting it as quiet. Settlements reach further back if what you need is the money.

</details>

<details>
<summary>An assistant reports fewer listings than the panel shows.</summary>

**Why:** Only approved listings are on sale, and only those are counted. A listing still in review is not yet a product anyone can buy.

**Fix:** Check the listing's approval state in the panel. The difference between the two numbers is what is waiting.

</details>

## What HeyMetra reads from Trendyol

Connect the seller account with the credentials from the Trendyol panel, then ask about it from your assistant: orders for a period with status, items and shipment details; listings with barcodes, prices, stock and whether each is on sale; and settlement lines for sales, returns, discounts and commission. Trendyol keeps orders for three months. When you connect, you choose whether your assistant may also propose changes, and every change it proposes waits until you approve it. Finance can be switched off for a team that should see volume but not payouts.

<details>
<summary>About Trendyol</summary>

Trendyol is Turkey’s largest e-commerce marketplace, where sellers list products and fulfil orders at scale.
</details>

## One connection, not seven

The reason to read Trendyol through HeyMetra rather than through a server that only knows Trendyol is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://github.com/zeisoft/google-ads-mcp)

**Analytics** — [Google Analytics 4](https://github.com/zeisoft/google-analytics-4-mcp) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp) · [PostHog](https://github.com/zeisoft/posthog-mcp)

**Ecommerce** — **Trendyol** · [n11](https://github.com/zeisoft/n11-mcp) · [Çiçeksepeti](https://github.com/zeisoft/ciceksepeti-mcp) · [Amazon Seller Central](https://github.com/zeisoft/amazon-seller-central-mcp) · [ikas](https://github.com/zeisoft/ikas-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://github.com/zeisoft/stripe-mcp) · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · [RevenueCat](https://github.com/zeisoft/revenuecat-mcp) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Work** — [Jira](https://github.com/zeisoft/jira-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [Trendyol connector page](https://heymetra.com/connectors/trendyol/)
- [Trendyol setup guide](https://heymetra.com/docs/trendyol/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with Trendyol. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>
