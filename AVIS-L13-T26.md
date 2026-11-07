VERDICT: OK

Relecture de `lot-13/L13-T26` (9244aed) contre la fiche de `origin/main`.

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 259 lignes (max 260) ; compactage fait sur des lignes vides, aucun test ni assertion retiré.
- Les 10 tests nommés sont présents ; vitest 10/10 vert. Devises fictives (XXD, XXC, XXE), sources et personne inventées.
- Ordre parité, BCE (au plus `joursMax` jours avant), saisi : respecté ; la BCE n'est pas lue pour une parité en vigueur (accesseur piège).
- Cas limites : taux 0, -1, NaN, 1,5, ±Infinity, au-delà de l'entier sûr, chaîne ; `joursMax` NaN, -1, 1,5, Infinity ; dates invalides ; source vide ou blancs (422).
- `joursMax` en argument, aucun délai en dur ; garde:litteraux et garde:fictif vertes, eslint vert.
- Mutations (toutes rougissent) : fin d'effet incluse ; plancher BCE élargi ; 422 retiré ; `validationAutorisee` toujours vraie ; date du taux BCE remplacée par la date demandée.
- Journal : 6 lignes, commence par `# Journal L13-T26`.

## Remarques
- `taux.ts:66` : les dates `effetDebut`/`effetFin` et la `source` d'une parité ne sont pas contrôlées (la fiche demande une parité saisie avec source) ; contrôle à prévoir à la saisie de la parité.
- Marge de taille nulle (259/260) : toute correction devra rester compacte.
- Stryker et `pnpm verifier` non lancés par l'auteur : à confirmer par la CI. PR sensible : fusion par Will.
