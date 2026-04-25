---
name: competitive-social-listening
description: "For challenger brands running paid ads against an incumbent — listens to what the market says about the COMPETITOR on Reddit, X, and G2, and turns their complaints, switcher threads, feature gaps, and price backlash into wedge hooks, switcher creatives, and audience targeting you can deploy this week."
metadata:
  version: 1.1.0
---

## 1. Purpose

This skill is the **mirror** of [social-listening](social-listening.md) — same three sources (Reddit, X, G2), flipped lens:

|                  | [social-listening](social-listening.md)                          | **competitive-social-listening** (this skill)                         |
| :--------------- | :--------------------------------------------------------------- | :-------------------------------------------------------------------- |
| **Subject**      | **Your** brand                                                   | A **competitor's** brand                                              |
| **Used by**      | The brand itself                                                 | A challenger running ads *against* that competitor                    |
| **Goal**         | Fix / defend your ads                                            | **Attack / exploit** the competitor                                   |
| **Typical move** | Preempt objections, lift praise into your hooks                  | Lift competitor complaints into wedge hooks, target their switchers   |

Every complaint, switcher, feature gap, or price gripe a competitor's customer airs publicly is a wedge you can lift directly into a creative — in the competitor's own customers' language — and target at people shaped like them.

Run **weekly**, or on demand before briefing a competitor‑targeted campaign.

Every run answers two questions:

1. **"What's cracking in the target brand's audience right now?"**
2. **"What should my ads *say* and *who* should they *target* because of it?"**

## 2. Inputs

- **Target brand** — the competitor being listened to (required; **one brand per run**).
- **Subreddits, X handles, G2 page** scoped to the target.
- **Your positioning** (from the platform's BrandKit) — so insights are filtered to wedges *you can credibly defend*, not every complaint uniformly.

## 3. Sources & What to Pull

Same three surfaces as `social-listening`, but every query is scoped to the **target competitor**, not your brand.

| Source     | Pull                                                                                                                   | Competitive value                                                                             |
| :--------- | :--------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------- |
| **Reddit** | Threads mentioning target · *"alternatives to [target]"* posts · 1‑star experiences · complaint threads in key subs    | Switcher threads and complaint posts — often the most candid wedge material.                  |
| **X**      | Target handle mentions · negative replies · *"just switched off [target]"* posts                                       | Speed — catches viral roasts, PR moments, founder gaffes.                                     |
| **G2**     | 1–3 star reviews for target · *"What do you dislike?"* sections · *"Why did you switch?"* answers                      | Structured feature gaps and switcher reasoning — by role and company size.                    |

**Minimum viable run:** ≥ **30 target‑relevant mentions** combined. Under threshold → output *"Insufficient data — broaden subreddit list or re‑run in 14 days."*

## 4. Signal Classification

Each mention gets one label (competitive lens, not your‑brand lens):

| Label                           | Definition                                                              |
| :------------------------------ | :---------------------------------------------------------------------- |
| 😤 **Complaint**                | Explicit frustration with target — friction, bugs, support, onboarding  |
| 🚪 **Switcher**                 | Someone leaving the target for an alternative (you or otherwise)        |
| 🕳 **Gap**                      | Feature/outcome the target doesn't deliver (wish list, feature request) |
| 💸 **Price**                    | Cost complaints — *"too expensive"*, *"not worth it"*, bill shock       |
| 🏆 **Praise (narrow)**          | Specific win for the target — flags what **not** to attack              |
| 🆚 **vs. You / alternatives**   | Target compared to you or another alternative                           |

## 5. Theme Clustering

Group mentions into themes (≥ **3 mentions** = reportable). Per theme:

- **Cluster label** — short phrase (*"setup takes forever"*, *"reporting is too shallow"*)
- **Mix** — % complaint / switcher / gap / price / praise
- **Verbatim quotes** — 3 per theme, one per platform when possible — **each must include full source attribution per §5.1**
- **Volume trend** vs. prior period (↑ / ↓ / flat)
- **Audience signal** — who's complaining (role, company size, industry if inferable from the post/review)

### 5.1 Quote Source Attribution (Required)

**Every verbatim quote in the report MUST be traceable back to its source.** Quotes without sources are unusable: competitive paid ads need verifiable provenance for legal review (avoid defamation, avoid copyrighted lifts) and for sanity‑checking before you spend budget amplifying someone else's actual words.

For each quote, capture:

| Field                  | Required | Example                                                          |
| :--------------------- | :------- | :--------------------------------------------------------------- |
| **Platform**           | ✅       | Reddit · X · G2                                                  |
| **Author handle**      | ✅       | `u/marketingmike` · `@adsec_pro` · *Verified G2 reviewer*        |
| **Permalink**          | ✅       | Direct URL to the comment / post / review                        |
| **Date posted**        | ✅       | `2026-04-18`                                                     |
| **Engagement signal**  | ⚪       | upvotes · likes · star rating                                    |
| **Author context**     | ⚪       | Role / company size / industry if visible (especially on G2)     |

**Render every quote in this exact form:**

> *"…quote text…"* — `@author` · [Platform ↗](permalink) · YYYY‑MM‑DD · engagement *(optional context)*

**Hard rule — if you can't attribute it, drop it:** if a quote's permalink or author cannot be retrieved (deleted post, login‑walled review, paraphrased screenshot), **omit the quote entirely**. Surface the omission count at the bottom of the report as: *"X unattributable quotes filtered."* Never report a quote with `[source unknown]` — that defeats the legal/verification purpose of the requirement.

## 6. Competitive Paid‑Ads Insight Logic

Each pattern maps to a specific competitive move:

| Theme pattern                                                    | Competitive move                                                                                                                                              |
| :--------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **High‑volume Complaint on a specific friction**                 | **Wedge hook** — lift the complaint **verbatim** (*"Still waiting 40s for [Target]'s dashboard?"*). Audience: `Interest: [Target]`.                            |
| **Recurring Switcher pattern** (*"left X because Y"*)            | **Switcher creative** — quote the exit reason. CTA: *"Make the switch."* Audience: lookalike of users engaging with your versus ads.                          |
| **Gap cluster** (repeated feature requests)                      | **"Finally, X can Y"** positioning — attack the gap. Brief via [creative-brief](creative-brief.md) pairing Gap + Direct Problem angles.                       |
| **Price backlash**                                               | **Value/price creative** — contrast pricing or bundle. Only run if your pricing is *actually* competitive — don't bluff.                                       |
| **Narrow Praise**                                                | **Defensive intel** — do *not* attack on this wedge; pivot to complaint/gap themes instead.                                                                   |
| **Comparisons that favor you**                                   | Lean in — the market is already saying it. Quote market language verbatim in the ad (beats brand‑written copy).                                               |
| **Comparisons that favor a third alternative**                   | Watch closely — a rival is eating the wedge you wanted. Escalate to positioning.                                                                              |
| **Complaint sentiment spike ≥ +10pp WoW**                        | 🚀 **Budget moment** — scale competitor‑targeted ads for 7–14 days while the narrative is hot.                                                                |

## 7. Operational Output: Competitive Intel Report

> **Competitive Social Listening — Target: `Competitor` · Week of Apr 20 · 142 target‑relevant mentions (↑31%)**
>
> **Target sentiment distribution**
>
> - 😤 Complaint **34%** (↑6pp) · 🚪 Switcher **12%** (↑3pp) · 🕳 Gap 18% · 💸 Price 9% · 🏆 Praise 19% · 🆚 Comparison 8%
>
> **Per‑source breakdown**
>
> | Source | Mentions | Complaint | Switcher | Gap  | Price | Praise | vs.  |
> | :----- | :------- | :-------- | :------- | :--- | :---- | :----- | :--- |
> | Reddit | 62       | 38%       | 15%      | 21%  | 8%    | 12%    | 6%   |
> | X      | 51       | 41%       | 10%      | 12%  | 12%   | 20%    | 5%   |
> | G2     | 29       | 17%       | 10%      | 24%  | 7%    | 31%    | 11%  |
>
> **Top themes — competitive wedges**
>
> **😤 "Reporting takes forever to load" — 23 mentions (↑)** · 91% Complaint
>
> - *"Waiting 40 seconds every time I pull a campaign report. It's 2026."* — `u/marketingmike` · [Reddit ↗](https://reddit.com/r/PPC/comments/abc123) · 2026‑04‑18 · 212 upvotes
> - *"Competitor's dashboard feels like it's powered by a potato."* — `@adsec_pro` · [X ↗](https://x.com/adsec_pro/status/9876543210) · 2026‑04‑21 · 89 likes
> - *"Their reporting speed is the single biggest reason I'm looking elsewhere."* — *Verified G2 reviewer (Marketing Manager · Mid‑Market)* · [G2 ↗](https://g2.com/products/competitor/reviews/r-7788) · 2026‑04‑15 · 2 stars
>
> → **Move:** **Wedge hook** — lift *"Still waiting 40 seconds for a campaign report?"* as a Direct Problem opener. Target `Interest: Competitor`. 3 variants via [creative-brief](creative-brief.md).
>
> **🚪 "Switched after 12+ months" — 9 mentions** · all Switcher
>
> - *"Cancelled our Competitor contract this quarter — reporting + support finally pushed us out."* — *Verified G2 reviewer (Director of Growth · 50–200 employees)* · [G2 ↗](https://g2.com/products/competitor/reviews/r-7791) · 2026‑04‑20 · 1 star
> - *"I was a Competitor customer for 18 months. Never again."* — `u/saas_skeptic` · [Reddit ↗](https://reddit.com/r/marketing/comments/def456) · 2026‑04‑19 · 47 upvotes
>
> → **Move:** **Switcher creative set** — *"Left [Competitor] this year? Here's what you're missing."* Audience: lookalike 1% of users engaging with your "[Competitor] vs. us" ads.
>
> **🕳 "No server‑side CAPI support" — 7 mentions** · all Gap
>
> - *"Why doesn't Competitor have server‑side conversions in 2026?"* — `u/perfmark_dan` · [Reddit ↗](https://reddit.com/r/PPC/comments/ghi789) · 2026‑04‑16 · 33 upvotes
> - *"If only they'd add CAPI, I'd stay."* — *Verified G2 reviewer (Performance Marketer · SMB)* · [G2 ↗](https://g2.com/products/competitor/reviews/r-7805) · 2026‑04‑22 · 3 stars
>
> → **Move:** **"Finally" hook** — *"Finally, a platform with server‑side CAPI out of the box."* Attack the gap directly.
>
> **💸 "Pricing is getting steep" — 11 mentions** · 78% Price
>
> - *"New Competitor pricing tier is ridiculous for what you get."* — `u/agency_owner_m` · [Reddit ↗](https://reddit.com/r/marketing/comments/jkl012) · 2026‑04‑21 · 167 upvotes
> - *"Paying $500/mo for reports I could pull in Sheets."* — `@growth_lara` · [X ↗](https://x.com/growth_lara/status/9876543299) · 2026‑04‑22 · 54 likes
>
> → **Move:** brief a **price‑positioning creative** — *"Get [feature] without the $500/mo bill."* **Only** run if our pricing is verifiably lower.
>
> **🏆 "Integrations are still the best" — 14 mentions (narrow praise)** · 100% Praise
>
> → **Move:** **do not attack on integrations.** Pivot to speed/pricing/gap wedges instead.
>
> **🆚 "Competitor vs. Us" — 6 mentions** · 67% favor us
>
> - *"We tried both — Adside beat Competitor on reporting speed hands down."* — *Verified G2 reviewer (Head of Performance · Agency)* · [G2 ↗](https://g2.com/products/adside/reviews/r-9012) · 2026‑04‑17 · 5 stars
>
> → **Move:** quote *"beat Competitor on reporting speed"* verbatim in a hook — market language beats brand copy.
>
> **🚀 Spike alert:** Complaint sentiment up **+6pp WoW**, reporting‑speed narrative heating up. Scale competitor‑targeted ads this week while the wedge is hot.
>
> **This week's competitive plays**
>
> 1. **3 wedge creatives** on the reporting‑speed complaint (priority — volume climbing).
> 2. **1 switcher creative set** targeting ex‑Competitor customers via lookalikes.
> 3. **1 gap creative** on server‑side CAPI.
> 4. **Hold** on pricing until our pricing model is verified competitive.
>
> *4 unattributable quotes filtered (deleted comments / login‑walled reviews).*
