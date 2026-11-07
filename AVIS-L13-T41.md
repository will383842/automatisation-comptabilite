VERDICT: OK

Fiche L13-T41, branche lot-13/L13-T41.

## Contrôles
- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 198 lignes pour 200 permises.
- Les 6 tests nommés passent. Stryker ciblé sur `tns.ts` : 84,62 (seuil 80).
- Mutations à la main (montant nul accepté, sens de la régularisation inversé, contrôle du mois retiré) : chacune rougit.
- Comptes passés en argument, aucune date ni taux en dur dans `src`, statut toujours `brouillon`. Cas 0, −1, NaN, 1,5, Infinity, 2026-02-30 présents.
- Aucun mot interdit, aucun prix, données fictives. Journal : 6 lignes, en-tête correct.

## Remarques (non bloquantes)
- `packages/noyau/src/dirigeant/tns.ts:68` : retirer `verifierDate(demande.date)` dans `ecritureAppel` laisse les tests verts ; ajouter un appel à date d'écriture invalide dans `entrees-invalides`.
- `tns.ts:38` : retirer `^` ou `$` de l'expression de date laisse les tests verts ; ajouter `2026-12-05x` et `x2026-12-05` aux dates refusées.
