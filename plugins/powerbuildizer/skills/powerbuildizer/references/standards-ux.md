# UX standards — the bar

Two kinds of rule here, don't conflate them. The numeric thresholds come from
verifiable standards: don't invent them, don't round them, and re-check them if
the date below is more than a year old. The rest is owned opinion, meant to be
replaced by the user's.

Sources last verified: September 2026.

## Accessibility — reference framework and legal obligation

**The reference is WCAG 2.2 level AA** (W3C recommendation since October 2023).
It is backward-compatible with 2.1, minus criterion 4.1.1 Parsing, now obsolete.
Targeting 2.1 today means targeting the previous version.

What's most often missing, because these are the criteria added in 2.2:

| Criterion | Level | Requirement |
|---|---|---|
| 2.5.8 Taille de cible (minimum) | AA | 24 × 24 px CSS, ou espacement suffisant : aucun cercle de 24 px de diamètre centré sur une cible n'en chevauche un autre |
| 2.4.11 Focus non masqué | AA | L'élément qui a le focus n'est pas entièrement caché par un en-tête collant, un bandeau cookies, une infobulle |
| 2.5.7 Mouvements de glissement | AA | Tout glisser-déposer a une alternative en simple pointeur |
| 3.3.8 Authentification accessible | AA | Pas de test cognitif obligatoire : le collage du mot de passe reste possible, pas d'énigme ni de mémorisation imposée |
| 3.2.6 Aide cohérente | A | L'accès à l'aide est au même endroit d'une page à l'autre |
| 3.3.7 Saisie redondante | A | On ne redemande pas une information déjà donnée dans le même parcours |

The 2.1 baseline stays whole: contraste 4.5:1 pour le texte courant et 3:1 pour le
texte large et les composants d'interface ; tout ce qui se fait à la souris se
fait au clavier ; focus visible ; la couleur ne porte jamais seule une
information ; alternative textuelle pour les images porteuses de sens.

44 × 44 px is criterion 2.5.5, level AAA. Not an AA obligation, but still the
right target on mobile for primary actions: 24 px is a compliance floor, not a
comfort goal.

**The legal obligation, in Europe.** L'European Accessibility Act s'applique
depuis le 28 juin 2025, transposé en France par la loi DDADUE n° 2023-171. Il
vise notamment le e-commerce, les services bancaires aux particuliers, les
communications électroniques, le transport de voyageurs, les médias
audiovisuels et les livres numériques. Les micro-entreprises (moins de 10
salariés et moins de 2 M€ de chiffre d'affaires) en sont exemptées. La période
transitoire jusqu'en 2030 concerne les services reposant sur des produits
physiques — bornes, terminaux de paiement — et non les sites et applications :
un site e-commerce existant est concerné depuis juin 2025.

Consequence for this skill: **ask early whether the product falls under the
EAA**, and record it in `ETAT.md`. If it does, accessibility stops being a
negotiable quality requirement and becomes a compliance constraint — that
changes the trade-off, and it's said before the spec, not after delivery. In
France, the usual evaluation framework is the RGAA.

## Perceived performance — Core Web Vitals

The three "good" thresholds, measured at the 75th percentile of real users over
a rolling 28 days (field data, not a Lighthouse score on your machine):

- **LCP ≤ 2.5 s** — the largest visible element is painted.
- **INP ≤ 200 ms** — response to an interaction, across the whole session.
  Replaced FID in March 2024; any rule still mentioning FID is stale.
- **CLS ≤ 0.1** — no layout shift.

Raise these at spec time, not at optimisation time: INP is the most commonly
failed of the three and is decided by JavaScript architecture, not by an
end-of-project tweak. Likewise CLS is avoided by reserving dimensions for
images, video and dynamic blocks from the mockup onwards.

## The four states, always

No screen is specified, critiqued or prototyped until all four are handled.

- **Vide (empty)** — first time, or nothing left to show. Best place to explain what
  the page is for and offer the first action. An empty state saying « Aucune
  donnée » wastes the opportunity.
- **Chargement (loading)** — under 300 ms show nothing: a flash is worse than
  the wait. Beyond that, a skeleton of the final shape rather than a spinner,
  which also serves CLS.
- **Erreur (error)** — says what happened, what the person can do, and never
  loses what they had typed.
- **Plein (full)** — and its forgotten cousin, overflow: 1 result, 10,000
  results, an 80-character name, a negative value, right-to-left text.

## Wording (keep all user-facing strings in French)

- Un libellé de bouton dit ce qui va se passer : « Envoyer l'invitation », pas
  « Valider ». « OK » ne veut rien dire sur une action destructive.
- Les erreurs ont une cause et une issue : « Ce fichier fait 40 Mo, la limite est
  25 Mo » plutôt que « Fichier invalide ».
- Pas de vocabulaire interne à l'écran. Si l'équipe dit « entité » et que
  l'utilisateur dit « client », l'écran dit client.
- Les confirmations destructives nomment l'objet : « Supprimer la facture
  2026-114 ? » et non « Êtes-vous sûr ? ».

## Load and friction

- One primary action per screen. If there are two, one is secondary: decide which.
- Every form field justifies itself to the person filling it. Nothing already
  entered is asked again (criterion 3.3.7).
- Don't make the user decide what you can derive.
- Every interaction acknowledges immediately, even when the result takes longer.
- Every destructive action is undoable, or confirmed. Not both: undo beats a
  confirmation people end up clicking without reading.
