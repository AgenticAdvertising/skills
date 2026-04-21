# Skill: The Fatigue Detector
**Objective:** To detect "Creative Decay" early using consecutive signal tracking, preventing budget waste before ROAS actually crashes.

---

## 1. Fatigue Signals (Hierarchy of Urgency)

1.  **CTR Decay (Most Critical):** Tracking a **20%+ decline** over **3 consecutive days**. This is the first sign of audience "blindness."
2.  **Impression Decline (Auction Priority):** If Impressions drop $>30\%$ while spend stays flat, Meta is deprioritizing the ad because of poor "User Value" (Fatigue).
3.  **Frequency Creep:** Flagging when Frequency exceeds **3.0 - 3.5** (depending on audience size).
4.  **CPC Inflation:** A **15-20%+ increase** in CPC over 3 days (non-seasonal).

## 2. Severity Matrix
| Level | Criteria | AI Action |
| :--- | :--- | :--- |
| **🟡 Warning** | Freq > 3.0 OR 10% CTR Drop | Flag for creative refresh in next 48 hours. |
| **🔴 Critical** | 20%+ CTR Decay (3 days) OR Impression Drop | **Pause Ad** or reduce budget by 50% immediately. |

## 3. The "Reset" Strategy
* **Memory Reset:** If a winner fatigues, log it in `learnings.md` and "rest" it for 2-4 weeks. Re-test once the audience "memory" resets.
* **Lifespan Prediction:** Logs the average days-to-fatigue per creative type (e.g., "Notes App ads last ~10 days; Testimonials last ~21 days").

## 4. Operational Output: The "Daily Briefing"
> **Fatigue Alert:** Ad `AD_ID_238` (**Notes App Hero**) is dying. 
> - **CTR Trend:** 3.2% → 2.8% → 2.1% (🔴 34% drop). 
> - **Frequency:** 3.8. 
> 
> **Action:** Pause `AD_ID_238`. Deploy replacement from 'The Hook Architect' queue (Style: 'Testimonial Variant') to maintain delivery volume.
