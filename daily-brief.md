---
name: daily-brief
description: "Morning ad‑ops briefing that chains am‑i‑on‑track, whats‑running, bleeders‑winners, and fatigue‑detector into a single prioritized digest with a 2‑line executive summary at the top."
metadata:
  version: 1.0.0
---

## 1. Purpose

A single morning read that answers: *"what needs my attention today, in priority order?"* It doesn't re‑implement detection logic — it **orchestrates the skills that already do it**, then synthesizes their output into a ranked digest. Run once per day; it's the entry point into the loop.

## 2. Chain of Skills

Run these in order; keep only the specified items from each output.

| Step | Skill                                     | Keep                                                            |
| :--- | :---------------------------------------- | :-------------------------------------------------------------- |
| 1    | [am-i-on-track](am-i-on-track.md)         | 🔴 Critical and 🟡 Warning pacing alerts only (drop 🟢)         |
| 2    | [whats-running](whats-running.md)         | ⚠️ flagged campaigns only (drop ✅)                             |
| 3    | [bleeders-winners](bleeders-winners.md)   | Top 3 Bleeders + top 3 Winners by spend impact                  |
| 4    | [fatigue-detector](fatigue-detector.md)   | 🔴 Critical entries only (drop 🟡 Warning)                      |

## 3. Ranking & Dedup Rules

- **Section order** by spend‑at‑risk: Pacing → Leaks → Stop/Scale → Fatigue → Winners.
- If the same ad appears in both **Bleeders** and **Fatigue**, keep only the Bleeders entry (stronger signal, explicit action).
- Collapse empty sections — don't render a header with no content.
- Cap the brief at **12 items total** across sections; if more, trim the lowest‑spend items from each section proportionally.

## 4. Executive Summary (top of brief)

A single scannable line. Skip counts that are zero.

> *"[N] campaign(s) [over|under]pacing · [N] leak(s) · [N] to pause, [N] to scale · [N] creative(s) critical."*

## 5. Operational Output: Morning Brief

> **Daily Brief — Mon, Apr 22**
>
> **Summary:** *2 campaigns overpacing · 1 leak · 3 to pause, 2 to scale · 1 creative critical.*
>
> **Pacing (2)**
>
> - 🔴 **Retargeting — Conversions:** projected $580 vs. $450 budget (+29%)
> - 🟡 **Summer Launch — Traffic:** 18% above pace
>
> **Leaks (1)**
>
> - ⚠️ **Q1 Test Campaign** ($50/day) — scheduled to end 3/1, still running
>
> **Stop / Scale (5)**
>
> - 🩸 **3 Bleeders:** `AD_412` · `AD_501` · `AD_733` — see [bleeders-winners](bleeders-winners.md) for copy + action
> - 🏆 **2 Winners:** `AD_388` · `AD_390` — +20% budget suggested (see [budget-shifter](budget-shifter.md) for source)
>
> **Creative Fatigue (1)**
>
> - 🔴 `AD_238` (Notes App Hero) — CTR dropped 34% in 3 days. Pause and queue replacement from [copy-rotation](copy-rotation.md).
