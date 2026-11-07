VERDICT: OK

Relecture de `lot-02/L02-T45` (commit 3700b17) par le relecteur qualité.

## Vérifications
- Fichiers modifiés : tous dans `fichiers_autorises` ; taille 247 lignes ajoutées, 1 retirée (maximum 280).
- Les 9 tests nommés sont présents (T11-1 16 400, T11-2 10 400, T11-3 seuils 12 000 et 10 000, T11-4 20 600, T11-6) ; cas limites aucun compte, aucun flux, horizon 0, `NaN`, négatif, non entier, montants `NaN` ou non entiers, deux flux le même jour : présents.
- `horizonJours`, `seuilBas`, `ancienneteMaxJours` passés en argument ; aucune fonction `tresorerie` exportée (testé) ; dates en dur seulement dans les tests.
- Aucun mot interdit ni prix ; données fictives ; journal de 7 lignes commençant par `# Journal L02-T45`.
- vitest : 12 tests verts ; eslint et `tsc` du noyau propres ; gardes fictif, textes et tests vertes.
- Mutations faites à la main (toutes détectées) : alerte calculée sur le scénario demandé, `<` en `<=` sur le seuil, flux rapprochés gardés, avertissement d'ancienneté décalé d'un jour.

## Remarques
- `packages/noyau/src/banque/tresorerie/prevision.ts:75` : deux soldes du même `compteId` sont additionnés (pas de « dernier relevé » par compte), et deux flux de même `id` comptent deux fois. Dédoublonner ou refuser, vu l'objectif « sans double comptage ».
- Un solde daté après `aujourdhui` n'est pas refusé.
- Un dépassement de capacité dans `ajouter` lève `ErreurArgent`, pas `ErreurPrevision`.
