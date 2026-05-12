# Method Applicability Matrix

Claim type to minimal and full method set mapping.

## Minimal Set

| Type | ≥2 sources | Lateral Reading | SIFT | Fermi | Turing | Popper | Lakatos | CoVe | Anti-hallucination | Anti-sycophancy | Stat. fact-checking | Bayes | Framing |
|------|-----------|-----------------|------|-------|--------|--------|---------|------|--------------------|----------------|-------------------|-------|---------|
| Figure-simple | ✅ | — | ✅ | ✅ fast | — | — | — | — | — | — | — | — | ✅ |
| Figure-statistics | ✅ | ✅ | ✅ | ✅ | — | — | — | — | — | — | ✅ | — | ✅ |
| Status | ✅ | — | — | — | ✅ mandatory | ✅ | — | — | — | — | — | — | — |
| Cause | ✅ | — | — | — | — | ✅ mandatory | — | — | — | — | — | — | — |
| Forecast | ✅ | — | — | ✅ mandatory | — | ✅ | — | — | — | — | — | ✅ mandatory | — |
| Methodology | — | — | — | — | ✅ mandatory | ✅ | ✅ mandatory | — | — | — | — | — | — |
| Own inference | — | — | — | — | — | — | — | ✅ mandatory | ✅ mandatory | ✅ mandatory | — | ✅ | — |

## Full Set (for publications)

Minimal + additional:
- Fermi — for all types (additional)
- Anti-hallucination — only for "figure-simple", "figure-statistics", "status", "own inference"
- Framing — only for "figure-simple", "figure-statistics", "forecast" (types with numbers)
- Lateral Reading — for all types, if external sources exist

## When to Expand the Set

If results diverge — return to Stage 2 and add:
- Source conflict → add Popper (seek disconfirmation of both sides)
- Unconfirmed → add Turing (reformulate the verification criterion)
- Factoid → add Lateral Reading (verify the propagator)
