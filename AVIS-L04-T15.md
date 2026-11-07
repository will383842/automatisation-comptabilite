VERDICT: OK

Relu : packages/noyau/src/pieces/lecture/confiance.ts, __tests__/confiance.test.ts, fiche, journal (6 lignes).
- Fichiers dans fichiers_autorises ; 145 lignes (max 220).
- 9 tests nommés présents et verts (vitest ciblé) ; tsc, eslint, gardes textes / fictif / littéraux vertes.
- Cas limites : NaN, Infinity, 101, -1, 1.5, douteux >= sur, liste vide.
- Mutations à la main (contrôle échoué ignoré, >= devenu >, aucun critique = sur, douteux > sur) : toutes rougissent.
- Barème et seuils en arguments, ECHELLE_MAX seule sur sa ligne ; aucun mot interdit, aucun prix.

Remarques
- Rebase : origin/main a été réécrit (force-push, nouvelle racine) ; la branche n'a plus de base commune avec main. Diff relu contre sa base d'origine ; à rebaser sur le nouveau main avant la PR.
- confiance.ts:38 : une valeur hors échelle ou non entière donne « douteux » au lieu d'une erreur ; choix prudent, documenté dans le journal.
