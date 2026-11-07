VERDICT: OK

Relecture de `lot-13/L13-T12` (68b1d65) contre la fiche de `origin/main`.

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 191 lignes (max 220).
- Les 8 tests nommés sont présents (plus `montants-invalides-refuses`) ; vitest 9/9 vert.
- Cas limites : NaN, -1, 1,5, Infinity pour l'effectif ; égalité au seuil ; millésime vide et en double.
- Aucun seuil réel dans `src` (seuils en argument), garde:litteraux et garde:fictif vertes, eslint vert.
- Mutations (toutes rougissent) : `>` en `>=` sur le total de bilan ; `<` en `<=` sur le nombre de critères ; `aVerifier` limité à `a_verifier` ; borne `< 0` en `< -1`.
- Journal : 5 lignes, commence par `# Journal L13-T12`.

## Remarques
- `annexe-simplifiee.test.ts:54` : la valeur -1 n'est testée que pour l'effectif, pas pour les montants (totalBilan, chiffreAffaires). Ajout conseillé.
- `annexe-simplifiee.test.ts:47`, `:91`, `:96` : les `try/catch` sans `expect.assertions` ne rougissent pas si rien n'est levé (couvert ici par le `toThrow` qui précède).
- Stryker et `pnpm verifier` non lancés par l'auteur : à confirmer par la CI. PR sensible : fusion par Will.
