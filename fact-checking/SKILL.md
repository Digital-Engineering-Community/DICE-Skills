---
title: "Fact-Checking: Identification, Method Selection, Verification"
description: "Search, verify, and analyze information. Identify claim types, select methods by mode, verify, classify. Apply to all verification and fact-checking tasks."
name: fact-checking
version: 6.0.1
author: Digital Engineering Community
license: Apache-2.0
properties: []
---

**Use when** verifying factual claims, source reliability, quoted numbers, research claims, or publication-ready analytical text.

## REGULATION

**Stage 1. Identification:** Formulate the main claim, break into atomic claims, classify by type, determine mode (quick / standard / publication-grade) based on types, assess significance. See "Stage 1".
**Stage 2. Method selection:** Match claim type to method set by layer. See "Stage 2".
**Stage 3. Verification:** Execute methods through two search channels, prefer primary sources, verify independence. See "Stage 3".
**Stage 4. Classification:** Assign a verdict (supported / partially supported / unsupported / conflicting / refuted / misleading), state confidence level and caveats. See "Stage 4".
**Stage 5. Synthesis:** Compile report using the template. See "Stage 5".

**Rules:** 1) Never generate numbers — only from sources. 2) Check source dates — flag outdated ones. 3) Scan for sycophancy — do not agree with the user without verification. 4) Fact-check your own claims before publication. 5) Red flag — STOP and report to operator. 6) Do not apply statistical methods without checking applicability conditions. 7) Do not name a method without a concrete result. 8) If base rate is unknown — state it, do not invent one.
**Exceptions:** 1) No sources available — record "unsupported", do not guess. 2) Contradiction in knowledge — pass to `research` skill.

## Stage 1. Identification

### 1.1. Main claim

Formulate the main claim of the text being checked. Examples for different materials:
- Skill — "the method set is sufficient for the task"
- Post — "the argument proves the conclusion"
- Report — "conclusions follow from data"
- Analytical brief — "assessment is supported by data"
- Presentation — "key thesis is confirmed"

If the material does not fit examples — formulate the main claim in your own words: what main idea are we checking.

Check the main claim using Popper's method: formulate 2–3 specific conditions under which the main claim would be false. For each condition, search for supporting data. If at least one disconfirming condition is confirmed — the main claim fails.

**When to apply:** use when the material has a clear argumentative structure (report, analytical brief, post with thesis) or when the stakes are high enough that a false main claim would mislead. Skip for simple lookup tasks (e.g., "does this standard exist?").

If the main claim is not confirmed — do not stop blindly. Narrow the scope: continue checking claims that explain why the main claim failed, or prevent misleading overcorrection.

### 1.2. Atomic claims

Break the text into minimal verifiable units. One claim = one check.

Example: "Kriogenmash is a major player, revenue 8.6 billion, growth 48%" — 3 claims: (1) major player [status], (2) revenue 8.6 billion [figure-simple], (3) growth 48% [figure-simple].

Opinions ("seems", "probably", "feels like") — discard, not subject to fact-checking.

### 1.3. Claim types

Determine the type of each claim. Methods by type — see [references/applicability-matrix.md](references/applicability-matrix.md).

**Figure-simple** — specific number, date, name, title without statistical context. Example: "revenue 8.6 billion", "founded in 2005". Methods: SIFT, primary source, cross-checking, framing.

**Figure-statistical** — averages, percentages, p-values, confidence intervals, sample sizes. Example: "average height 175 cm with N=200", "accuracy 97%". Methods: SIFT, primary source, cross-checking, lateral reading + GRIM, effect size, Benford's law (by applicability conditions).

**Status** — statement about the state of affairs. Example: "term is established", "standard is adopted". Methods: SIFT, lateral reading, cross-checking.

**Cause** — causal relationship. Example: "sanctions led to a 40% price increase". Methods: SIFT, cross-checking.

**Forecast** — statement about the future or an estimate. Example: "market will grow 3x". Methods: SIFT, Fermi estimation, Bayes / base rates.

**Methodology** — assessment of an approach's reliability, method, or school. Example: "SIFT is the fact-checking standard in journalism". Methods: lateral reading, cross-checking.

**Quote** — accuracy of citation. Example: "Einstein said: 'Imagination is more important than knowledge'" — verify whether he actually said it and where it first appeared. Methods: quote verification, primary source.

**Attribution** — who owns a claim, idea, or product. Example: "PDCA was proposed by Deming". Methods: SIFT, primary source.

**Existence** — does an object exist. Example: "there is GOST R 57700.37". Methods: SIFT, primary source.

**Comparison** — "better/bigger/first/only". Example: "Russia is the leader in gas reserves". Methods: SIFT, cross-checking, framing.

**Normative** — reference to a law, standard, regulation. Example: "according to ISO 9001:2015, clause 4.1". Methods: primary source (text of the law/standard).

**Scientific result** — statement about research results. Example: "method shows 97% accuracy on MNIST dataset". Methods: research paper workflow (Stage 3).

**Own inference** — claim generated by the agent. Example: "probably the reason is staff shortage". Methods: chain-of-verification (CoVe), anti-hallucination, anti-sycophancy.

### 1.4. Mode

Determine the mode based on claim types:

- **Quick** — all claims are "figure-simple", "existence", "attribution", "status". Apply operational methods and protective mechanisms. Verify via primary source + sanity check, deliver verdict in 1–3 sentences. Stages 2–4 abbreviated, Stage 5 — no detailed report. Status claims qualify for quick mode only when verifiable through a single primary source.
- **Standard** — claims include "figure-statistical", "cause", "forecast", "status", "comparison", "quote", "normative". Apply operational, statistical, and protective methods. Compile a full report using template (Stage 5).
- **Publication-grade** — material intended for channel, article, conference, or includes "methodology", "scientific result" types. Apply all method layers, including epistemic frameworks. Compile a full report using template.

### 1.5. Significance

Assess whether the claim affects the argument's conclusion. A claim that is the foundation of the argument — verify with high priority. A claim that does not affect the conclusion — low priority.

**Stage 1 completion criteria:** main claim formulated and checked, each claim classified by type, mode determined by types, opinions discarded, significance assessed.

## Stage 2. Method selection

Methods are divided into four layers. Layer selection depends on mode and claim type. Detailed description of each method — in [references/methodologies.md](references/methodologies.md). "Type × method × layer" matrix — in [references/applicability-matrix.md](references/applicability-matrix.md).

**Feedback loop:** if results diverge at Stage 3 — return to Stage 2 and add:
- Conflicting sources — add Popper (falsificationism)
- Unconfirmed — add Turing (operational criterion)
- Factoid / same-source echo — add lateral reading

### Layer 1. Operational methods (all modes)

**SIFT (Caulfield, 2019).** Stop, investigate the source, find better coverage, trace to the original.

**Lateral reading (Wineburg & McGrew, 2017).** Check the source from the outside: who is behind the site, what others say, any conflict of interest. Do not trust the "About us" page.

**Primary source.** Prefer primary sources. Secondary independent — when primary is unavailable, conflicts, or interpretation rather than raw fact is being checked.

**Cross-checking.** If sources diverge — find a third, independent source.

**Fermi estimation.** Estimate the order of magnitude before searching. "10 billion users" — impossible. Named after Enrico Fermi, popularized by Bergstrom and West (Calling Bullshit, 2020).

**Framing.** "90% survival rate" vs "10% mortality" — the same number. Check the formulation, not just the number.

**Quote verification.** Open the original, compare verbatim. Check context: is the quote taken out of context?

### Layer 2. Statistical methods (standard and publication-grade modes)

Apply **only** to claims with numerical data. Each method has applicability conditions — do not apply blindly.

**Effect size.** Statistical significance (p-value) does not mean practical significance. A 0.1% difference can be statistically significant at N=100000 but meaningless in practice. Check: is the difference large enough to have practical consequences?
- Applicable: when there is a quantitative result and practical significance can be assessed.
- Not applicable: when there is no significance threshold for the domain.
- What to do: state that practical significance was not assessed.

**GRIM test.** Checks internal consistency: if a mean is reported for N respondents, the product of mean × N should yield an integer (if the scale is integer). If it doesn't — the mean was likely computed incorrectly or fabricated.
- Applicable: only for means from integer scales with known N.
- Not applicable: for non-integer scales, unknown N, percentages without a stated base.

**Benford's law.** In natural numerical data (populations, budgets, areas) the first digit is distributed unevenly: 1 occurs in ~30% of cases, 9 — in ~5%. If the distribution of first digits in a dataset deviates strongly from this law — fabrication is possible.
- Applicable: for natural numerical data at large scale (populations, budgets).
- Not applicable: for IDs, bounded ranges, psychologically rounded prices, small samples (< 100).

**Bayes / base rates.** For forecasts: what is the base probability from past forecasts of a similar type? A positive test for a rare event does not mean high probability. Example: "market will grow 3x" — if 1 out of 10 past 3x growth forecasts came true, base probability is 10%. An authoritative source does not mean confirmation.
- Applicable: when base rate data is available.
- Not applicable: when base rate is unknown — do not invent numbers. State: "base rate unknown, forecast is unreliable".

### Layer 3. Protective mechanisms (all modes)

**Anti-hallucination.** Check: (1) the source exists — find via search, do not trust model memory, (2) the quote is accurate — open the original, (3) the number is from the original — check context.

**Anti-sycophancy.** Formulate the user's position, find facts against it, compare. If facts contradict — explicitly state the discrepancy.

**Chain-of-Verification — CoVe (Meta AI, 2023).** For agent's own inferences: (1) formulate a verification question, (2) answer independently, (3) compare, (4) correct if divergent.

### Layer 4. Epistemic frameworks (publication-grade mode only)

**Popper (falsificationism).** For each claim, formulate: what would have to be true for the claim to be false? Search for data confirming this "disconfirming condition". Example: claim "X grew thanks to reform Y" — disconfirming condition: "X grew at the same rate before reform Y". If found — claim is unsupported.

**Lakatos (research programmes).** When theories conflict, assess: does one side predict new, previously unknown facts (progressive programme), while the other retrofits explanations post hoc (degenerative programme). Example: "the company explains every failure as force majeure" — degenerative programme.

**Kuhn (paradigms).** When sources conflict — present both positions as different coordinate systems, do not reduce to a common denominator. Result: for each position state (1) what premise it accepts, (2) what facts it explains, (3) what it cannot explain.

**Turing (operational criterion).** If a claim cannot be verified through an observable result — it is an opinion, not a fact. Formulate a concrete criterion: what exactly you are checking and what result would confirm or refute it. Example: "the term is established" — criterion: there is a Wikipedia article, academic publications, a generally accepted definition. Cannot formulate a criterion — it is an opinion.

⚠️ **Do not apply epistemic frameworks to simple checks.** They are appropriate only when verifying scientific and methodological claims where an unambiguous answer is impossible without a position in a scientific debate.

**Stage 2 completion criteria:** for each claim a method set is selected according to mode and type, selection is justified.

## Stage 3. Verification

### Source search

Formulate a search query and execute through **two search channels**:

1. **Regional channel** — local-language sources, national regulations, companies, standards.
2. **International channel** — international sources in all languages. Default to English, additionally adapt to the language of the expected source (Chinese, Arabic, Japanese, etc.).

Fetch/extract source content using available web or browser tools.

If the task goes beyond fact-checking (complex research, comparative analysis, synthesis from multiple sources) — pass to the `research` skill.

### Primary-source-first principle

Prefer primary sources: arXiv paper — the paper itself, GitHub repo — the repo itself, API docs — official documentation, law/standard — the text of the law/standard. Two retellings do not make a fact more reliable if both cite the same primary source.

### Source independence check

Before counting "confirmed by 2+ sources" check: is there a common primary source? Independent confirmation or reprint? Any conflict of interest? Does the source report the fact itself or cite someone else?

Distinguish:
- **Primary-source confirmation** — fact confirmed by the primary source.
- **Independent corroboration** — two independent sources confirm.
- **Same-source echo** — multiple sources retell the same source — does not count as independent confirmation.

### Scientific and technical claim verification

For scientific and technical claims — separate workflow: (1) check paper metadata (authors, date, journal), (2) compare abstract with the claim formulation, (3) check tables/appendix for specific numbers, (4) check code and data availability, (5) check peer review status, (6) check confidence intervals, (7) distinguish direct measurement from model-derived estimate.

### False rigor rule

**Do not name a method if you have not applied it concretely and cannot state the result.**

Bad: "Using Popperian falsification, the claim is plausible."
Good: "Search for disconfirming evidence: X, Y. Found Z, which weakens the claim."

**Stage 3 completion criteria:** each claim verified by selected methods, sources cited with dates, hallucinations identified and corrected.

## Stage 4. Classification

### Verdicts

Assign one verdict to each claim:

- **Supported** (✅) — confirmed by a reliable primary source or independent sources
- **Partially supported** (⚠️) — correct in essence, but with caveats: inaccurate numbers, different context, missing conditions
- **Unsupported** (❓) — insufficient data to confirm or refute
- **Conflicting** (🔴) — sources diverge
- **Refuted** (❌) — demonstrably false
- **Misleading** (⛔) — not technically false, but distorts: cherry-picking, false framing, taken out of context

### Uncertainty

For each verdict state: **Confidence level** (high / medium / low), **Evidence quality** (primary / secondary / indirect / absent), **Caveats** (what could change the verdict), **Not checked** (what was not verified).

Cite sources with publication dates.

**Stage 4 completion criteria:** all claims classified with verdict, confidence level, and sources with dates.

## Stage 5. Synthesis

### Quick mode

Deliver verdict in 1–3 sentences with source.

### Standard and publication-grade modes

Compile report using the template:

**Summary verdict** — 1–3 sentences: what was checked, overall result.

**Claim checks** — for each: claim, verdict, evidence, sources with dates, caveats, confidence level.

**Material issues** — overstatements (what is exaggerated), missing context (what context is omitted), unsupported assumptions (what assumptions are unconfirmed).

**Suggested correction** — reformulated claims incorporating verification results.

When sources conflict — present both positions, do not reduce to a common denominator. Apply Lakatos assessment only in publication-grade mode when the conflict is between competing methodological frameworks, not between data points.

**Stage 5 completion criteria:** gaps noted, conflicts not smoothed over, result compiled per template.

## References

- `references/methodologies.md` — detailed description of each method
- `references/applicability-matrix.md` — "claim type × method × layer" matrix
- `references/fact-checking-theory.md` — philosophical context: Turing, Popper, Lakatos, Kuhn
