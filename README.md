# Campaign Agents

A Claude plugin that turns one campaign brief into a full launch plan: paid campaigns on **Meta, Snapchat, TikTok, Google Ads and X**, a CRO check of the landing page, and the CRM journeys (**MoEngage, WebEngage, CleverTap**) that follow up with the people the ads bring in. It adapts to e-commerce, SaaS, B2B, B2C, apps and lead gen.

## Safety rules built in

- Plan first; nothing is built until you approve.
- Everything is created **paused / draft**. You activate it yourself.
- Read-only audit of each account before any write, one account at a time.
- Never touches budgets beyond the brief, billing or payment methods.
- Missing inputs are marked `MISSING`, never guessed.

## What it can build today

| Platform | With its official connector | Without it |
|---|---|---|
| Meta (Facebook, Instagram) | Builds campaigns, paused (Meta Ads MCP, open beta) | Build sheet |
| TikTok | Builds campaigns, paused (TikTok for Business connector) | Build sheet |
| Snapchat | Reads data only (Snap's connector is read-only for now) | Build sheet |
| Google Ads | Reads data only (Google's MCP is read-only) | Google Ads Editor import sheet |
| X, LinkedIn | — | Build sheet |
| MoEngage | Builds campaigns and segments as drafts | Journey sheet |
| CleverTap | Campaigns and segments via its MCP | Journey sheet |
| WebEngage | — | Journey sheet |

No connectors at all? It still runs the full plan in manual mode and hands you the sheets.

## Install

In Claude Code:

```
/plugin marketplace add islamagendi-hue/campaign-agents
/plugin install campaign-agents@campaign-agents
```

In the Claude app (chat or Cowork): open the Plugins settings, add a marketplace from a GitHub repository, enter `islamagendi-hue/campaign-agents`, then install **campaign-agents**.

## Use

Ask Claude to plan a campaign and give it a brief: brand, offer and price, ideal customer, goal, markets and language, budget, platforms, CRM and allowed channels, destination URL, existing creative, tracking setup and dates. It works with the platforms' official MCP connectors when they are connected, or in manual mode, delivering build sheets (including a Google Ads Editor import tab).

## License

MIT
