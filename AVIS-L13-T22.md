VERDICT: OK

Relecture de `lot-13/L13-T22` (dedce98) contre la fiche de `origin/main`.

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 239 lignes (max 240).
- Les 7 tests nommés sont présents (plus `compte-manquant-refuse` et `retenues-nulles-sans-ligne-organismes`) ; vitest 9/9 vert.
- Valeurs MOT87-1/2/3 reprises en centimes ; écritures en `brouillon`, jamais `valide` ; aucun numéro de compte ni taux dans `src`.
- Cas limites : -1, NaN, 1,5, Infinity sur chaque montant ; statut inconnu (y compris `toString`).
- garde:litteraux et garde:fictif vertes, eslint vert.
- Mutations (toutes rougissent) : `charges !== 0` en `>= 0` ; `!==` en `<` sur la cohérence de paie ; statut `propose` ; borne `< 0` en `< -1`.
- Journal : 6 lignes, commence par `# Journal L13-T22`.

## Remarques
- `remuneration.ts:55` : un montant nul (prélèvement 0, rémunération 0, brut 0) laisse une écriture sans ligne, refusée par `verifierEcriture` avec une `ErreurEcriture` et non une `ErreurDirigeant`. La fiche ne tranche pas ce cas ; à préciser dans une fiche suivante (code dédié ou liste vide).
- Code `compte_manquant` ajouté hors fiche : utile, il est testé.
- Stryker et `pnpm verifier` non lancés par l'auteur : à confirmer par la CI. PR sensible : fusion par Will.
