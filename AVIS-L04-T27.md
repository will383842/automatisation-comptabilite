VERDICT: OK

Relu : classement/proposition.ts, __tests__/proposition.test.ts, fiche, journal (7 lignes). Diff relu contre le main fusionné dans la branche (0419a35) : seuls les 4 fichiers autorisés.
- 144 lignes (max 280) ; 9 tests nommés verts ; tsc, eslint, gardes textes / fictif / littéraux vertes.
- Statut toujours brouillon ; exemple trois taux : D 350,00, TVA 6,00 + 5,50 + 38,00, C 399,50 ; clé sha256:type ; comptes en arguments ; sommes par ajouter ; ecritures/modele.ts non modifié.
- Cas limites : taux 1.5, débordement MAX_SAFE_INTEGER, TTC 0, signes mêlés, parTaux vide : aucune exception, aucune: desequilibre ou vide.
- Mutations (statut propose, ligne TVA nulle gardée, sens non inversé, sensible ignoré) : toutes rougissent. Le retrait du contrôle Σ = TTC survit car verifierEcriture fait le même contrôle (mutant équivalent).

Remarques
- Rebase : origin/main a été réécrit (force-push, nouvelle racine) ; la branche n'a plus de base commune avec main. Diff relu contre sa base d'origine ; à rebaser sur le nouveau main avant la PR.
- proposition.ts:30 : le sens dépend du signe du TTC, pas du type. Une pièce de type avoir avec des montants positifs donnerait une charge et une TVA au débit. La fiche définit l'avoir par TTC négatif ; à couvrir en amont ou par une raison aucune dans une fiche suivante.
