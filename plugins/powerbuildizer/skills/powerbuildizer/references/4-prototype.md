# Phase 4 — Prototype

A prototype is a decision instrument, not the start of a product. Success is
measured one way: do you now know something you didn't know before building it.

## The question first

Before writing a line, record the single question the prototype must answer.
Examples: « est-ce que l'utilisateur comprend qu'il doit d'abord choisir un
atelier ? », « est-ce que le tableau reste lisible avec 200 lignes ? ».

Without it, you build a pretty mockup and draw conclusions about people's taste
in colours.

## Rules

- **One flow**, the one from framing. No full menu, no side pages, no accounts.
- **Realistic data.** Never Lorem ipsum or "Client 1, Client 2". Real names are
  long, real lists are lopsided, real amounts are ugly — that's exactly where
  mockups break.
- **The four states visible**, with a cheap way to switch between them (debug
  buttons, URL parameter). A prototype showing only the nominal case tests
  nothing.
- **Throwaway and owned as such.** A standalone file in `docs/produit/proto/`,
  outside the product tree. No architecture, tests or performance concerns. If
  someone proposes shipping it, the answer is no.
- **Interactive on the critical path** at minimum: clicking must do something,
  even faked.

## Write-up

At the top of the file or in a neighbouring `README.md`, in French:

```markdown
# Proto — [nom] — [date]
Question : [la question unique]
Parcours couvert : [en une ligne]
Faux / simulé : [ce qui est en dur, pour ne pas se tromper sur l'état réel]
Ce qu'on a appris : [à remplir après l'avoir montré — c'est le vrai livrable]
```

The last line is the one that counts. A prototype where nobody filled in "ce
qu'on a appris" only filled an afternoon.
