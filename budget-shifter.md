---
name: budget-shifter
description: "Reallocates budget across campaigns and ad sets based on ROAS and CPA — finds donors (underperformers with budget to spare) and receivers (scalable winners), with guardrails against learning‑phase resets."
metadata:
  version: 1.0.0
---

## 1. Purpose

When a campaign wins, raising its budget in isolation is half the job — the other half is *finding the money* without blowing total account spend. This skill identifies **donors** (underperformers that can shed budget without hurting delivery) and **receivers** (winners with room to scale), then proposes a set of moves with amounts and reasoning.

Two modes:

- **Redistribute** (default): total account spend unchanged; money moves between campaigns.
- **Scale up**: additive — suggest incremental budget for receivers without donor cuts.

## 2. Donor Signals (pull budget from)

A campaign is a **donor** if it hits **any** of these:

| Signal                    | Threshold                                                          |
| :------------------------ | :----------------------------------------------------------------- |
| **Underperforming ROAS**  | ROAS < 0.8× account median (last 14 days)                          |
| **Overshooting CPA**      | CPA > 1.3× target CPA for 7+ days                                  |
| **Fatigued at scale**     | Frequency > 3.5 AND spending > 10% of account daily total          |
| **Underdelivering**       | Spending < 70% of its budget daily for 5+ days — budget is unused  |

## 3. Receiver Signals (send budget to)

A campaign is a **receiver** only if it meets **all** of these:

| Signal                  | Threshold                                                                          |
| :---------------------- | :--------------------------------------------------------------------------------- |
| **ROAS above target**   | ROAS > 1.2× target for 7+ days                                                     |
| **Delivery headroom**   | Daily spend at ≥ 85% of current budget — the campaign is actually using its money  |
| **Audience freshness**  | Frequency < 2.5                                                                    |
| **Past learning phase** | ≥ 50 conversions in trailing 7 days OR ad set out of platform "Learning" status    |

## 4. Move Sizing & Guardrails

| Rule                       | Value                                                                                    |
| :------------------------- | :--------------------------------------------------------------------------------------- |
| **Max single move**        | 20% of the receiver's current daily budget per shift                                     |
| **Donor floor**            | Never cut a donor below the learning threshold (~50 conversions/week/ad set)             |
| **Cooldown**               | Don't shift the same (source, destination) pair twice in < 48 hours                      |
| **Aggregate cap per run**  | Total reallocation ≤ 10% of account daily spend                                          |
| **New‑campaign shield**    | Campaigns < 7 days old are neither donors nor receivers                                  |
| **One‑way donor rule**     | A donor in one run can't become a receiver in the next 48h (avoid churn)                 |

## 5. Operational Output: Budget Shift Proposal

> **Budget Shifts — Mon, Apr 22** · Mode: **Redistribute** · Total moved: **$180/day** (4.5% of $4K account daily spend)
>
> | From → To                                               | Amount   | Why                                                                                                                                   |
> | :------------------------------------------------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------ |
> | **Q1 Test Campaign** → **Retargeting — Conversions**    | $40/day  | Donor: CPA $38 vs. $25 target (7 days). Receiver: ROAS 3.4× (target 2.0×), freq 1.8, past learning.                                  |
> | **Evergreen Prospecting** → **Founder UGC Hook**        | $60/day  | Donor: underdelivering (52% of $120 budget used last 5 days). Receiver: 17 conversions in 7 days, CPA $15.                           |
> | **Spring Sale Carousel** → **Summer Launch — Traffic**  | $80/day  | Donor: fatigued (freq 4.1, CTR 0.8%, spending 14% of account). Receiver: CPC 42% of account avg, freq 2.1, spending 93% of budget.   |
>
> **Action:** apply all 3 in one batch, then re‑check in 48h before the next shift.
