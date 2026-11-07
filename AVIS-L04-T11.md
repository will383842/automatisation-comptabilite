VERDICT: OK

Relecture de `lot-04/L04-T11` (commit 26f47d5) par le relecteur qualité.

## Vérifications
- Fichiers modifiés : tous dans `fichiers_autorises` (conventions.ts, formats.ts, test, fiche, journal) ; taille 190 lignes ajoutées, 1 retirée (maximum 300).
- Les 10 tests nommés sont présents ; cas limites vide, `abc`, `1,2,3,4`, `NaN`, `Infinity`, plafond de l'entier sûr (positif et négatif), 29/02 sur 1900, 2000, 2028, année sur deux chiffres : présents.
- Aucun `parseFloat`, `toFixed` ni `/` ; conversion par `Number.parseInt` puis `centimes()` (qui ramène -0 à 0) ; aucune date littérale dans `src` ; les conventions sont des usages d'écriture, pas des valeurs légales.
- Aucun mot interdit ni prix ; données fictives ; journal de 7 lignes commençant par `# Journal L04-T11`.
- vitest : 10 tests verts ; eslint et `tsc` du noyau propres ; gardes fictif, textes et tests vertes.
- Mutations faites à la main (toutes détectées) : règle des siècles retirée de la bissextile, `>` en `>=` sur le plafond, ordre MJA ignoré, groupes de milliers de 1 à 3 chiffres acceptés.

## Remarques
- `packages/noyau/src/pieces/lecture/formats.ts:29` : blancs et `EUR` retirés partout (« 12 34,56 » est lu 1 234,56 ; « 1EUR2 » est lu 12). La fiche demande ce retrait ; à garder en tête pour L04-T13.
- `formats.ts:81` : « 1er avril 2026 » (usage français courant) et « 3 avril 26 » donnent `illisible`.
