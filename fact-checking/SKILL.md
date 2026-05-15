---
title: "Fact-Checking: Identification, Method Selection, Verification"
description: "Use when verifying factual claims, source reliability, quotes, numbers, scientific results, or publication texts. Identifies claim type, selects methods by mode (quick / standard / publication), performs verification, classifies verdict."
properties:
  - name: name
    value: ["fact-checking"]
  - name: version
    value: ["6.1.0"]
  - name: author
    value: ["Digital Center of Engineering — DICE"]
  - name: license
    value: ["Apache-2.0"]
---

Use for source verification, fact-checking claims, and preparing materials for publication. The skill must guide the agent toward a verifiable protocol, not a list of methodological labels: for each substantive claim, record the verification criterion, source type, level of access to evidence, and final verdict.

## REGULATION

**Fast-path:** for simple reference queries (simple figure, existence, attribution) — one primary source, verdict in 1–3 sentences, no full report. Risk gate may upgrade the mode.

**Stage 1. Identification:** Formulate the main claim, decompose into atomic claims, determine literal/rhetorical, classify by type, apply risk gate and select mode (quick / standard / publication), assess significance. See "Stage 1" section.
**Stage 2. Method selection:** Match type to method set by layers. See "Stage 2" section.
**Stage 3. Verification:** Find sufficient evidence: primary source, independent confirmation, or explicitly marked absence of data. Use two search circuits when the primary source does not resolve the question or independent context is needed. See "Stage 3" section.
**Stage 4. Classification:** Assign verdict (confirmed / partially confirmed / unconfirmed / contradiction / refuted / misleading / unverifiable in this formulation), indicate confidence level, source level, and access level. See "Stage 4" section.
**Stage 5. Synthesis:** Compile report using template. See "Stage 5" section.
**Stage 6. Archiving:** Save report, update indexes. See "Stage 6" section.

**Rules:** 1) Do not generate numbers — only from sources or explicitly marked Fermi estimates. 2) Check source dates — mark outdated ones. 3) Scan for sycophancy — do not agree with the user without verification. 4) Verify your own conclusions before publication. 5) Red flag — stop normal output and notify the operator if there is risk of: harm to health, defamation / reputational damage, publication of personal data without consent, client/partner trade secrets, medical/legal/financial advice, details of active negotiations. 6) Do not apply statistical methods without checking applicability conditions. 7) Do not name a method without a concrete result. 8) If the base rate is unknown — state it, do not invent one.
**Exceptions:** 1) No sources — record "unconfirmed" or "unverifiable in this formulation", do not speculate. 2) If full topic research is needed rather than verification of specific claims — delegate to a research skill.

## Stage 1. Identification

### 1.1. Main claim

Formulate the main claim of the text being checked. Example formulations for different materials:
- Skill — "the set of methods is sufficient for the task"
- Post — "the argument proves the conclusion"
- Report — "the conclusions follow from the data"
- Analytical note — "the assessment is supported by data"
- Presentation — "the key thesis is confirmed"

If the material does not fit the examples — formulate the main claim in your own words: what main idea are you checking.

For the main claim, formulate 2–3 conditions that could weaken or refute it. Do not call this "Popper" unless you show specific conditions and search results. One refuting condition automatically breaks only absolute claims ("always", "never", "the only one"). For probabilistic and contextual claims it reduces confidence or requires frame clarification.

**When to apply:** use for materials with clear argumentative structure (report, analytical note, thesis-driven post) or when the cost of error is high. Skip for simple reference queries, quote checks, and artistic/rhetorical phrases unless the user asks for literal verification.

If the main claim is not confirmed — do not stop blindly. Narrow the scope: continue checking claims that explain why the main one failed, or prevent an erroneous correction.

### 1.2. Atomic claims

Decompose the text into minimal verifiable units. One claim = one check.

Example: "Kriogenmash is a major player, revenue 8.6 billion, growth 48%" — 3 claims: (1) major player [status], (2) revenue 8.6 billion [simple figure], (3) growth 48% [simple figure].

Opinions with markers ("it seems", "I think", "in my feeling") — strip the **form** but check the **factual core**. If behind the opinion wrapper there is a verifiable claim — extract and check it. Discard only pure opinions without a factual core.

Examples:
- "It seems to me, revenue is 8.6 billion": strip "it seems", check "revenue is 8.6 billion"
- "I think the birds won't make it": strip "I think", check "the birds won't make it"
- "It feels like quality is declining": pure opinion, not verifiable

### 1.3. Literal, rhetorical, and verifiable

Before typing, determine how the claim is being used:

- **Literal as fact:** check normally, proceed to 1.4.
- **Rhetorically / artistically / as a joke:** do not check as fact unless the user requests literal verification. Mark as "rhetorical", stop.
- **Evaluative or vague:** formulate an operational criterion. If no criterion is possible, issue verdict "unverifiable in this formulation", stop.

Example: "A rare bird will reach the middle of the Dnieper" as a Gogol quote requires quote verification (literal); as an artistic hyperbole it is classified as rhetorical, stop.

### 1.4. Claim types

Determine the type of each claim. Methods by type — see [references/applicability-matrix.md](references/applicability-matrix.md).

**Simple figure:** a specific number, date, name, title without statistical context. Example: "revenue 8.6 billion", "founded in 2005". Methods: SIFT, primary source, cross-checking, framing.

**Statistics:** averages, percentages, p-values, confidence intervals, sample sizes. Example: "average height 175 cm with N=200", "accuracy 97%". Methods: SIFT, primary source, cross-checking, lateral reading + GRIM, effect size, Benford's law (subject to applicability conditions).

**Status:** a claim about a state of affairs. Example: "the term is established", "the standard has been adopted". Methods: SIFT, lateral reading, cross-checking.

**Causation:** a cause-and-effect relationship. Example: "sanctions led to a 40% price increase". Methods: SIFT, cross-checking.

**Prediction:** a claim about the future or an estimate. Example: "the market will grow 3x". Methods: SIFT, Fermi estimate, Bayes / base rates.

**Methodology:** assessment of an approach's, method's, or school's reliability. Example: "SIFT is the fact-checking standard in journalism". Methods: lateral reading, cross-checking.

**Quote:** accuracy of citation. Example: "Einstein said: 'Imagination is more important than knowledge'" — check whether he actually said it and in which source it first appeared. Methods: quote verification, primary source.

**Attribution:** who a claim, idea, or product belongs to. Example: "PDCA was proposed by Deming". Methods: SIFT, primary source.

**Existence:** whether an object exists. Example: "there is GOST R 57700.37". Methods: SIFT, primary source.

**Comparison:** "better/bigger/first/only". Example: "Russia is the leader in gas reserves". Methods: SIFT, cross-checking, framing.

**Normative:** reference to a law, standard, regulation. Example: "according to ISO 9001:2015, clause 4.1". Methods: primary source (text of the law/standard).

**Scientific result:** a claim about research results. Example: "the method shows 97% accuracy on the MNIST dataset". Methods: scientific publication verification (Stage 3).

**Agent's own conclusion:** a claim generated by the agent. Example: "the likely reason is staff shortage". Methods: light verification chain, anti-hallucination, anti-sycophancy.

**Historical-personal:** a claim from personal chronicle or project history: "we met on March 1", "the team received a grant", "the first prototype was built in a week". Methods: internal primary source + search for external trace; if no external trace exists, mark as self-report / externally uncorroborated.

**Source provenance:** origin of a document, screenshot, image, letter, archive. Methods: check the original, metadata, URL, publication/modification date, archival copy, independent registry; separately indicate whether a screenshot is evidence of the fact or only evidence that the screenshot exists.

### 1.5. Risk gate and mode

**Level A — task context (before claim decomposition):**
- result will be published in a channel, article, presentation, or report: upgrade minimum to standard
- topic: health, law, finance, reputation, personal data: upgrade minimum to standard

**Level B — after claim decomposition:**
- claim contains "first / only / best / largest": upgrade to standard
- sources conflict: upgrade to standard
- source has a conflict of interest: upgrade to standard
- longread (5+ substantive claims): upgrade to publication

**Final mode = max(level_A, level_B, mode_by_types).**

After risk gate, refine the mode by claim types:

- **Quick** — all claims of type "simple figure", "existence", "attribution", "status". Apply operational methods and protective mechanisms. Check via one primary source, Fermi estimate if needed. Deliver verdict in 1–3 sentences. Stage 2 — select method automatically by type, without justification. Stage 3 — one source. Stage 4 — verdict without confidence/caveats. Stage 5 — no expanded report. "Status" claims are allowed in quick mode only if checked via one primary source.
- **Standard** — contains claims of type "statistics", "causation", "prediction", "status", "comparison", "quote", "normative". Apply operational, statistical, and protective methods. Compile full report using template (Stage 5).
- **Publication** — material intended for a channel, article, conference, or contains types "methodology", "scientific result". Apply all method layers, including epistemic frameworks. Compile full report using template.

### 1.6. Significance

Assess whether the claim affects the argument's conclusion. A fact that is the argument's foundation — confirm first. A fact that does not affect the conclusion — low priority.

**Stage 1 completion criteria:** main claim formulated, substantive claims identified, literal/rhetorical usage determined, each claim classified by type, mode selected via risk gate + types, significance assessed.

## Stage 2. Method selection

Methods are divided into four layers. Layer selection depends on mode and claim type. Detailed description of each method — in [references/methodologies.md](references/methodologies.md). The "type × method × layer" matrix — in [references/applicability-matrix.md](references/applicability-matrix.md).

**Refinement cycle:** if results diverge at Stage 3, return to Stage 2 and add not a "beautiful method" but the missing operation:
- Source conflict — check dates, definitions, primary sources, independence, and evidence access level.
- Unconfirmed — formulate an operational verification criterion; if no criterion exists, verdict "unverifiable in this formulation".
- Same-source echo — add lateral reading and find an independent source or explicitly mark as same-source echo.
- Methodological dispute — only in publication mode present competing presuppositions; do not use Popper/Kuhn/Lakatos for simple data-point conflicts.

### Layer 1. Operational methods (all modes)

**SIFT (Caulfield, 2019).** Stop, investigate the source, find better coverage, trace to the original.

**Lateral reading (Wineburg & McGrew, 2017).** Check the source from the outside: who is behind the site, what others say, is there a conflict of interest. Do not trust the "About us" page.

**Primary source.** Prefer primary sources. Secondary independent ones — when the primary is unavailable, conflicts, or the interpretation rather than raw fact is being checked.

**Cross-checking.** If results diverge — find a third, independent source.

**Fermi estimate.** Estimate the order of magnitude before searching. "10 billion users" — impossible. Named after Enrico Fermi, popularized by Bergstrom and West (Calling Bullshit, 2020).

**Framing.** "90% survival rate" vs "10% mortality" — the same number. Check the framing, not just the number.

**Quote verification.** Open the original with an available tool, compare verbatim. Check context: is the quote taken out of context?

### Layer 2. Statistical methods (standard and publication modes)

Apply **only** to claims with numerical data. Each method has applicability conditions — do not apply blindly.

**Effect size.** Statistical significance (p-value) does not mean practical significance. A 0.1% difference can be statistically significant at N=100000 but meaningless in practice. Check: is the difference large enough to have practical consequences?
- Applicable: when there is a quantitative result and practical significance can be assessed.
- Not applicable: when there is no significance threshold for the given field.
- What to do: state that practical significance was not assessed.

**GRIM test.** Checks internal consistency: if a mean is reported for N respondents, then the product of mean × N should yield an integer (if the scale is integer). If it doesn't — the mean was likely computed incorrectly or fabricated.
- Applicable: only for means from integer scales with known N.
- Not applicable: for non-integer scales, unknown N, percentages without a stated base.

**Benford's law.** In suitable natural numerical data (populations, budgets, areas) the leading digit is distributed unevenly: 1 appears about 30% of the time, 9 — about 5%. Deviation is only a screening signal when applicability conditions are met, not proof of manipulation by itself.
- Applicable: for natural large-scale numerical data (populations, budgets).
- Not applicable: for IDs, bounded ranges, prices with psychological rounding, small samples (< 100).

**Algorithm on deviation:**
1. Check applicability conditions (N > 100, natural data, not IDs, not bounded range). If conditions are not met, the signal is false — stop.
2. If conditions are met, check alternative explanations: small sample, psychological rounding, narrow range, threshold values.
3. If alternatives do not explain, mark in report: "leading digit distribution deviates from Benford's law. Possible cause: [options]. Not proof of manipulation."
4. Do not write "data fabricated" based on Benford's alone without additional evidence.

**Bayes / base rates.** For predictions: what is the base probability from past forecasts of a similar type? A positive test for a rare event does not mean high probability. Example: "the market will grow 3x" — if 1 out of 10 past 3x growth forecasts came true, base probability is 10%. An authoritative source does not mean confirmation.
- Applicable: when base rate data exists.
- Not applicable: when base rate is unknown — do not invent numbers. State: "base rate unknown, forecast estimate unreliable."

### Layer 3. Protective mechanisms (all modes)

**Anti-hallucination.** Check: (1) the source exists — find via search, do not trust model memory, (2) the quote is accurate — open the original, (3) the number is from the original — check context.

**Anti-sycophancy.** Formulate the user's position, find facts against it, compare. If facts contradict — explicitly indicate the discrepancy.

**Light verification chain.** For agent's own conclusions: formulate one verification question whose answer could change the verdict; check it independently of the draft; correct the conclusion if they diverge. Use full CoVe only for publication mode.

### Layer 4. Epistemic frameworks (rarely, publication mode only)

**Popper (falsificationism).** Use as a technique for finding conditions that weaken the thesis, not as a label in the report. For absolute claims, a confirmed counterexample can refute the thesis; for probabilistic and contextual claims it reduces confidence or requires clarification.

**Lakatos (research programs).** When theories conflict, assess: does one side predict new, previously unknown facts (progressive program), while the other constantly adjusts explanations post hoc (degenerative program). Example: "the company explains every failure as force majeure" — degenerative program.

**Kuhn (paradigms).** When sources conflict — show both positions as different coordinate systems, do not reduce to a common denominator. Result: for each position indicate (1) what presupposition it accepts, (2) what facts it explains, (3) what facts it cannot explain.

**Operational criterion.** If a claim cannot be verified through an observable result — it is not a fact in the current formulation. Formulate a specific criterion: what exactly is being checked and what result would confirm or refute it. Example: "the term is established" — criterion: there are academic publications, standards, dictionary/encyclopedia fixation, or stable usage in specialized sources. Cannot formulate a criterion — verdict "unverifiable in this formulation".

⚠️ **Do not apply epistemic frameworks to simple checks.** They are appropriate only when verifying scientific and methodological claims where an unambiguous answer is impossible without a position in a scientific dispute.

**Stage 2 completion criteria:** for each claim, a set of methods is selected according to mode and type, selection is justified.

## Stage 3. Verification

### Source search

Start with a source that can directly confirm or refute the claim: registry, law, original publication, object card, archive, source document.

Use **two independent discovery paths** if the primary source is unavailable, incomplete, has a stake, or external context is needed. Examples:

1. Official registry + general search.
2. Primary document + archival copy.
3. Russian-language/local query + international or original-language query.
4. Source website + lateral search about the source.

Extract content using available web/browser/archival tools and mark the evidence access level.

If the task goes beyond fact-checking (complex research, comparative analysis, synthesis from multiple sources) — delegate to a research skill.

### Primary-source-first principle

Prefer primary sources: arXiv paper — the article itself, GitHub repo — the repository itself, API docs — official documentation, law/standard — the text of the law/standard. Two retellings do not make a fact more reliable if both cite the same primary source.

### Source hierarchy and independence

Before counting "confirmed by 2+ sources" check: is there a common primary source? Independent confirmation or reprint? Is there a conflict of interest? Does the source report the fact itself or quote someone else?

Distinguish evidence levels (**standard and publication modes only**):

- **A. Official machine-verifiable source** — registry, law, standard, DOI, WHOIS, API, database record.
- **B. Original document or scan with provenance** — order, letter, photograph, archival copy with clear origin.
- **C. Author's self-report** — participant/organization reports about itself; confirms the fact of the statement, but not always the external fact.
- **D. Independent secondary source** — media, research, catalog, directory without a common primary source and conflict of interest.
- **E. Same-source echo / quote aggregator / search snippet** — does not count as independent confirmation.
- **internal** — internal source (transcript, memo, knowledge file, issue). Primary for the fact "participant X reported Y". Not independent for an external fact.

Distinguish:
- **Primary source confirmation** — fact confirmed by a level A/B source.
- **Independent confirmation** — two independent sources of level D or above confirm.
- **Same-source echo** — multiple sources retell the same original — does not count as independent confirmation.

In quick mode, do not require A–E hierarchy — "confirmed / unconfirmed" is sufficient.

### Evidence access level (**standard and publication modes only**)

For each substantive source, mark what was actually accessible:

- **full text open** — original/page/document was read;
- **metadata open** — card, date, title, author accessible, but not full text;
- **search snippet** — only SERP output visible; use as weak evidence and explicitly mark;
- **image/OCR** — text read from image; indicate recognition error risk;
- **unavailable/paywall/blocked** — do not count as confirmation without an alternative.

### Article and longread verification

For long materials, do not check every detail. Identify 5–10 substantive claims that affect the conclusion or could cause harm if wrong. Separately check:

1. links and broken URLs;
2. publication/update dates;
3. quotes and attributions;
4. numbers and strong comparisons;
5. screenshots/images and their provenance;
6. personal recollections: mark as self-report if no external trace exists;
7. internal project sources: primary for "author asserts", but not independent for external facts.

### Scientific and technical claim verification

For scientific and technical claims — a separate procedure: (1) check publication metadata (authors, date, journal), (2) compare abstract with claim formulation, (3) check tables and appendices for numbers, (4) check code and data availability, (5) check peer review status, (6) check confidence intervals, (7) distinguish direct measurement from model-based estimate.

### False rigor rule

**Do not name a method if you did not apply it specifically and cannot state the result.**

Bad: "Using Popperian falsification, the claim is plausible."
Good: "Search for refuting data: X, Y. Found Z, which weakens the claim."

**Stage 3 completion criteria:** each claim verified by selected methods, sources indicated with dates, hallucinations identified and corrected.

## Stage 4. Classification

### Verdicts

Assign each claim one of the verdicts:

- **Confirmed** (✅) — confirmed by a reliable primary source or independent sources
- **Partially confirmed** (⚠️) — correct in essence but with caveats: inaccurate numbers, different context, omitted conditions
- **Unconfirmed** (❓) — insufficient data for confirmation or refutation
- **Contradiction** (🔴) — sources diverge
- **Refuted** (❌) — provably false
- **Misleading** (⛔) — technically not a lie but distorts: out-of-context quoting, cherry-picking, false framing
- **Unverifiable in this formulation** (◻️) — metaphor, evaluation, vague formulation, or claim without an operational criterion

### Uncertainty

For each verdict indicate: **Confidence level** (high / medium / low), **Source level** (A–E or primary / secondary / indirect / absent), **Access level** (full text / metadata / snippet / OCR / unavailable), **Caveats** (what could change the verdict), **Not checked** (what was not verified).

Indicate sources with publication dates.

**Stage 4 completion criteria:** all claims classified with verdict, confidence level, and sources with dates.

## Stage 5. Synthesis

### Quick mode

Deliver verdict in 1–3 sentences with source.

### Standard and publication modes

Compile report using template:

**Brief verdict** — 1–3 sentences: what was checked, overall result.

**Claim verification** — for each: exact formulation, interpretation (literal/rhetorical/evaluative), type, confirmation/refutation criterion, sources with dates, source level and access, verdict, confidence, caveats.

**Key issues** — exaggerations (what is exaggerated), missing context (what context is missing), unconfirmed assumptions (which assumptions are unconfirmed).

**Suggested correction** — reformulated claims accounting for verification.

When sources conflict — show both positions, do not reduce to a common denominator. Assess the "research program" (Lakatos) only in publication mode and only when there is a conflict between competing methodological positions, not when data points diverge.

**Stage 5 completion criteria:** gaps noted, conflicts not smoothed over, result compiled using template.

## Stage 6. Archiving

### 6.1. Artifacts

Final deliverable: fact-checking report with verdicts, sources, and caveats.

### 6.2. Saving

Save the report to an appropriate project directory.

### 6.3. Index updates

Update project indexes as needed.

**Stage 6 completion criteria:** report saved, frontmatter valid.

## References

- `references/methodologies.md` — detailed description of each method
- `references/applicability-matrix.md` — "claim type × method × layer" matrix
- `references/fact-checking-theory.md` — philosophical context: Turing, Popper, Lakatos, Kuhn
