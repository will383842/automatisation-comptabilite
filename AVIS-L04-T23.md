VERDICT: OK

Relu : classement/doublons.ts, __tests__/doublons.test.ts, fiche, journal (7 lignes).
- Fichiers dans fichiers_autorises ; 189 lignes (max 300).
- 10 tests nommés + tests ajoutés (23 au total), verts ; tsc, eslint, gardes textes / fictif / littéraux vertes.
- Ordre respecté : niveau 1, puis numéros différents = aucun, puis niveaux 2 à 5. F-0201 / F-0202, 49,99, même jour, même texte : aucun.
- Cas limites : distanceImageMax NaN, Infinity, -1, 1.5 refusés ; distance NaN, -1, absente ; champs vides ; ordre inversé dans pieceDeReference.
- Mutations (règle des numéros retirée, <= devenu <, collision sans TTC connus, zéros de tête) : toutes rougissent.

Remarques
- Rebase : origin/main a été réécrit (force-push, nouvelle racine) ; la branche n'a plus de base commune avec main. Diff relu contre sa base d'origine ; à rebaser sur le nouveau main avant la PR.
- doublons.ts:50-52 : une pièce avec numéro et une sans numéro peuvent devenir doublon_sur (niveau 3) par fournisseur + date + TTC + heure. Cohérent avec la cascade, à garder en tête pour le cas ticket + facture.
- doublons.ts:55 : distanceImage non entière (2.5) acceptée ; pieceDeReference compare recueLe en texte (suppose un format ISO homogène en UTC).
