VERDICT: OK

Relu : classement/typologie.ts, classement/mots-cles-types.ts, __tests__/typologie.test.ts, fiche, journal (9 lignes).
- Fichiers dans fichiers_autorises ; 180 lignes (max 280).
- 9 tests nommés + 2 tests ajoutés, verts ; tsc, eslint, gardes textes / fictif / littéraux vertes.
- Cas limites : NaN, Infinity, 0.5, nombre négatif, texte vide ou absent, « pouvoir » / « avoirs » sans déclenchement.
- Mutations (mot entier retiré, ttc < 0 devenu <= 0, > 1 devenu > 2, désaccord sans regle null) : toutes rougissent.
- Table comptée complète pour les 13 types ; plusieurs numéros = plusieurs_factures et à vérifier.

Remarques
- Rebase : origin/main a été réécrit (force-push, nouvelle racine) ; la branche n'a plus de base commune avec main. Diff relu contre sa base d'origine ; à rebaser sur le nouveau main avant la PR.
- mots-cles-types.ts:4, :8 et :10 : « avoir » (verbe courant) et « devis », « reservation » en mot seul enverront des factures ordinaires (« selon devis n° 12 ») en désaccord, donc À vérifier. Sens prudent, mais bruit probable : à surveiller sur le banc de pièces.
- typologie.ts:53 : ttc_nul_ht_non_nul masque desaccord_type (un seul motif) ; noté dans le journal.
