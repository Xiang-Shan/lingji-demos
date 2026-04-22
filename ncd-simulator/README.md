# China Commercial Auto Insurance NCD Exemption Scenario Simulator

This package is an offline, English-language scenario simulator for discussing how an NCD exemption in intelligent-driving contexts could affect portfolio mix and premium level over time in the China commercial motor market.

It is designed for directional scenario analysis and management discussion. It is not a pricing engine, not a policy-administration tool, and not a formal interpretation of the underlying rule set.

## Why this matters

For a UK management audience, the value of this simulator is not the exact China-specific rule detail on its own. The value is that it provides a transparent way to discuss:

- how an NCD exemption can change the distribution of policyholders across discount states
- how that shift can flow through to an average premium-level proxy
- how sensitive the result is to claim frequency, exemption eligibility, and regional rule settings
- how a market may communicate and test insurance design choices for emerging ADAS and intelligent-driving risks

## China market and regulatory background

The simulator sits against a live policy backdrop in China. In March 2026, the Beijing branch of China’s financial regulator announced the launch of development and application work for dedicated commercial insurance products for intelligent connected new-energy vehicles, a.k.a. `Atonomous Vehicles`.

At a high level, the regulator’s message was:

- dedicated products are being developed because current motor products do not fully match intelligent-driving use cases and related software or hardware loss scenarios
- the existing motor insurance framework is intentionally being retained
- the reasons include legal consistency, efficient compensation for road-traffic victims, and the practical ability for insurers to settle first and then pursue recovery where defects or product liabilities exist
- rollout is phased and initially narrow, with early focus on a Beijing-led pilot context and eligible intelligent connected NEVs
- “intelligent-driving insurance” does not remove driver responsibility; it is not a substitute for legal driving responsibility

This should be read as market and regulatory context only. The simulator itself is a simplified analytical model rather than an implementation of any formal regulatory engine.

## What the simulator shows

The simulator compares a base scenario with one or more exemption scenarios and shows:

- regional NCD migration under the selected lower-bound rule
- one-step transition matrices for the base and exemption scenarios
- the difference matrix between those two transition structures
- the average NCD coefficient path across renewal rounds
- the Premium Impact Ratio as a premium-level proxy
- the round at which the exemption effect is strongest under the current assumptions

## What it does not do

The simulator should not be read as:

- a production pricing model
- a policy-administration engine
- an exact replication of the full rolling-history China NCD rule
- a regulatory, accounting, or reserving calculation

It is best used as a transparent scenario tool for discussing direction, magnitude, and sensitivity.

## How to open

Open [index.html](./index.html) locally in a browser. The package is fully static and does not require a backend service or any external CDN.

[simulation.html](./simulation.html) is included as a compatibility alias and simply redirects to the main page.

## Package contents

- [README.md](./README.md): executive overview and usage guidance
- [index.html](./index.html): main interactive simulator
- [simulation.html](./simulation.html): compatibility redirect to the main page
- [math_model.md](./math_model.md): technical companion note for the current model
- [vendor-mathjax](./vendor-mathjax): local MathJax runtime for offline formula rendering

## Reading guidance

The most useful management readout is usually the Premium Impact Ratio together with the average NCD coefficient path and the transition-matrix differences. Those outputs make it easier to see whether an exemption primarily preserves better discount states, how quickly the effect appears, and whether the gap later narrows as the portfolio approaches a longer-run distribution.

The model remains deliberately simplified. That is a strength for communication and sensitivity testing, but a limitation for any attempt to treat the output as a rule-exact market view.
