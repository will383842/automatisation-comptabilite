VERDICT: OK

Relecture de `lot-13/L13-T28` (1034453) contre la fiche de `origin/main`.

- Périmètre : 4 fichiers, tous dans `fichiers_autorises` ; `index.ts` et `fr.ts` non touchés. Taille : 122 lignes (max 200).
- Les 6 tests nommés sont présents ; vitest 6/6 vert. Phrases exactes de R05, R08, R14, R17 et de la fiche reprises mot pour mot ; vouvoiement ; aucun pourcentage.
- 16 codes, liste écrite dans le test ; objet gelé (testé).
- garde:textes verte, garde:fictif verte, eslint vert ; aucun mot interdit en clair.
- Mutations (toutes rougissent) : texte `introuvable` modifié ; « et » en « ou » dans la mention de déclaration ; `Object.freeze` retiré.
- Journal : 6 lignes, commence par `# Journal L13-T28`.

## Remarques
- `messages.test.ts:25` : la liste est recopiée alors que `outils/gardes/textes.mjs` exporte `MOTS_INTERDITS` ; la copie omet `MOTS_INTERDITS_ENTIERS` (mots en entier). Importer les deux listes, ou recopier aussi la seconde, rendrait le test fidèle à la garde.
- Fiche non sensible (`sensible: non`), mais le diff touche `pilotage/` (fiche et journal de la PR seulement) : hors critère sensible.
