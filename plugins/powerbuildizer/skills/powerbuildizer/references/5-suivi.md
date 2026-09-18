# Phase 5 — Tracking

`docs/produit/ETAT.md` is the project's source of truth: the first file read at
the start of any session, any phase, by any agent. Keep it short by
construction — past two screens it stops being read.

## Format (French, as shown)

```markdown
# État — [projet]
Mise à jour : AAAA-MM-JJ

## Contexte produit
Type : [SaaS B2B / outil interne / grand public / ...]
Utilisateurs : [qui, en une ligne]
Stade : [idée / premiers utilisateurs / production]
Parcours principal : [une phrase]
Champ EAA : [oui / non / à vérifier]

## Où on en est
[3 à 5 lignes en prose. Ce qui est fait, en cours, bloqué. Pas une liste de
tâches : le récit qu'on ferait à quelqu'un qui revient de trois semaines.]

## Décisions prises
| Date | Décision | Pourquoi | Trace |

## Questions ouvertes
| Question | Qui tranche | Pour quand |

## Risques
| Risque | Impact | Ce qu'on fait |

## Fichiers
[Liens vers cadrages, specs, stories, critiques, avec leur statut.]
```

## Discipline

- **Update it at the end of every phase**, not "when there's time". A stale
  `ETAT.md` is worse than none: people trust it.
- **Only the main thread (N0) writes to it.** No sub-agent touches it, or it
  becomes a log of competing drafts.
- **A structural decision becomes an ADR** in `docs/produit/decisions/`:
  context, options considered, decision, accepted consequences. One page. What
  you want back in six months isn't the decision, it's what was known when it
  was made.
- **Open questions always have a name next to them.** Without an owner, a
  question isn't open, it's abandoned.

## At session start

Read `ETAT.md`, then open with a short point: where things stand, what moved,
and the most urgent call to make. Not an exhaustive summary — the person knows
their project, they need the thread back, not their own history.
