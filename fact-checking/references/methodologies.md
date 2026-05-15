---
title: "Fact-Checking Methodologies: Sources and Descriptions"
---

# Fact-Checking Methodologies: Sources and Descriptions

Detailed descriptions of methods referenced by SKILL.md. Philosophical context (Turing, Popper, Lakatos, Kuhn) — in `fact-checking-theory.md`.

## SIFT (Mike Caulfield, 2019)

Four steps for rapid information assessment. Developed by Caulfield (at time of publication — Washington State University Vancouver, now — UW Bothell).

1. **Stop** — do not react emotionally
2. **Investigate the source** — who is behind the information?
3. **Find better coverage** — find better coverage in authoritative sources
4. **Trace to the original** — trace to the primary source

Resource: https://hapgood.us/2019/06/19/sift-the-four-moves/

## Lateral Reading (Wineburg & McGrew, Stanford, 2017)

Fact-checkers do not read a page "in depth" but go "sideways" — search for information about the resource itself. Study: 45 participants (10 fact-checkers, 10 historians, 25 students). Fact-checkers worked faster and more accurately than all others.

Study: "Lateral Reading and the Nature of Expertise: Reading Less and Learning More", Stanford History Education Group, 2017. SSRN: 3048994.

Caulfield and Wineburg are co-authors of the book "Verified" (University of Chicago Press).

## IFCN Code of Principles (Poynter Institute)

International fact-checking standard. 31 criteria, 5 principles:

1. Non-partisanship and Fairness
2. Transparency of Sources
3. Transparency of Organization & Funding
4. Transparency of Methodology
5. Open & Honest Corrections

Resource: https://ifcncodeofprinciples.poynter.org/

## Calling Bullshit (Bergstrom and West, 2020)

Course and book (University of Washington). Key concepts: Brandolini's law (energy to refute >> energy to create bullshit), Fermi estimation, GRIM test, Benford's law, effect size, visual manipulations (truncated axes, proportional ink violations).

Resource: https://www.callingbullshit.org/

## Statistical fact-checking

Methods for verifying numerical data, popularized by Bergstrom and West (Calling Bullshit, 2020):

- **Effect size** — is the result clinically meaningful? Statistical significance (p < 0.05) does not mean practical significance.
- **GRIM test** — consistency check: do the mean, N, and proportions converge? If mean is 4.3 with N=7 — must yield an integer × N / N.
- **Benford's law** — distribution of leading digits in suitable natural data: 1 appears about 30% of the time, 9 — about 5%. Deviation is only a screening signal when applicability conditions are met; by itself does not prove manipulation.

**Algorithm on deviation:**
1. Check applicability conditions (N > 100, natural data, not IDs, not bounded range). If conditions are not met, the signal is false — stop.
2. If conditions are met, check alternative explanations: small sample, psychological rounding, narrow range, threshold values.
3. If alternatives do not explain, mark in report: "leading digit distribution deviates from Benford's law. Possible cause: [options]. Not proof of manipulation."
4. Do not write "data fabricated" based on Benford's alone without additional evidence.

## Anti-sycophancy

A method for detecting agreement with the user contrary to facts. Differs from anti-hallucination: hallucination — the agent fabricated a fact, sycophancy — the agent found a fact but agreed with the user instead of challenging them.

Method: formulate the user's position, find facts against that position via search, compare. If facts contradict — explicitly indicate the discrepancy, do not adjust the conclusion.

## CoVe — Chain-of-Verification (Meta AI, 2023)

AI-specific technique for reducing hallucinations:

1. Draft response — draft answer
2. Plan verification questions — verification questions for the draft
3. Answer independently — answer questions without draft context
4. Generate verified response — verified answer

Study: Dhuliawala et al., "Chain-of-Verification Reduces Hallucination in Large Language Models", arXiv:2309.11495, 2023.

## Baloney Detection Kit (Carl Sagan, 1995)

Chapter "The Fine Art of Baloney Detection" from the book "The Demon-Haunted World" (first edition — 1995, Random House). Tool kit: independent confirmation, multiple hypotheses, Occam's razor, quantitative estimates, checking every link in the argument.

## Critical Thinking (Tom Chatfield, Oxford)

Anchoring, framing, Bayes' theorem, base rate fallacy. Separate formulation from substance.

## Anatomy of Delusions (Nikita Nepryakhin, Alpina)

Presentation form ≠ content. Cognitive biases, logic, argumentation.

## KlemGU Algorithm (Komleva and Solomin, 2022)

Unified fact-checking algorithm for online media journalists. Checks: proper names, sources, quotes, details, visual elements.

Source: Komleva V.Yu., Solomin V.E., "Virtual Communication and Social Networks", 2022, 1(4): 167-171.

---

## v6 Additions

The following methods and principles were introduced in v6.0+ of the skill and are documented here for completeness.

### Primary-source-first principle

Prefer primary sources over secondary retellings. ArXiv paper — the article itself, not a blog summary. GitHub repo — the repository itself, not a news item about it. Law or standard — the official text.

Two retellings do not make a fact more reliable if both cite the same primary source. See also "Same-source echo" below.

### Source hierarchy and access level

For production fact-checking, a single "primary / secondary" division is insufficient. Record two dimensions.

**Source level (standard and publication modes only):**

- **A. Official machine-verifiable source** — registry, law, standard, DOI, WHOIS, API, database record.
- **B. Original document or scan with provenance** — order, letter, photograph, archival copy with clear origin.
- **C. Author's self-report** — participant/organization reports about itself; confirms the fact of the statement, but not always the external fact.
- **D. Independent secondary source** — media, research, catalog, directory without a common primary source and conflict of interest.
- **E. Same-source echo / quote aggregator / search snippet** — does not count as independent confirmation.
- **internal** — internal source (transcript, memo, knowledge file, issue). Primary for the fact "participant X reported Y". Not independent for an external fact.

In quick mode, do not require A–E hierarchy — "confirmed / unconfirmed" is sufficient.

**Access level (standard and publication modes only):** full text open / metadata open / search snippet / image or OCR / unavailable.

If only a snippet or OCR was used, this must be explicitly stated in the report: the agent must not pass such a source as a fully verified original.

### Source independence and echo

Before counting "confirmed by 2+ sources" check whether there is a common primary source:

- **Primary source confirmation** — fact confirmed directly by the primary source.
- **Independent confirmation** — two sources confirm independently, without a common basis.
- **Same-source echo** — multiple sources retell the same original. Does not count as independent confirmation.

Also check for conflict of interest: does the source report the fact itself or quote someone else?

### Literal, rhetorical, and artistic

Before checking a contested phrase, determine its usage mode:

- quote — check source, verbatim accuracy, and attribution;
- artistic image / metaphor / joke — do not check as fact unless the user requests literal verification;
- literal claim — formulate an operational criterion and check as a regular claim.

This gate prevents false fact-checking of artistic phrases and slogans.

### Article / Longread Workflow

For a long article, identify 5–10 substantive claims, not all details. Be sure to check:

1. links and broken URLs;
2. publication/update dates;
3. quotes and attributions;
4. numbers, comparisons, and "first/only/largest";
5. screenshots, images, and provenance;
6. personal recollections as self-report if no external trace exists;
7. internal project sources: primary for the author's statement, but not independent for an external fact.

### Quote verification

Open the original document, compare verbatim. Check context: is the quote taken out of context? Is the attribution correct? Does the surrounding text change the meaning?

Applicable to the "quote" type — required in all modes.

### Scientific and technical claim verification

A separate procedure for scientific/technical claims:

1. Check publication metadata (authors, date, journal)
2. Compare abstract with claim formulation
3. Check tables/appendices for specific numbers
4. Check code and data availability
5. Check peer review status
6. Check confidence intervals
7. Distinguish direct measurement from model-based estimate

### Light Chain-of-Verification

Full CoVe is heavy for quick responses. Minimal production variant: for your own conclusion, formulate one question whose answer could change the verdict, check it separately, and correct the conclusion if they diverge. Reserve full CoVe for publication mode.

### False rigor rule

Do not name a method if you did not apply it specifically and cannot state the result.

Bad: "Using Popperian falsification, the claim is plausible."
Good: "Search for refuting data: X, Y. Found Z, which weakens the claim."

### Verdict "unverifiable in this formulation"

Use when a claim is too vague, evaluative, metaphorical, or does not provide a verification criterion. This is better than "unconfirmed" because it does not create the false impression that there was a fact and it failed verification.

Examples: "the best approach", "an amazing result", "no river in the world can compare" without specified comparison criteria.

### Uncertainty, confidence, and caveats

For each verdict indicate:
- **Confidence level** — high / medium / low
- **Source level** — A/B/C/D/E or primary / secondary / indirect / absent
- **Access level** — full text / metadata / snippet / OCR / unavailable
- **Caveats** — what could change the verdict
- **Not checked** — what was not verified

### Report template (standard and publication modes)

1. **Brief verdict** — 1–3 sentences: what was checked, overall result.
2. **Claim verification** — for each: exact formulation, interpretation, type, verification criterion, verdict, evidence, source level, access level, dates, caveats, confidence level.
3. **Key issues** — exaggerations, missing context, unconfirmed assumptions.
4. **Suggested correction** — reformulated claims accounting for verification results.
