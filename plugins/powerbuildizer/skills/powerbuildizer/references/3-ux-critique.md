# Phase 3 — UX critique

Make an interface better, not demonstrate that you can criticise. Every problem
comes with a concrete fix. A critique without a fix is noise and costs credit
with whoever receives it.

## Before looking

Two things must be known, or the critique floats: the task the user is trying to
complete on this screen, and their state of mind (first visit, daily use, in a
hurry, panicking). An admin screen used 200 times a day and a signup page aren't
judged with the same grid.

**Derive before asking**, in this order — asking for something the person has
already published is the fastest way to look useless:

1. `docs/produit/ETAT.md`.
2. The product's own documentation: `README.md` at the repo root, `docs/`, a
   landing page, the repo URL the person just pasted. READMEs usually state who
   the tool is for and what problem it solves, in their own words. Fetch and
   read it.
3. The surrounding code: route names, component names, test fixtures.
4. The request itself and the conversation.

Only what none of these answer becomes a question — one, not three. When you
derive rather than ask, say which source you used in a single line, so the
person can correct a wrong reading.

**Declare your observation conditions.** A critique made from a static
screenshot of a demo dataset is not a critique of the product. State what you
looked at, at what width, on real or seeded data, and what you did not measure
(contrast ratios, keyboard navigation, behaviour under load). Severities depend
on it: a panel that overlaps at 1366 px may be fine at 1920 px.

## The grid, in order

Order matters: fixing hierarchy after debating button radii is the most common
way to lose a review.

1. **Flow** — within three seconds, is it clear what can be done here and what
   the primary action is? Is there more than one primary action?
2. **Hierarchy** — is what's visually strongest also what matters most?
3. **Load** — how many decisions at once? What could be removed, deferred, or
   decided on the user's behalf?
4. **States** — empty, loading, error, full, plus the in-betweens: partially
   filled, single result, 10,000 results, insufficient permissions, offline.
   This is where most real problems are.
5. **Words** — do labels say what will happen? Do errors say what to do next?
   See `standards-ux.md`.
6. **Accessibility and mobile** — contrast, target size, keyboard, visible
   focus, behaviour at 375 px wide. Check against `standards-ux.md`, which
   carries the WCAG 2.2 AA criteria most often missed.

`lois-ux.md` is the optional reading grid: use it to explain *why* something
fails, two or three laws at most, never as the argument itself.

## Output format

To `docs/produit/04-ux/<date>-<écran>.md`, sorted by severity, not by position
on screen. French headings:

```markdown
# Critique — [écran] — [date]
Contexte : [tâche de l'utilisateur, état d'esprit] — source : [d'où ça vient]
Conditions : [capture statique ou app en main, largeur, données réelles ou démo]
Non mesuré : [contrastes, clavier, charge, ce qui reste à vérifier]

## Bloquant
### B1 — [problème en une ligne]
Ce qui se passe : [observation factuelle]
Conséquence : [ce que l'utilisateur rate ou subit]
Correctif : [proposition concrète, jusqu'au libellé si c'est du texte]

## Majeur
## Mineur

## Ce qui marche bien
[2 ou 3 points, honnêtes.]

## Ce dont je ne suis pas sûr
[Hypothèses prises, ce qui changerait le verdict, ce qui reste à vérifier.]
```

Severity: **Bloquant** — the user can't complete the task, loses data, or is
excluded (accessibility). **Majeur** — they manage, with friction, a likely
error or a plausible abandon. **Mineur** — cosmetic, consistency, polish.

Don't inflate. If everything is blocking, nothing is, and the reader stops
reading. The "ce qui marche bien" section isn't politeness: what works must be
named so it survives the next redesign.

## With several agents

Critique is the best place to parallelise — each angle is independent and you
want views that don't contaminate each other. See `6-agents.md`, "Critique
fan-out".
