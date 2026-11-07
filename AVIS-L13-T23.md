VERDICT: OK

Relecture de `lot-13/L13-T23` (f024462) contre la fiche de `origin/main`.

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 244 lignes (max 260).
- Les 9 tests nommés sont présents ; vitest 9/9 vert. Table et règle inventées reprises de la fiche (dates attendues identiques).
- Critère « table-modifiee-change-le-resultat rougit si les dates sont figées » : vérifié (dates d'acompte figées sur une liste fixe, ce test rougit).
- Cas limites : 2027-02-30, chaîne vide, 2027-1-1 ; moisApres NaN, 1,5, Infinity, -1 ; jour 0, 32, 1,5, NaN ; fenêtre qui passe le 31/12.
- Aucune date AAAA-MM-JJ ni délai réel dans `src` ; garde:litteraux et garde:fictif vertes, eslint vert.
- Autres mutations (toutes rougissent) : fenêtre à cheval `||` en `&&` ; `table_ambigue` à partir de 3 ; exceptions ignorées ; `aVerifier` forcé à faux.
- Journal : 5 lignes, commence par `# Journal L13-T23`.

## Remarques
- `impot-societes.test.ts:89` : l'assertion sur les bornes (`bord`) accepte toute erreur autre que `fenetre_absente`/`table_ambigue` (par exemple `table_incoherente`) ; une valeur attendue exacte serait plus nette.
- `impot-societes.ts:85` : `decalageAnnees` négatif est accepté ; la fiche ne l'interdit pas.
- Stryker et `pnpm verifier` non lancés par l'auteur : à confirmer par la CI. PR sensible : fusion par Will.
