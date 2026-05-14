# Fact-Checking Methodologies: Sources and Descriptions

Detailed descriptions of methods referenced in SKILL.md. Philosophical context (Turing, Popper, Lakatos, Kuhn) — in `fact-checking-theory.md`.

## SIFT (Mike Caulfield, 2019)

Four steps for rapid information assessment. Developed by Caulfield (Washington State University Vancouver at the time of publication, now UW Bothell).

1. **Stop** — pause, do not react emotionally
2. **Investigate the source** — who is behind the information?
3. **Find better coverage** — find better coverage in authoritative sources
4. **Trace to the original** — trace to the primary source

Resource: https://hapgood.us/2019/06/19/sift-the-four-moves/

## Lateral Reading (Wineburg & McGrew, Stanford, 2017)

Fact-checkers do not read a page "in depth" — they go "laterally", seeking information about the resource itself. Study: 45 participants (10 fact-checkers, 10 historians, 25 students). Fact-checkers worked faster and more accurately than all others.

Study: "Lateral Reading and the Nature of Expertise: Reading Less and Learning More", Stanford History Education Group, 2017. SSRN: 3048994.

Caulfield and Wineburg are co-authors of "Verified" (University of Chicago Press).

## IFCN Code of Principles (Poynter Institute)

International fact-checking standard. 31 criteria, 5 principles:

1. Non-partisanship and Fairness
2. Transparency of Sources
3. Transparency of Organization & Funding
4. Transparency of Methodology
5. Open & Honest Corrections

Resource: https://ifcncodeofprinciples.poynter.org/

## Calling Bullshit (Bergstrom & West, 2020)

Course and book (University of Washington). Key concepts: Brandolini's law (energy to refute >> energy to create bullshit), Fermi estimation, GRIM test, Benford's law, effect size, visual manipulations (truncated axes, violation of proportional ink).

Resource: https://www.callingbullshit.org/

## Statistical Fact-Checking

Methods for verifying numerical data, popularized by Bergstrom & West (Calling Bullshit, 2020):

- **Effect size** — is the result clinically significant? Statistical significance (p < 0.05) does not imply practical significance.
- **GRIM test** — consistency check: do the mean, N, and proportions converge? If the mean is 4.3 with N=7 — it must be an integer * N / N.
- **Benford's law** — distribution of leading digits in natural data: 1 appears ~30%, 9 — ~5%. Deviation is a sign of manipulation.

## Anti-Sycophancy

A method for detecting agreement with the user contrary to facts. Distinct from anti-hallucination: hallucination — the agent fabricated a fact, sycophancy — the agent found the fact but agreed with the user instead of challenging them.

Method: formulate the user's position, find facts against this position via search, compare. If facts contradict — explicitly state the discrepancy, do not fit the conclusion.

## CoVe — Chain-of-Verification (Meta AI, 2023)

AI-specific technique for reducing hallucinations:

1. Draft response — draft answer
2. Plan verification questions — verification questions for the draft
3. Answer independently — answer questions without the draft context
4. Generate verified response — verified answer

Study: Dhuliawala et al., "Chain-of-Verification Reduces Hallucination in Large Language Models", arXiv:2309.11495, 2023.

## Baloney Detection Kit (Carl Sagan, 1995)

Chapter "The Fine Art of Baloney Detection" from "The Demon-Haunted World" (first edition — 1995, Random House). A toolkit: independent confirmation, multiple hypotheses, Occam's razor, quantitative estimates, checking every link in the argumentation.

## Critical Thinking (Tom Chatfield, Oxford)

Anchoring, framing, Bayes' theorem, base rate fallacy. Separate framing from content.

## Anatomy of Delusions (Nikita Nepryakhin, Alpina)

Form of presentation ≠ content. Cognitive biases, logic, argumentation.

## KlemGU Algorithm (Komleva & Solomin, 2022)

Unified fact-checking algorithm for online media journalists. Verification: proper names, sources, quotes, details, visual elements.

Source: Komleva V.Yu., Solomin V.E., "Virtual Communication and Social Networks", 2022, 1(4): 167-171.

---

## v6 Additions

The following methods and principles were introduced in v6.0 of the skill and are documented here for completeness.

### Primary-Source-First Principle

Prefer primary sources over secondary retellings. An arXiv paper — the paper itself, not a blog summary. A GitHub repo — the repo, not a news article about it. A law or standard — the official text.

Two retellings do not make a fact more reliable if both cite the same primary source. See also "Same-source echo" below.

### Source Independence and Same-Source Echo

Before counting "confirmed by 2+ sources", check whether sources share a common primary origin:

- **Primary-source confirmation** — fact confirmed by the primary source directly.
- **Independent corroboration** — two sources confirm independently, without sharing an origin.
- **Same-source echo** — multiple sources retell the same original source. Does not count as independent confirmation.

Also check for conflict of interest: does the source report the fact itself, or cite someone else?

### Quote Verification

Open the original document, compare verbatim. Check context: is the quote taken out of context? Is the attribution correct? Does the surrounding text change the meaning?

Applicable to claim type "quote" — always required in all modes.

### Scientific and Technical Claim Verification

Separate workflow for scientific/technical claims:

1. Check paper metadata (authors, date, journal)
2. Compare abstract with the claim formulation
3. Check tables/appendix for specific numbers
4. Check code and data availability
5. Check peer review status
6. Check confidence intervals
7. Distinguish direct measurement from model-derived estimate

### False Rigor Rule

Do not name a method if you have not applied it concretely and cannot state the result.

Bad: "Using Popperian falsification, the claim is plausible."
Good: "Search for disconfirming evidence: X, Y. Found Z, which weakens the claim."

### Uncertainty, Confidence, and Caveats

For each verdict, state:
- **Confidence level** — high / medium / low
- **Evidence quality** — primary / secondary / indirect / absent
- **Caveats** — what could change the verdict
- **Not checked** — what was not verified

### Output Template (Standard and Publication-Grade)

1. **Summary verdict** — 1–3 sentences: what was checked, overall result.
2. **Claim checks** — for each: claim, verdict, evidence, sources with dates, caveats, confidence level.
3. **Material issues** — overstatements, missing context, unsupported assumptions.
4. **Suggested correction** — reformulated claims incorporating verification results.
