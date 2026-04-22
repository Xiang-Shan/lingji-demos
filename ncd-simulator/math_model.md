# Technical Note: Regional NCD Exemption Scenario Model

## Purpose

This note explains the mathematical structure used in [index.html](./index.html). It is intended to help a non-developer technical reader understand what the simulator is doing, what the key assumptions mean, and how the outputs should be interpreted.

## Model positioning

The simulator is a simplified annual first-order Markov model. It is useful for directional comparison between a base scenario and one or more exemption scenarios, but it is not a rule-exact reproduction of the full China rolling-history NCD framework.

In particular, the current state records only the current NCD level. The real China rule depends on a richer recent-history structure, including continuous insured years and recent claims.

## Regional state space and coefficients

The simulator supports two regional settings because the lower bound differs by region.

### Beijing / Xiamen

Levels:

$$
\{-5,-4,-3,-2,-1,0,1,2,3,4,5\}
$$

Coefficients:

$$
(0.4,0.5,0.6,0.7,0.8,1.0,1.2,1.4,1.6,1.8,2.0)
$$

### Other regions

Levels:

$$
\{-4,-3,-2,-1,0,1,2,3,4,5\}
$$

Coefficients:

$$
(0.5,0.6,0.7,0.8,1.0,1.2,1.4,1.6,1.8,2.0)
$$

The common upper bound is:

$$
5
$$

## Annual transition logic

Let:

- \(L_t\) be the current NCD level
- \(K_t\) be the annual at-fault claim count
- \(A_t\) be the realised exemption count in that policy term
- \(L_{\min}\) be the region-specific lower bound

The base transition is:

$$
L_{t+1}^{\text{base}}=\mathrm{clamp}(L_t-1+K_t,\ L_{\min},\ 5)
$$

The exemption transition is:

$$
L_{t+1}^{\text{ex}}=\mathrm{clamp}(L_t-1+K_t-A_t,\ L_{\min},\ 5)
$$

The term \(-1\) represents the natural one-level improvement associated with one more year of continuous renewal in the simplified model.

## Claim-count model

Annual at-fault claims are modeled as:

$$
K \sim \mathrm{Poisson}(\lambda)
$$

with:

$$
F = E[K] = \lambda
$$

and:

$$
\Pr(K=k)=e^{-F}\frac{F^k}{k!}, \qquad k=0,1,2,\ldots
$$

So if \(F=35\%\), the model uses \(F=0.35\) and therefore \($\lambda=0.35$\).

The probability of at least one at-fault claim is derived, not input directly:

$$
\Pr(K \ge 1)=1-e^{-F}
$$

## Realised exemption model

The page allows a configurable exemption cap \(M\), meaning the maximum number of eligible exemptions within one policy term.

Given total at-fault claims \(K_t=k\), the number of exemption-eligible claims is modeled as:

$$
X_t \mid K_t=k \sim \mathrm{Binomial}(k,e)
$$

where \(e\) is the per-claim exemption trigger probability shown on the page.

The realised exemption count is then:

$$
A_t=\min(X_t,M)
$$

This guarantees two things:

- realised exemptions never exceed the number of actual claims
- realised exemptions never exceed the chosen policy cap \(M\)

When \(M=0\), the exemption scenario collapses to the base scenario. When \(M=1\), the model reduces to the single-exemption-per-term case.

## Transition matrices

The simulator shows three one-step matrices:

### Base matrix

$$
P_{\mathrm{base}}[i,j]
=
\sum_k \Pr(K=k)\cdot \mathbf{1}\{T_{\mathrm{base}}(l_i,k)=l_j\}
$$

### Exemption matrix

$$
P_{\mathrm{ex}}[i,j]
=
\sum_k \Pr(K=k)
\sum_{a=0}^{\min(k,M)}
\Pr(A_t=a \mid K_t=k,M)\cdot \mathbf{1}\{T_{\mathrm{ex}}(l_i,k,a)=l_j\}
$$

### Difference matrix

$$
\Delta P = P_{\mathrm{ex}} - P_{\mathrm{base}}
$$

This makes it easy to see where the exemption increases the chance of remaining in, or returning to, better NCD states.

## Portfolio metrics shown on the page

Let \(\pi_t\) be the distribution vector at round \(t\). Then:

$$
\pi_t=\pi_0\cdot P^t
$$

The average NCD coefficient is:

$$
\bar{C}_t=\sum_l \pi_t(l)\cdot C(l)
$$

The Premium Impact Ratio is:

$$
\text{Premium Impact Ratio}_t=\frac{\bar{C}^{\text{With Exemption}}_t}{\bar{C}^{\text{Base}}_t}
$$

A value below \(100\%\) indicates that the exemption lowers the overall premium-level proxy.

The simulator also shows:

- preferred-tier net vehicle gain, defined as the net change in vehicles at levels \($l \le 0$\)
- the peak improvement round, defined by the maximum value of \($\bar{C}^{\text{Base}}_t-\bar{C}^{\text{With Exemption}}_t$\)

## Numerical implementation notes

To build the one-step matrices efficiently, the simulator enumerates claim counts exactly up to a finite point and then pools the far tail into level \(5\), because sufficiently large claim counts always end at the capped upper bound.

This is an implementation convenience within the capped state space, not a change to the conceptual model above.

## Main assumptions and limitations

- closed renewing portfolio
- no new business inflow
- no lapses or ownership transfers
- state defined by current NCD level only
- China-specific scenario framing and regional lower-bound settings

These assumptions make the tool transparent and easy to discuss, but they also mean the results should be interpreted as comparative scenario output rather than market-exact forecasts.

## Interpretation guidance

For a UK audience, the model is best read as a communication and sensitivity framework:

- Does the exemption preserve better discount states?
- How large is the portfolio effect under plausible assumptions?
- In which renewal rounds is the effect most visible?
- Does the gap later stabilise or narrow?

Those are the right questions for this pack. Exact regulatory replication would require a richer state model than the one implemented here.
