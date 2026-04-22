# LingJi — Auto Insurance AI Demos

Interactive, browser-based demos of the **LingJi** platform — AI-native tools for the motor insurance industry.

> **Live URL:** https://xiang-shan.github.io/lingji-demos/

Two products, one AI layer:

- **LingJi · ZhiLue (灵玑 · 智略)** — Auto Insurance **A+BI Assistant**. Conversational analytics for underwriting and actuarial teams.
- **LingJi · ZhiYu (灵玑 · 智语)** — **Sales Intelligence** / call-centre AI. Real-time scoring, coaching, and proprietary data capture.

A bilingual wrapper slide deck frames both products with problem statement, value thesis, and launch links.

---

## What's in this repo

| File | Demo | Description |
|---|---|---|
| [`index.html`](./index.html) | Landing | Clean English landing page linking to all three demos |
| [`车险全流程智能管理 — 律商联讯风险.html`](./车险全流程智能管理%20—%20律商联讯风险.html) | Wrapper deck | Bilingual slide deck — "Auto Insurance End-to-End Intelligence Management". Arrow-key navigation. |
| [`LingJi-ZhiLue-Auto-Insurance-A+BI-Assistant.html`](./LingJi-ZhiLue-Auto-Insurance-A+BI-Assistant.html) | A+BI | Full A+BI product demo — core KPIs, AI diagnosis, anomaly alerts, findings & actions, **What-If Simulator**, and conversational Q&A. |
| [`LingJi-ZhiYu-Sales-Intelligence.html`](./LingJi-ZhiYu-Sales-Intelligence.html) | ZhiYu | Full ZhiYu product demo — management dashboard, agent capability heatmap, loss analysis, call insights, and **real-time AI assist**. |

---

## LingJi · ZhiLue — A+BI Assistant

**For:** underwriters, actuaries, portfolio managers.

**The problem:** traditional BI dashboards are rigid, backward-looking, and locked to pre-defined views. By the time a custom report answers your question, the business has moved on.

**The idea:** put a large language model *behind* the dashboard — not in front of it. The dashboard still shows numbers (all computed by SQL, not the LLM). The LLM interprets them, surfaces anomalies, generates findings with owners and expected impact, and powers a live What-If Simulator that lets you drag pricing and mix sliders to watch combined ratio recalculate in real time.

**Hero moment:** drag three sliders — taxi uplift, regional expense ratio, scale quality — and watch the book swing from a ¥23.5M underwriting loss to a profit, combined ratio from 107.5% to ~98%.

**Key features shown in the demo:**
- Core KPIs with AI diagnosis (revealing hidden combined ratio, expense ratio, claim frequency)
- Regional performance decomposition (loss-driven vs expense-driven patterns)
- Multi-dimensional risk scan (pricing deviation, NCD effectiveness, vehicle risk, brand risk)
- Anomaly alerts (taxi fleets, corporate policies, NEV brand risk)
- Findings & Actions — each with owner, expected impact, verification metric
- What-If Simulator with transparent arithmetic
- Conversational deep-dive Q&A

---

## LingJi · ZhiYu — Sales Intelligence Platform

**For:** telesales agents, team leads, QA, call-centre directors, cross-functional teams (Claims, Underwriting, Customer Service, Product).

**The problem:** outbound telesales has three structural flaws — quality variance between best and worst agents, churn that takes tacit knowledge with it, and compliance that depends on after-the-fact spot-checks.

**The idea:** score every call, coach in real time, and turn conversations into structured data routed across the organisation. Every call becomes a proprietary customer profile, a competitor-pricing datum, and a market signal — intelligence the insurer owns that platforms and aggregators cannot take.

**Hero moment:** a live call simulation where suggestion, warning, and insight cards slide in mid-conversation — "value-anchor before price", "customer emotion trending negative; pivot to service benefits", "recommend the ¥3,080 + voucher bundle". Coaching in the agent's ear *during* the call, not after.

**Key features shown in the demo:**
- Management dashboard — 299 calls, 70.9 avg score, 30.8% conversion, 85.5% compliance
- Agent capability heatmap — 44-point quality variance between best (Chen Fang, 94) and worst (Liu Yang, 50)
- Data insights — 1,186 customer profiles, 4,888 structured data points, 580 items auto-routed per month
- Loss analysis with 5-dimension root-cause framework (Customer / Agent / Competitor / External / Process)
- Call insights with compliance flagging and emotion arcs
- **Real-time AI assist** — live coaching during the call
- Cross-functional data routing — Claims, Underwriting, Customer Service, Product

---

## Running locally

All three HTMLs are fully self-contained. Clone the repo and open any file in Chrome / Safari / Edge:

```bash
git clone https://github.com/Xiang-Shan/lingji-demos.git
cd lingji-demos
open index.html          # macOS
# or: xdg-open index.html # Linux
# or just double-click in Finder / File Explorer
```

**Recommended:** resolution 1440 × 900 or higher. The A+BI sidebar collapses on narrower windows.

---

## About

These demos are interactive product pitches for the LingJi platform — a China-built, globally-applicable pair of AI tools for the motor insurance market. The underlying thesis: mid-tier insurers everywhere (UK challenger brands, US regional carriers, EU bancassurance mid-tier) are squeezed between oligopolist top-tier competitors and platform-driven customer-data erosion. Software leverage — force-multiplying small analytics teams and building proprietary conversation-layer data — is the structural response.

---

## License

Demos are made available for evaluation and discussion. Contact [@Xiang-Shan](https://github.com/Xiang-Shan) for licensing or deployment enquiries.
