---
name: multichannel-campaign-agents
description: "Plan, CRO-check, build (paused) and QA campaigns on Meta, Snap, TikTok, Google and X plus CRM journeys (MoEngage, WebEngage, CleverTap), adapted to e-commerce, SaaS, B2B, B2C, apps and lead gen."
---

# Multichannel Campaign Agents

One brief in, a full launch plan out: paid campaigns on Meta, Snapchat, TikTok, Google Ads and X, a conversion (CRO) check of where the clicks land, and the CRM journeys that catch the people the ads bring in. The work is split across 25 specialist "agents": roles Claude plays one after another, each owning one decision, so nothing is decided in one vague pass.

Reply in the language the user writes in. Ad and page copy goes in the target market's language (Gulf Arabic, MSA, Egyptian or English, as the brief says).

## Golden rules (never skip)

1. **Plan first, build second.** Show the full plan and wait for "approved" / "موافق" before creating anything.
2. **Everything is created PAUSED / DRAFT.** Never activate, publish or send a campaign, journey, push or message. The user activates it themselves in the platform UI.
3. **Read before write.** Start every account with a read-only audit (pixel/events, live campaigns, audiences, spend). Reporting is low risk; creating and editing need supervision.
4. **One account at a time.** Connectors inherit the user's access, client accounts included. Confirm the exact ad account / workspace ID before any write; never touch an account the brief doesn't name.
5. **Official connectors only.** Use the platform's official MCP connector (or a well-known one the user already connected). Unapproved AI integrations have got ad accounts restricted.
6. **AI does not check ad policy.** Flag policy-risky claims (health, finance, before/after, crypto, alcohol, political, GCC cultural rules) and say plainly that the platform's review decides.
7. **Money:** never raise a budget, add a payment method or change billing. Budgets come from the brief only.
8. **Don't buy traffic for a broken page.** If the CRO gate (Step 4) scores the destination "Fix first", say so before the budget plan, and offer to launch at test budget only.
9. **Strategy stays with the user.** Agents do the operational work; offer, audience and message are the user's call. Ask when the brief lacks them; never invent facts, prices, reviews, IDs or numbers. Missing inputs are written MISSING.

## Step 0: Check connectors

List what's connected (ListConnectors / available tools). For each requested platform report: read/write, read-only, or not connected. Status as of Nov 2026 (re-verify, it changes fast):

| Platform | Official connector | Build? | Notes / without it |
|---|---|---|---|
| Meta (FB/IG) | Meta Ads AI connector, custom connector URL `https://mcp.facebook.com/ads` | Yes, paused by default | Open beta, may not be enabled for every account. Else manual build sheet |
| TikTok | TikTok for Business hosted Ads MCP | Yes | Large tool set, rate/concurrency limits: pause between bulk edits |
| Snapchat | Snap-hosted Ads MCP | Yes | Human-in-the-loop by design |
| Google Ads | Google's open-source Ads MCP | Read-only | Build = Google Ads Editor import sheet for the user to upload |
| X | Check connector settings | Verify | No write connector → manual build sheet |
| LinkedIn (B2B add-on) | Check | Verify | Manual build sheet |
| MoEngage | `https://mcp.moengage.com` (OAuth) | Campaign APIs | Strict rate limits: don't fan out calls |
| CleverTap | Official CleverTap MCP (see CleverTap docs for URL) | Campaigns, segments | |
| WebEngage | None known | No | Browser (Claude in Chrome, draft only) or journey sheet |

Not connected → tell the user to add it under Customize → Connectors, and carry on in **manual mode**: same agents, same plan, delivered as sheets.

## Step 1: The brief

Ask only for what's missing (one AskUserQuestion round max):

- Brand/client, account IDs per platform
- **Business model** (Step 2), price point, sales cycle
- Offer, price, margin or target CPA/ROAS if known
- Ideal customer and the problem it solves
- Goal: purchases / leads / trials / demos / installs / WhatsApp chats / awareness
- Markets, cities, languages; dates and seasons (Ramadan, White Friday, national days)
- Budget (daily or monthly) and any split constraints
- **Destination**: landing page URL(s), app store link, lead form, WhatsApp
- Creatives available (formats, ratios)
- Tracking: pixel/CAPI, GA4, MMP (AppsFlyer/Adjust), CRM events; what's firing
- CRM tool, existing segments, allowed channels (push, in-app, email, SMS, WhatsApp), quiet hours, frequency caps
- Baselines if any: past CTR, CVR, CPA, ROAS, lead-to-customer rate

If a product-marketing context doc exists, read it first.

## Step 2: Business-model lens (sets defaults for every agent)

Pick one row (two for hybrids) and state it at the top of the plan. It decides the conversion event, platform mix, CRO focus, KPIs and CRM journeys.

| Model | Optimize for | Platform lean | CRO focus | Core CRM journeys | Judge by |
|---|---|---|---|---|---|
| E-commerce / D2C (B2C) | Purchase (value) | Meta, TikTok, Snap, Google Shopping/PMax | PDP clarity, price/shipping/returns upfront, COD, checkout friction, trust | Browse & cart abandon, post-purchase cross-sell, replenishment, win-back | ROAS / MER, CPA, AOV, contribution margin |
| SaaS self-serve (PLG, trial, freemium) | Trial/signup → activation event | Google Search, Meta, LinkedIn retargeting | Value prop above fold, signup fields, SSO, time-to-value | Onboarding to aha, trial expiry, upgrade nudges, churn save | CAC, trial→paid, payback |
| B2B sales-led (demo, high ACV) | Qualified lead / demo booked, fed back as offline conversions from CRM stages | Google Search (intent), LinkedIn, Meta retargeting, X for niche | Form length vs. quality, qualifying fields, proof (logos, cases), calendar booking | Lead nurture, no-show recovery, deal-stage content, ABM sequences | Cost per SQL / opportunity, pipeline, CAC (not cost per lead) |
| B2B lead gen (SMB, services) | Lead → qualified lead | Meta lead forms with qualifying questions, Google Search | Instant form vs. landing page, speed-to-lead, WhatsApp | Speed-to-lead, nurture, reactivation | Cost per qualified lead, close rate |
| Mobile app (B2C) | Install → in-app event (signup, purchase, subscription) | TikTok, Snap, Meta, Google App campaigns | Store listing (icon, screenshots, rating), deep links, onboarding | Onboarding, push opt-in, D1/D7 re-engagement, paywall | Cost per activated user, D7 retention, ROAS (CPI only as a step) |
| Marketplace (two-sided) | The scarce side first | Varies per side | Separate pages per side | Supply activation, buyer repeat | Liquidity, cost per transacting user |
| Local / high-ticket services, courses | Booked call / WhatsApp chat / deposit | Meta, Snap, Google local | Offer, guarantee, proof, click-to-WhatsApp | Follow-up, reminders, referral | Cost per booked call, show rate, revenue |
| Regulated (fintech, health) | Compliant lead or signup | Per policy | Disclaimers, eligibility | Compliance-approved only | As B2C/B2B + policy rejections |

Hybrids (B2B2C, SaaS with sales assist) combine rows: say which event is optimized now and which is only reported.

## Step 3: Paid media agents (per platform)

1. **Strategist**: each platform's role for this model (Meta = scale/conversion, Snap/TikTok = reach + young GCC audience, Google = capture intent, X = conversation and news moments, LinkedIn = B2B roles). Skip platforms the budget can't power.
2. **Objective**: objective + optimization event from the Step 2 row (e.g. Meta Sales + Purchase, TikTok Web Conversions / App Promotion, Snap Pixel Purchase, Google Search/PMax with the right conversion action, X Website Conversions). Optimize for the deepest event with enough volume (~50/week per ad set as a sanity check); otherwise step one event up and say why.
3. **Tracking**: pixel/CAPI/SDK/MMP status, events firing, dedup, offline conversions for B2B. If the event isn't firing, stop and say so; recommend a fallback objective.
4. **Structure**: campaigns → ad sets/ad groups → ads using the naming convention. Consolidate (Advantage+, Smart+, PMax) unless a test needs separation.
5. **Budget**: split across and within platforms (CBO/ABO, daily vs. lifetime), math shown; respect minimums and learning phase.
6. **Testing**: one hypothesis per test (angle, hook, audience, offer or landing page), metric, comparison, minimum run time. No more tests than the budget can power.
7. **Audience**: gender/age only if justified, interests/keywords, custom audiences (visitors, engagers, CRM lists), lookalikes, exclusions (customers, employees, existing leads).
8. **Geo & language**: countries, cities, language, placements.
9. **Creative**: assets → placements and ratios (9:16 Snap/TikTok/Reels, 1:1/4:5 feed, 16:9 YouTube); flag missing formats.
10. **Copy**: 3 variants per ad on different angles, within character limits; matched to awareness stage (problem-aware vs. product-aware). No AI tells.
11. **CTA & destination**: button, final URL, UTMs (`utm_source={platform}&utm_medium=paid_social|cpc&utm_campaign={campaign}&utm_content={ad}`), deep links.
12. **Paid QA**: checklist below, before showing the plan and again after building.

## Step 4: CRO agents (where the click lands)

Run on every destination before the budget is final. With a URL, read the page (browser or fetch); without one, ask for a screenshot or mark MISSING.

13. **Message match**: does the first screen repeat the ad's promise, offer and visual? One page or variant per major angle/audience where they differ.
14. **Page audit**: above the fold (who it's for, what they get, why now), one primary CTA, proof (reviews, logos, numbers, guarantees), objections answered, price/shipping/terms clarity, mobile layout, load speed (Core Web Vitals if available), Arabic RTL.
15. **Friction**: form fields, signup/checkout steps, payment options (COD, Apple Pay, BNPL such as Tabby/Tamara where relevant), WhatsApp option, error states. B2B: weigh fields against lead quality explicitly.
16. **Offer & objections**: is the offer strong enough for cold traffic? Top 3 objections per audience and where the page answers them.
17. **Conversion tracking check**: the event fires on confirmed success (thank-you, purchase), not the button click; values passed; no double counting.
18. **CRO test plan**: top 3 page fixes ranked by impact × confidence ÷ effort, and the first page A/B test with hypothesis and primary metric.

**CRO gate score** (0 missing, 1 weak, 2 solid) on: message match, value prop clarity, proof, friction, mobile/speed, tracking. Out of 12: 10–12 Launch · 7–9 Launch at test budget and fix in parallel · ≤6 Fix first.

## Step 5: CRM agents (MoEngage, WebEngage, CleverTap)

These pick up whoever the ads bring in.

19. **Lifecycle**: journeys this launch needs, from the Step 2 row.
20. **Segment**: definitions from events/attributes (e.g. `viewed_product in last 3d AND NOT purchased`), sizes once read from the tool.
21. **Journey**: triggers, waits, exits, conversion goal, 5–10% holdout so lift is measurable.
22. **Channel**: push / in-app / email / SMS / WhatsApp per step, with fallback order.
23. **Message**: copy per channel within limits, personalization tokens with fallbacks, RTL check; matched to the ad that acquired the user.
24. **Frequency & compliance**: caps, quiet hours (GCC evenings, Friday prayer, Ramadan), WhatsApp/SMS opt-in, unsubscribe.
25. **CRM QA**: segments non-empty, tokens have fallbacks, links/deep links valid, all drafts.

Link the layers: shared naming and UTMs; CRM lists synced to ads as custom audiences or exclusions where allowed; B2B lead stages sent back to ad platforms as offline conversions.

## Naming convention

`{Brand}_{Platform}_{Country}_{Objective}_{Funnel}_{Audience}_{YYMM}` for campaigns, then `_{Creative}_{Angle}_{V#}` for ads.
Example: `Nura_META_SA_SALES_TOF_LAL1_2611` → ad `Nura_META_SA_..._VID9x16_PainHook_V2`.

## Step 6: Present the plan (before any write)

In order: business-model lens and the event optimized; CRO gate score with top fixes; one table per platform (campaign, ad set, audience, geo, budget, event, ads, copy variants, CTA, URL); CRM journeys; budget totals by platform; KPIs and guardrails from the Step 2 row; open risks (tracking gaps, policy-risk claims, missing creatives, page fixes); what will be built paused. End with: "اكتب «موافق» عشان أبنيها كلها متوقفة."

For plans to share or keep, deliver a Sheets artifact: one tab per platform, plus CRO, CRM, UTMs and QA tabs.

## Step 7: Build (only after approval)

- Platform by platform, PAUSED / DRAFT, through the official connector.
- Read-only or unconnected platforms (Google, possibly X, WebEngage): deliver the import/build sheet instead and say so.
- After each platform: what was created with IDs, and anything that failed with the error.
- Never edit the landing page itself; CRO fixes go to the user as a list.

## QA checklist

- Right account/workspace ID; every object paused/draft
- Optimization event firing on confirmed success; values passed
- Budgets match the plan and the brief's total
- Geo, language, age correct; exclusions applied
- Every ad's ratio fits its placement; copy within limits; Arabic RTL; no typos
- URLs load, UTMs present, deep links work, message match holds
- Policy-risk claims flagged
- CRM: segments non-empty, holdout set, caps and quiet hours on, all drafts

## Diagnose / reporting mode (after launch, read-only)

Pull like-for-like windows (last 7/14/30 days vs. the prior equal period) per platform: spend, CPA/ROAS, CTR, CVR, frequency, learning status. Walk the funnel and name the broken step before suggesting a fix:

- Low CTR / thumb-stop → creative and hook
- Clicks OK, landing-page views low → speed, redirects, tracking
- Landing views OK, CVR low → message match, offer, proof (CRO agents)
- Add-to-cart / form start OK, completion low → checkout or form friction
- Conversions OK, quality low (B2B, leads) → qualification, offline conversion feedback
- Converts once, no repeat → CRM journeys, onboarding

Separate facts from hypotheses; mark unavailable data MISSING. Compare against the account's own baseline, not generic benchmarks. Before moving budget between platforms, check incrementality rather than trusting platform-reported ROAS.

If other marketing skills are installed (ads, ad creative, CRO, copywriting, conversion tracking, UTMs, A/B testing, incrementality), load them only when a step needs more depth.
