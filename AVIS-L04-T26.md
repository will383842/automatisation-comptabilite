VERDICT: A CORRIGER

Relu : classement/nom.ts, __tests__/nom.test.ts, fiche, journal (7 lignes). 150 lignes (max 220), fichiers autorisés, 8 tests verts, tsc, eslint et gardes vertes.

Défauts
1. packages/noyau/src/pieces/classement/nom.ts:39-41 : le nom peut dépasser longueurMax. Seul le fournisseur est coupé ; si numéro + date + montant ne tiennent pas, le fournisseur devient vide (« __ ») et le nom déborde. Mesuré : numéro de 170 caractères, longueurMax 180 → nom de 192 caractères. La spec (PCE-021) fixe « 180 caractères au plus ». Correction : après avoir réduit le fournisseur (en lui gardant au moins un caractère), couper aussi le numéro (et la devise si besoin), jamais la date ni le montant, pour que la longueur soit toujours <= longueurMax.
2. packages/noyau/src/pieces/classement/__tests__/nom.test.ts:47 : ce test fige le débordement (nom de 85 caractères pour longueurMax 40, fournisseur vide). Le remplacer par un test qui vérifie nom.length <= longueurMax, date et montant intacts, numéro coupé, aussi avec un numéro très long à 180.

Remarques
- Rebase : origin/main a été réécrit (force-push, nouvelle racine) ; la branche n'a plus de base commune avec main. Diff relu contre sa base d'origine ; à rebaser sur le nouveau main avant la PR.
- nom.ts:35 : datePiece n'est pas validée dans nomNormalise (« hier » donne « HIER_… ») alors que cheminVirtuel la refuse ; utiliser SANS-DATE pour une date non AAAA-MM-JJ.
- nom.ts:13 : DATE_ISO accepte un mois 13 (« 2026-13-45 » → 2026/13) ; réutiliser MOIS / JOUR déjà définis plus bas.
