---
title: "Fact-Checking Method Applicability Matrix"
---

# Method Applicability Matrix

Claim type — methods by layers. Layers are activated by mode (quick / standard / publication) and risk gate from `SKILL.md`.

## Layer 1. Operational (all modes)

| Type | SIFT | Primary source | Cross-checking | Lateral reading | Fermi estimate | Framing | Quote verification |
|------|------|----------------|----------------|-----------------|----------------|---------|-------------------|
| Simple figure | ✅ | ✅ | ✅ | — | ✅ quick | ✅ | — |
| Statistics | ✅ | ✅ | ✅ | ✅ | ✅ quick | ✅ | — |
| Status | ✅ quick | ✅ | ✅ | ✅ | — | — | — |
| Causation | ✅ | ✅ | ✅ | ✅ on conflict | — | ✅ | — |
| Prediction | ✅ | ✅ | ✅ | ✅ | ✅ required | ✅ | — |
| Methodology | ✅ | ✅ | ✅ | ✅ | — | ✅ | — |
| Quote | — | ✅ required | — | — | — | — | ✅ required |
| Attribution | ✅ | ✅ | ✅ on dispute | ✅ | — | — | — |
| Existence | ✅ | ✅ required | — | — | — | — | — |
| Comparison | ✅ | ✅ | ✅ | ✅ on conflict | ✅ at scale | ✅ required | — |
| Normative | — | ✅ required | ✅ on versions | — | — | — | — |
| Scientific result | ✅ | ✅ | ✅ | ✅ | ✅ sanity-check | ✅ | — |
| Agent's own conclusion | — | — | — | — | ✅ if numerical | ✅ | — |
| Historical-personal | ✅ | ✅ self-report/archive | ✅ external trace | ✅ | — | — | — |
| Source provenance | ✅ | ✅ required | ✅ archive/registry | ✅ | — | — | ✅ if text document |

## Layer 2. Statistical (standard and publication modes)

Only for claims with numerical data. Each method has applicability conditions.

| Type | Effect size | GRIM test | Benford's law | Bayes / base rates |
|------|-------------|-----------|---------------|-------------------|
| Simple figure | — | — | — | — |
| Statistics | ✅ if significance threshold exists | ✅ integer scales, known N | ✅ large natural data | — |
| Prediction | — | — | — | ✅ if base rate exists |
| Comparison | ✅ | — | — | ✅ if comparing probability |
| Scientific result | ✅ | ✅ if applicable | — | ✅ if probability claimed |
| Agent's own conclusion | — | — | — | ✅ if base rate exists |

Applicability conditions:
- **Effect size** — applicable when there is a quantitative result and a significance threshold for the field. Without a threshold — state "not assessed".
- **GRIM test** — only for means from integer scales with known N.
- **Benford's law** — only for suitable large natural datasets. Deviation is a screening signal, not proof of manipulation.
- **Bayes** — not applicable if base rate is unknown. Do not invent numbers.

## Layer 3. Protective (all modes)

| Type | Anti-hallucination | Anti-sycophancy | Light verification chain |
|------|--------------------|-----------------|--------------------------|
| All types | ✅ | ✅ on discrepancy with user position | — |
| Agent's own conclusion | ✅ required | ✅ required | ✅ required |
| Level E source / snippet / OCR | ✅ required | — | ✅ required |
| Publication material | ✅ required | ✅ required | ✅ minimum for key conclusions |

## Layer 4. Epistemic (rarely, publication mode only)

| Situation | What to do |
|-----------|------------|
| Methodological dispute | Explicitly describe competing presuppositions and evaluation criteria |
| Scientific result without consensus | Show publication status, limitations, alternative explanations |
| Frame conflict, not data conflict | Present positions separately, do not reduce to false consensus |
| Simple fact / date / quote check | Do not apply epistemic frameworks |

⚠️ Do not apply in quick and standard modes without explicit necessity. Do not write "per Popper/Kuhn/Lakatos" if the report contains no concrete result of that operation.

## When to expand the set (refinement cycle)

If results diverge at Stage 3 — return to Stage 2 and add the missing operation:
- Source conflict — check dates, definitions, primary sources, independence, and access level.
- Unconfirmed — formulate an operational criterion; if no criterion exists, mark "unverifiable in this formulation".
- Same-source echo — add lateral reading and search for an independent source.
- Longread — identify only substantive claims and separately check links/dates/screenshots/provenance.
