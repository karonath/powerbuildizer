# Reading grid — Laws of UX

From lawsofux.com (Jon Yablonski), also published in French at lawsofux.com/fr/.
Cognitive-psychology heuristics, not standards.

**How to use them.** A law shows where to look for a problem, never that you are
right. « Hick's law, donc on enlève trois options » is a disguised appeal to authority. « Il y a sept actions de poids égal ici, aucune
n'est visiblement principale — qu'est-ce qui se passe si on en promeut une et
qu'on range les autres ? » is an observation supported by the same law, and it stays
arguable. Cite two or three per critique at most, and only when they add
something to the raw observation.

## What the user already expects

| Law | What it predicts | When it helps |
|---|---|---|
| **Jakob** | Les gens passent leur temps ailleurs et attendent que ça marche pareil | Justifier une convention plutôt qu'une invention. L'originalité d'un parcours se paie |
| **Modèle mental** | Chacun agit selon l'idée qu'il se fait du système | Écart entre ce que fait le système et ce que la personne croit qu'il fait : source n°1 des erreurs |
| **Postel** | Sois permissif en entrée, strict en sortie | Formats de saisie : accepter un numéro avec des espaces, des tirets, en majuscules |

## Mental cost

| Law | What it predicts | When it helps |
|---|---|---|
| **Charge cognitive** | Les ressources mentales disponibles sont limitées | Le budget d'attention se dépense : demande-toi ce que coûte chaque élément |
| **Mémoire de travail / Miller** | Environ 7 ± 2 éléments retenus en mémoire de travail | Uniquement pour ce qu'il faut **mémoriser** d'un écran à l'autre. Pas pour compter des entrées de menu |
| **Chunking** | L'information groupée se traite mieux | Numéros, dates, longs formulaires : découper en blocs porteurs de sens |
| **Hick** | Le temps de décision croît avec le nombre et la complexité des choix | Choix réels et comparables. Une liste catégorisée qu'on balaie des yeux n'obéit pas à la même mécanique |
| **Surcharge de choix** | Trop d'options paralysent | Tarifs, listes de modèles : proposer un défaut recommandé |
| **Tesler** | Une part de complexité est irréductible et ne peut que se déplacer | Question à poser : qui la porte, l'utilisateur ou le système ? |
| **Rasoir d'Occam** | À prédiction égale, le moins d'hypothèses | Arbitrer entre deux conceptions équivalentes |
| **Attention sélective** | On ne voit que ce qui sert notre objectif | Explique pourquoi un bandeau important reste invisible |
| **Paradoxe de l'utilisateur actif** | Personne ne lit le manuel, tout le monde se lance | Tuto d'accueil, page d'aide : compte dessus et tu perds |

## Perception and gaze (Gestalt)

| Law | What it predicts |
|---|---|
| **Proximité** | Ce qui est proche est perçu comme lié — l'espacement dit la structure avant la couleur |
| **Région commune** | Une bordure ou un fond partagé crée un groupe plus fort que la proximité seule |
| **Similarité** | Ce qui se ressemble est perçu comme de même nature. Piège : un texte bleu non cliquable |
| **Connexité uniforme** | Ce qui est relié visuellement est perçu comme le plus lié de tous |
| **Prägnanz** | On interprète le complexe sous sa forme la plus simple |
| **Von Restorff** | Ce qui détonne est retenu — d'où : une seule action mise en avant, sinon aucune ne l'est |

## Speed and pointing

| Law | What it predicts | When it helps |
|---|---|---|
| **Fitts** | Le temps pour atteindre une cible dépend de sa taille et de sa distance | Actions fréquentes : grandes et proches. Complète le critère WCAG 2.5.8 sans le remplacer |
| **Seuil de Doherty** | La productivité décolle quand la machine répond en moins de 400 ms | Sert d'objectif de réactivité perçue ; le seuil mesuré côté conformité reste l'INP à 200 ms |

## Memory and felt experience

| Law | What it predicts | When it helps |
|---|---|---|
| **Pic-fin** | On juge une expérience sur son pic et sa fin | Soigner le moment le plus intense et le dernier écran, pas la moyenne |
| **Position sérielle** | On retient le premier et le dernier élément | Placement dans une navigation ou une liste |
| **Zeigarnik** | Ce qui est inachevé se retient mieux | Barres de progression, tâche reprise plus tard |
| **Gradient de but** | On accélère à l'approche du but | Montrer la progression, surtout en fin de parcours |
| **Esthétique-utilisabilité** | Le beau est perçu comme plus utilisable | À double tranchant : en test utilisateur, une belle maquette masque ses défauts d'usage |
| **Flow** | Immersion quand le défi égale la compétence | Outils experts : ne pas interrompre une tâche engagée |

## Prioritisation

| Law | What it predicts | When it helps |
|---|---|---|
| **Pareto** | 80 % des effets viennent de 20 % des causes | Identifier le parcours qui porte l'essentiel de l'usage |
| **Parkinson** | Le travail s'étale jusqu'à remplir le temps disponible | Découpage, échéances, périmètre |

## Traps

- **Une loi ne remplace pas un test.** Elle formule une hypothèse observable.
  Cinq personnes qui butent sur le même écran valent plus que n'importe quelle
  citation.
- **Miller n'a jamais parlé de menus.** Sept plus ou moins deux concerne ce
  qu'on mémorise, pas ce qu'on peut relire à l'écran.
- **Hick ne dit pas « moins d'options ».** Il dit que choisir coûte du temps.
  Catégoriser, ordonner et proposer un défaut réduisent ce coût sans amputer.
- **L'esthétique ne compense pas un parcours cassé**, elle retarde seulement le
  moment où on s'en aperçoit.
- **Ne cite jamais une loi seule.** Observation d'abord, loi ensuite si elle
  éclaire, correctif dans tous les cas.
