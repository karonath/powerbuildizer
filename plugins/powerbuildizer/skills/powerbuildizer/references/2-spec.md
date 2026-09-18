# Phase 2 — Spec (cahier des charges, PRD, user stories)

Produce a document a human or an agent can execute without coming back with ten
questions. Quality test: if a developer who wasn't in the conversation can build
the feature without guessing, the spec holds.

Prerequisite: framing is validated. If it isn't, go back to phase 1.

## Imposed structure

One file per feature in `docs/produit/02-spec/<feature>.md`. The YAML
front-matter isn't decoration: it's what lets agents read, filter and
cross-check specs without parsing prose. Keep the French headings.

```markdown
---
id: SPEC-012
feature: nom-court-en-kebab-case
statut: brouillon | validé | en-construction | livré
cadrage: docs/produit/01-cadrage/<sujet>.md
maj: AAAA-MM-JJ
---

# [Nom de la feature]

## Pourquoi
[3 phrases max, reprises du cadrage. Le problème, pas la solution.]

## Parcours principal
[Étape par étape, numéroté, du départ au résultat. Colonne vertébrale du reste.]

## Écrans et états
[Par écran : son rôle en une ligne, puis vide / chargement / erreur / plein.]

## Règles métier
[Ce qui ne se voit pas à l'écran : droits, limites, calculs, conflits. RM-1...]

## Ce qu'on ne fait pas
[Explicite, avec la raison quand elle existe.]

## Dépendances et risques

## Questions ouvertes
[Question — qui tranche — d'ici quand.]
```

## Cahier des charges vs PRD

Two audiences, not two competing formats. Ask which is targeted if it isn't
obvious.

- **PRD (internal)**: the structure above. Oriented towards deciding and building.
- **Cahier des charges (external, vendor, tender)**: add contractual scope,
  expected deliverables, acceptance criteria, technical and legal constraints,
  schedule, and who owes what. The tone becomes binding: what's written can be
  held against you.

In both, the four states and the non-goals stay mandatory. A cahier des charges
describing only the nominal case produces an impossible acceptance phase and a
dispute.

## User stories

Separate file, `docs/produit/03-stories/<feature>.md` — the spec moves slowly,
stories move every sprint. Stable IDs, they'll be cited in commits and tickets.

```markdown
### US-012-03 — [titre court]
En tant que [rôle précis], je veux [action] afin de [bénéfice observable].

Critères d'acceptation
- Étant donné [contexte], quand [action], alors [résultat vérifiable]
- Étant donné [cas limite], quand [action], alors [résultat vérifiable]
- Étant donné [erreur], quand [action], alors [message et issue de secours]

Couvre : SPEC-012 §Parcours étapes 2-4, RM-3
Ne couvre pas : [ce qui est laissé à une autre story]
```

Three substantive requirements:

1. **The benefit is not the feature.** "afin de pouvoir filtrer" is worthless.
   "afin de retrouver une commande sans faire défiler 400 lignes" is verifiable.
2. **Every story has an error criterion**, or you ship the happy path.
3. **A story fits one iteration.** If it doesn't, split by vertical slice of
   value — a piece of the full flow — never by technical layer. "Le back du
   filtre" is not a story.

## Stay ahead of the engineer

Before declaring the spec ready, walk the eleven recurring engineering questions
in `7-questionnement.md` ("Devance l'ingénieur"): rights, data lifecycle, source
of truth, concurrency, volumes, third-party failures, existing-data migration,
i18n, GDPR, measurement event, rollout. Answer the ones that apply in the
relevant section; put the rest under "Questions ouvertes" with an owner. Never
invent an answer to a technical question you can't settle.

## Exit gate

Every screen has its four states; every story has at least one error criterion;
non-goals are written; no unsourced number without `[À VÉRIFIER]`; open
questions have owners. If something is missing, say so and offer to fill it now.
Don't ship a spec with a hole hoping construction will close it.
