---
title: "Fact-Checking Method Applicability Matrix"
properties: []
---

# Method Applicability Matrix

Claim type — methods by layer. Layers activate depending on mode (quick / standard / publication-grade).

## Layer 1. Operational (all modes)

| Type | SIFT | Primary source | Cross-checking | Lateral reading | Fermi estimation | Framing | Quote verification |
|------|------|----------------|----------------|-----------------|------------------|---------|---------------------|
| Figure-simple | ✅ | ✅ | ✅ | — | ✅ quick | ✅ | — |
| Figure-statistical | ✅ | ✅ | ✅ | ✅ | ✅ quick | ✅ | — |
| Status | ✅ | ✅ | ✅ | ✅ | — | — | — |
| Cause | ✅ | ✅ | ✅ | — | — | — | — |
| Forecast | ✅ | ✅ | ✅ | — | ✅ required | — | — |
| Methodology | — | ✅ | ✅ | ✅ | — | — | — |
| Quote | — | ✅ required | — | — | — | — | ✅ required |
| Attribution | ✅ | ✅ | — | — | — | — | — |
| Existence | ✅ | ✅ required | — | — | — | — | — |
| Comparison | ✅ | ✅ | ✅ | — | — | ✅ | — |
| Normative | — | ✅ required | — | — | — | — | — |
| Scientific result | — | ✅ | ✅ | — | — | — | — |
| Own inference | — | — | — | — | — | — | — |

## Layer 2. Statistical (standard and publication-grade modes)

Only for claims with numerical data. Each method has applicability conditions.

| Type | Effect size | GRIM test | Benford's law | Bayes / base rates |
|------|-------------|-----------|---------------|---------------------|
| Figure-simple | — | — | — | — |
| Figure-statistical | ✅ (if significance threshold exists) | ✅ (integer scales, known N) | ✅ (large natural data) | — |
| Forecast | — | — | — | ✅ required |
| Comparison | ✅ | — | — | — |
| Scientific result | ✅ | ✅ | — | ✅ |
| Own inference | — | — | — | ✅ |

Applicability conditions:
- **Effect size** — applicable when there is a quantitative result and a domain significance threshold. Without a threshold — state "not assessed".
- **GRIM test** — only for means from integer scales with known N.
- **Benford's law** — not applicable for IDs, bounded ranges, small samples (< 100).
- **Bayes** — not applicable if base rate is unknown. Do not invent numbers.

## Layer 3. Protective (all modes)

| Type | Anti-hallucination | Anti-sycophancy | Chain-of-Verification (CoVe) |
|------|--------------------|-----------------|------------------------------|
| All types | ✅ | ✅ (when contradicting user's position) | — |
| Own inference | ✅ required | ✅ required | ✅ required |

## Layer 4. Epistemic (publication-grade mode only)

| Type | Popper | Lakatos | Kuhn | Turing |
|------|--------|---------|------|--------|
| Status | — | — | — | ✅ |
| Cause | ✅ | — | — | — |
| Forecast | ✅ | — | — | — |
| Methodology | ✅ | ✅ required | — | ✅ |
| Scientific result | ✅ | ✅ | — | — |
| When sources conflict | ✅ | — | ✅ required | — |

⚠️ Do not apply in quick and standard modes without explicit necessity.

## When to expand the set (feedback loop)

If results diverge at Stage 3 — return to Stage 2 and add:
- Conflicting sources — add Popper (seek refutation of both sides)
- Unconfirmed — add Turing (reformulate verification criterion)
- Factoid / same-source echo — add lateral reading (check the spreader)
