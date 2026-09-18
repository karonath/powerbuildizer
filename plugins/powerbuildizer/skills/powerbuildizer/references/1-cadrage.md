# Phase 1 — Framing (cadrage)

Turn an intuition into a problem you can attack. The output is not a feature
list. It's a problem precise enough that in three months you can say whether it
was solved.

## Running the exchange

Don't produce the document in one shot. Frame first, with short questions, three
per turn maximum. Highest-yield ones, in order:

1. **Who has this problem, concretely?** Refuse "the users". Look for a role, a
   moment, a frequency. "The workshop manager, every Monday morning, building
   the week's schedule."
2. **How do they cope today without us?** The answer is almost always a
   spreadsheet, a WhatsApp group or a habit. That's the real competitor and the
   bar to beat.
3. **What does it cost them?** Time, money, errors, mental load. If nobody can
   answer, that's the first signal the problem is assumed rather than observed.
4. **Why now?** What changed. With no answer, the project will slip.

If they arrive with a solution ("we need a mobile app"), don't reject it: ask
what it would let them do that nothing does today, trace back to the problem,
then return to their solution and say honestly whether it still holds.

## The signal that matters most

Find the riskiest assumption: the one that, if false, collapses everything else.
It's almost always of the form "people will change how they work", and almost
never technical. Name it explicitly and propose the cheapest way to test it —
five conversations, a mockup shown to three people, a manually-operated version
behind the scenes. That test comes before the spec.

## Deliverable

Write to `docs/produit/01-cadrage/<sujet>.md`. Keep the French headings:

```markdown
# Cadrage — [sujet]
Statut : brouillon | validé le [date]

## Le problème
[3 à 5 phrases. Qui, quand, quoi, ce que ça coûte. Pas de solution ici.]

## Aujourd'hui, sans nous
[Comment ils s'en sortent. Le vrai concurrent.]

## Le parcours principal visé
[Une phrase. "X arrive avec Y, et repart avec Z."]

## À quoi on saura que c'est réussi
[1 à 3 signaux observables. Sans données, écrire [À VÉRIFIER].]

## Hypothèse la plus risquée
[L'hypothèse + comment la tester pour pas cher, avant de construire.]

## Ce qu'on ne fait pas
[3 à 6 lignes. Les tentations évidentes qu'on écarte, et pourquoi.]

## Questions ouvertes
[Question — qui peut répondre — d'ici quand]
```

## Exit gate

Don't move to Spec until: the problem holds without naming any feature; the main
flow fits in one sentence; the riskiest assumption is named; the person has read
and explicitly validated.

Say it plainly when it isn't the case: « On peut écrire la spec, mais on ne sait
pas encore [X] — si c'est faux, la spec est à jeter. Tu préfères tester d'abord
ou avancer quand même ? »
