# Changelog

All notable changes to Powerbuildizer are documented here. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); this project uses
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] — 2026-09-18

First release. Built and stress-tested in a single session; every rule below
that looks oddly specific is specific because a test made it so.

### Added

- **`SKILL.md`** — router carrying the calibration test, the seven closed gates,
  the phase table, the deliverable tree, the agent model and the posture.
  ~2,100 tokens, the only file loaded on every trigger.
- **`1-cadrage.md`** — turning a vague idea into an attackable problem; the four
  highest-yield questions; naming the riskiest assumption and testing it cheaply
  before any spec.
- **`2-spec.md`** — PRD and cahier des charges (same structure, different
  audiences and legal weight), user stories with stable IDs, Gherkin acceptance
  criteria including a mandatory error case, vertical-slice splitting.
- **`3-ux-critique.md`** — six-step grid in fixed order, three severity levels,
  no finding without a fix.
- **`4-prototype.md`** — the single question a prototype must answer, realistic
  data, all four states, throwaway by design.
- **`5-suivi.md`** — `ETAT.md` format, ADR discipline, session-start ritual.
- **`6-agents.md`** — three-level orchestration (N0/N1/N2), written brief
  contract, what parallelises and what doesn't, context-economy rules.
- **`7-questionnement.md`** — digging, proposing over asking, challenging a
  claim, the eleven recurring engineering questions, the uncertainty report.
- **`standards-ux.md`** — WCAG 2.2 AA (including 2.5.8, 2.4.11, 2.5.7, 3.3.8,
  3.2.6, 3.3.7), Core Web Vitals (LCP 2.5 s / INP 200 ms / CLS 0.1), European
  Accessibility Act scope, the four states, wording and load rules.
  Sources verified September 2026.
- **`lois-ux.md`** — 28 heuristics adapted from Laws of UX, grouped by use, with
  an explicit list of their common misuses.
- Plugin marketplace manifests, CC BY-NC-SA 4.0 license, English README.

### Design decisions worth remembering

- **One skill, not six.** A set of narrow skills that trigger poorly is worse
  than one entry point with phases behind it. Revisit if usage turns out to be
  lopsided — UX critique is the likeliest candidate for extraction.
- **Instructions in English, deliverables in French.** Measured cost of French
  prose: ~22% more tokens, plus slightly weaker instruction-following. The
  deliverable templates stay French to stop the instruction language from
  leaking into the output; a `## Language` section enforces it.
- **Agents diverge and verify, they never decide.** Parallelising product
  decisions yields several coherent documents that are wrong together, with no
  signal that anything broke.
- **Hierarchy in files, not in the call stack.** Briefs point at paths instead of
  copying content, so no level works from a paraphrase of a paraphrase. Same rule
  saves tokens and accuracy at once.

### Found by testing, fixed before release

Four defects, none visible on reading — all four surfaced by running the skill
on real prompts.

1. **No escape hatch for small requests.** The full protocol applied to a
   two-hour task doesn't get corrected, it gets bypassed. Added the calibration
   test (irreversible? sensitive or legal? more than two days?) ahead of the
   gates, with gates 1, 5 and 6 still active in light mode, and the reverse
   switch when a light request turns heavy mid-way.
2. **Asking for context that was already published.** The skill only looked at
   `ETAT.md`. Added an explicit derivation order — `ETAT.md`, then the product's
   own README and docs, then the code, then the conversation — with at most one
   question for what none of them answer, and a line naming the source used.
3. **Observation conditions left implicit.** A critique made from a static
   screenshot of a demo dataset is not a critique of the product. The critique
   template now declares what was looked at, at what width, on real or seeded
   data, and what was not measured.
4. **The insistence clause fired on a keyword.** The rule allowed pressing a
   second time on "legal obligation (accessibility under the EAA, GDPR)" — which
   led to invoking the EAA on a local proprietary tool it plainly doesn't cover.
   Pressing in the name of a law that doesn't apply spends authority you don't
   get back. The clause now requires an obligation *checked as applicable to
   this product*, and the skill must concede the framing when it doesn't apply.
   Same fix added the category-rejection manoeuvre: when feedback rejects a whole
   category, test whether the substance survives under another name before
   dropping it — and drop it without negotiating if it doesn't.

### Known limits

- Marketplace manifest schema was not validated against official documentation;
  verify locally with `/plugin marketplace add /path/to/repo` before relying on
  the marketplace route.
- Numeric standards are dated and will drift. `standards-ux.md` carries its
  verification date for that reason.
- The `lois-ux.md` grid paraphrases CC BY-NC-ND material. It comments rather than
  reproduces, but that boundary is not sharp — hence the NC-SA license choice.
- Conversational behaviour was exercised on a single simulated exchange. Real
  usage over a week is the actual test.
