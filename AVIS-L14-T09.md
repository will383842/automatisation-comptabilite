VERDICT: A CORRIGER

Relu : diff contre origin/main (4 fichiers, tous dans fichiers_autorises ; 97 lignes sur 150 au plus), journal de 6 lignes. Les tests existants sont inchangés et `diviser` reste privée.
Tests : vitest sur `src/__tests__/argent.test.ts` donne 29/29.

## Défaut
- packages/noyau/src/__tests__/argent.test.ts:194-200 (`fraction-grand-produit-sans-perte`) : le test ne vérifie pas l'absence de perte.
  - Mutation faite : dans packages/noyau/src/argent/index.ts:103, le produit est calculé en flottant (`BigInt(Number(a) * Number(numerateur))`). Les 29 tests restent VERTS.
  - Cause : le cas 4000000000000001 × 7000000001 ÷ 7000000001 retombe juste même en flottant.
  - Correction demandée : ajouter un cas où le flottant se trompe, par exemple `expect(fraction(c(Number.MAX_SAFE_INTEGER), 3, 3, 'inferieur')).toBe(Number.MAX_SAFE_INTEGER)`. En flottant, ce calcul donne 9007199254740990.
  - Vérifier que ce cas rougit avec la mutation, puis l'annuler.

## Remarques
- Les autres mutations rougissent : dénominateur négatif accepté, argument non entier accepté, `verifier` retiré.
- Stryker et `pnpm verifier` n'ont pas été lancés : le cloud tourne en Node 22.
