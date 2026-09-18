# Orchestration — hierarchical agent team

## Principle

The hierarchy lives in files, not in the call stack. Each level writes a brief to
disk before delegating, and every agent reads that brief **and** the original
source documents. Otherwise each hop adds a layer of rephrasing and level 3 works
from a paraphrase of a paraphrase — the result is clean, coherent and off-target.

Working directory: `docs/produit/_agents/<run-id>/`. One run = one delegation
wave. It outlives the session, which is what makes the work auditable.

## Three levels

| Level | Role | Decides | Delegates to |
|---|---|---|---|
| **N0 — Lead** | Main thread, faces the human | Scope, trade-offs, phase sign-off | N1 |
| **N1 — Pole lead** | Splits a lot, recombines, judges quality | Nothing touching scope | N2 |
| **N2 — Worker** | One angle, one deliverable, one file | Nothing | Nobody |

Possible N1 poles: Cadrage, Spec, UX, Prototype, Cohérence. Open only those with
real work. A pole with one N2 is pointless — do it yourself.

**Maximum depth: 3.** If an N2 needs to delegate, its lot was badly split. It
reports back to N1 rather than creating an N3.

Spawn N1 and N2 with the Task tool, one call per agent, all agents of a pole in
the same turn.

## Delegation contract

No agent is launched without its written brief, in
`_agents/<run-id>/briefs/<level>-<name>.md`:

```markdown
---
agent: N2-ux-etats
parent: N1-ux
run: 2026-09-18-refonte-checkout
---
## Ta mission
[Une phrase. Un seul angle.]

## Lis d'abord (dans cet ordre)
- docs/produit/ETAT.md
- docs/produit/02-spec/checkout.md §Écrans et états
- [les sources originales, jamais un résumé]

## Ce que tu produis
Fichier : _agents/<run-id>/sorties/N2-ux-etats.md
Format : [le gabarit exact attendu]

## Hors de ton périmètre
[Explicite : c'est ce qui empêche quatre agents de réécrire la même chose.]

## Si tu es bloqué
Écris BLOQUÉ en tête de ton fichier, avec la question. Ne devine pas.
```

Reports always take the same shape: what I found, what I'm unsure about, what I
couldn't verify. The third section is the most useful and the one agents drop —
require it.

## What parallelises, and what doesn't

**Yes** — divergent or verifiable work: multi-angle critique of a screen; three
competing flow options to compare; consistency checks across spec, stories and
mockups; acceptance criteria for already-split stories; competitive scans.

**No** — work needing a single owner: framing the problem; any scope or priority
call; phase sign-off; writing `ETAT.md` (N0 only).

Same reason every time: when several agents decide, nobody decides, and the
inconsistency shows up three weeks later in the code.

## Critique fan-out — the model case

N1-UX opens four N2 on one screen, each blind to the others: flow and hierarchy
/ states and edge cases / wording and error messages / accessibility and mobile.
Each returns its list in the `3-ux-critique.md` format.

N1-UX then recombines: merge duplicates, settle severities, and — the important
part — **list the disagreements separately** instead of smoothing them. Two
agents diverging on a severity is the most interesting output of the run, not a
defect to clean up.

## Guard rails

1. **A run announces its budget** before launching: how many agents, roughly
   what it costs. Eight agents on a two-day feature is a scale error; say so.
2. **Nothing merges into `docs/produit/` without N0.** Agent outputs stay in
   `_agents/` until validated.
3. **A blocked agent reports, it doesn't improvise.** An assumption invented at
   N2 comes out at N0 as a fact.
4. **Re-read outputs before believing them.** N0's job isn't to aggregate what
   its agents said, it's to judge it. If N0 only adds glue, the run shouldn't
   have happened.

## Context economy

A run costs most through recopying: each level that reproduces what it read pays
twice for the same content and adds a layer of distortion on top. These rules
serve accuracy as much as performance.

- **A brief points, it doesn't copy.** File paths and section numbers, never
  content. That's also what guarantees the agent reads the source.
- **Targeted reads.** On a large file, Grep for the section and Read that range
  alone. A whole file loaded for three lines is context lost to the rest of the run.
- **Short, fixed-format reports.** Findings, uncertainties, unverified. No
  restatement of the mission, no closing pleasantries: the parent knows the
  context, it only wants what's new.
- **Four agents per pole maximum.** Beyond that, angles overlap and recombining
  costs more than it returns.
- **One wave when possible.** Launch a pole's agents together rather than in
  series: same work, same wall-clock wait.
- **Nothing is relaunched without cause.** If an output is nearly right, fix it
  directly instead of re-briefing the agent.

The same economy applies outside runs: one reference file per phase, and never
re-read `ETAT.md` twice in one session.
