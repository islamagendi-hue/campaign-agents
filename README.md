# Campaign Agents

A Claude plugin that turns one campaign brief into a full launch plan: paid campaigns on **Meta, Snapchat, TikTok, Google Ads and X**, a CRO check of the landing page, and the CRM journeys (**MoEngage, WebEngage, CleverTap**) that follow up with the people the ads bring in. It adapts to e-commerce, SaaS, B2B, B2C, apps and lead gen.

## Safety rules built in

- Plan first; nothing is built until you approve.
- Everything is created **paused / draft**. You activate it yourself.
- Read-only audit of each account before any write, one account at a time.
- Never touches budgets beyond the brief, billing or payment methods.
- Missing inputs are marked `MISSING`, never guessed.

## Install

In Claude Code:

```
/plugin marketplace add islamagendi-hue/campaign-agents
/plugin install campaign-agents@campaign-agents
```

In the Claude app, add this repo as a plugin marketplace from the plugins settings, then install **campaign-agents**.

## Use

Ask Claude to plan a campaign and give it a brief: brand, offer and price, ideal customer, goal, markets and language, budget, platforms, CRM and allowed channels, destination URL, existing creative, tracking setup and dates. It works with the platforms' official MCP connectors when they are connected, or in manual mode, delivering build sheets (including a Google Ads Editor import tab).

## License

MIT
