# Powerbuildizer

A Claude skill that runs product work end to end — framing a vague idea, writing
a cahier des charges, a PRD and user stories, critiquing an interface, building a
throwaway prototype, keeping project state current, and orchestrating a team of
sub-agents.

Instructions are written in English for instruction-following reliability.
**Everything it produces is written in the user's language, French by default**,
with deliverable templates kept in French on purpose.

---

## Why this exists

Most product assistants agree with you. They turn a one-line request into a
plausible PRD in ninety seconds, and the cost of a product has never come from
the speed of writing — it comes from the assumptions nobody questioned.

Powerbuildizer is built around the opposite behaviour: it refuses to move when
the ground isn't solid, it says so out loud, and it argues once before complying.

## What it does differently

**Closed gates, not advice.** No solution before the problem is stated. One main
flow, named in a single sentence, before any spec or screen. The four states of
every screen — empty, loading, error, full — because the nominal case is the easy
part and the other three are what gets discovered in production. Mandatory
non-goals. No invented numbers: a source, or an explicit `[À VÉRIFIER]` marker.

**Calibration before ceremony.** A rigorous protocol applied to a two-hour
request doesn't get corrected, it gets bypassed — the most likely failure mode
of any demanding skill. Three checks (irreversible? sensitive data or legal
obligation? more than two days?) decide between one question and the full
protocol, and the skill announces which mode it picked.

**Sourced, dated standards.** WCAG 2.2 level AA as the reference, including the
criteria teams most often miss: target size 2.5.8 (24 × 24 CSS px, with the
spacing exception), focus not obscured 2.4.11, dragging movements 2.5.7,
accessible authentication 3.3.8, consistent help 3.2.6, redundant entry 3.3.7.
Core Web Vitals at their current thresholds — LCP ≤ 2.5 s, INP ≤ 200 ms (INP
replaced FID in March 2024), CLS ≤ 0.1, at the 75th percentile of field data.
Scope of the European Accessibility Act, so the skill asks early whether
accessibility is a quality goal or a compliance constraint for this product.

**A cognitive reading grid, with its misuses named.** Twenty-eight heuristics
adapted from [Laws of UX](https://lawsofux.com), grouped by use, each with what
it predicts and when it actually helps — plus an explicit trap list. Miller's
7 ± 2 is about what you memorise, not about menu entries. Hick's law doesn't say
"fewer options", it says choosing costs time. The aesthetic-usability effect
cuts both ways: a beautiful mockup hides its own usability defects in testing.
The rule is two or three laws per critique, never cited as the argument itself.

**A posture that challenges.** Derive before asking — the repo README, the docs,
the code — then at most three questions per turn. Propose two options with their
trade-offs rather than asking an open question. Answer the eleven questions an
engineer will ask on day one before they land. And when feedback is a claim
rather than a preference, probe it once, then close the loop and record the
decision instead of relitigating it every turn.

**Hierarchical agent orchestration.** Three levels — lead, pole leads, workers —
where the hierarchy lives in files rather than in the call stack. Every
delegation goes through a written brief that points at file paths without copying
their contents, and every agent reads the original sources. Agents diverge and
verify; they never decide.

---

## Installation

### Claude Code — plugin marketplace (recommended)

```
/plugin marketplace add <owner>/<repo>
/plugin install powerbuildizer@karonath-skills
```

Pull later changes with `/plugin marketplace update`, then `/plugin update`.
To validate the manifests before publishing, `add` accepts a local path:
`/plugin marketplace add /path/to/this/repo`.

### Claude Code — manual copy

```bash
# personal, available in every project
cp -r plugins/powerbuildizer/skills/powerbuildizer ~/.claude/skills/

# project-scoped, shared with the team through the repo
cp -r plugins/powerbuildizer/skills/powerbuildizer .claude/skills/
```

### Claude on web and desktop

Zip the `skills/powerbuildizer` folder, rename it to `powerbuildizer.skill`, and
import it under Settings → Capabilities → Skills.

---

## How it works

Powerbuildizer routes to one phase at a time and loads a single reference file
for it.

| The user says, in substance | Phase | Reference |
|---|---|---|
| "j'ai une idée", "on pourrait faire" | Framing | `1-cadrage.md` |
| "écris la spec", "le cahier des charges" | Spec | `2-spec.md` |
| "regarde cet écran", shares a screenshot | UX critique | `3-ux-critique.md` |
| "fais un proto" | Prototype | `4-prototype.md` |
| "on en est où" | Tracking | `5-suivi.md` |
| wide work, independent angles | Orchestration | `6-agents.md` |

Deliverables are written to the repository, in Markdown, versioned:

```
docs/produit/
├── ETAT.md                     # dashboard and source of truth
├── 01-cadrage/<sujet>.md
├── 02-spec/<feature>.md
├── 03-stories/<feature>.md
├── 04-ux/<date>-<écran>.md
├── decisions/ADR-001-<titre>.md
├── proto/
└── _agents/<run-id>/
```

`ETAT.md` is read at the start of every phase and updated at the end of each one.
It carries the product context — type, users, stage, EAA scope — so the skill
asks those questions once and never again.

## Repository structure

```
.claude-plugin/marketplace.json     # marketplace catalog
plugins/powerbuildizer/
├── .claude-plugin/plugin.json      # plugin manifest
└── skills/powerbuildizer/
    ├── SKILL.md                    # router: calibration, gates, phases, posture
    └── references/
        ├── 1-cadrage.md
        ├── 2-spec.md
        ├── 3-ux-critique.md
        ├── 4-prototype.md
        ├── 5-suivi.md
        ├── 6-agents.md
        ├── 7-questionnement.md
        ├── standards-ux.md
        └── lois-ux.md
```

Only `SKILL.md` (~2,100 tokens) loads on every trigger. The nine files total
roughly 11,700 tokens, loaded one reference at a time.

## Customising it

Two files carry opinions and are meant to be edited:

- **`standards-ux.md`** — the numeric thresholds come from verifiable standards
  and shouldn't be invented or rounded; the rest is owned opinion (show nothing
  below 300 ms of loading, undo over confirmation, one primary action per
  screen). Replace it with yours.
- **`7-questionnement.md`** — governs conversational behaviour. Adjust here if
  the skill pushes back too much or too little.

Standards carry a verification date. Re-check them when it is more than a year
old: sources were last verified in September 2026.

---

## Attribution

The cognitive reading grid in `lois-ux.md` is adapted from
[Laws of UX](https://lawsofux.com) by Jon Yablonski, which is published under
CC BY-NC-ND 4.0. The file paraphrases and comments rather than reproducing the
original text; if you redistribute it, keep the attribution.

Accessibility criteria come from the W3C's WCAG 2.2 recommendation. Performance
thresholds come from Google's Core Web Vitals. Scope and dates for the European
Accessibility Act come from Directive (EU) 2019/882 and its French
transposition (loi DDADUE n° 2023-171).

## License

Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
(CC BY-NC-SA 4.0). See [`LICENSE`](LICENSE).

The NonCommercial and ShareAlike terms are a deliberate choice, aligned with the
terms of the Laws of UX material this skill draws on. To relicense more
permissively, edit `LICENSE` and this section — but review the attribution above
first.

## Author

Charlys Menuet (Karonath)
