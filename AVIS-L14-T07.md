VERDICT: OK

Relu : diff contre origin/main (4 fichiers, tous dans fichiers_autorises ; 178 lignes sur 180 au plus), journal de 4 lignes.
Tests : vitest sur `src/sources/__tests__/connecteurs.test.ts` donne 9/9 (6 tests nommés et 3 de cas limites).
Mutations, chacune rougit des tests : `>=` remplacé par `>` au seuil de dégradation (3 rouges), seuils égaux acceptés (1 rouge), jour antérieur accepté (1 rouge), seuil non entier accepté (1 rouge), date impossible acceptée (1 rouge).
Cas limites présents : seuils NaN, nuls, négatifs, non entiers et Infinity ; seuils incohérents ; jour mal formé ; nom de connecteur vide.
Aucune valeur en dur : les seuils sont des arguments.

## Remarques (non bloquantes)
- Stryker et `pnpm verifier` n'ont pas été lancés : le cloud tourne en Node 22.
