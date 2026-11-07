VERDICT: OK

Fiche L13-T40, branche lot-13/L13-T40.

## Contrôles
- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 170 lignes pour 200 permises.
- Les 6 tests nommés passent. Stryker ciblé sur `compte-courant.ts` : 85,42 (seuil 80).
- Mutations à la main (seuil débiteur `<=`, lien vide accepté, tri retiré, doublon ignoré) : chacune rougit.
- Convention de signe en commentaire de tête et testée dans les deux sens. NaN, 1,5, ±Infinity, liste vide présents.
- Aucun mot interdit, aucun prix, données fictives. Journal : 6 lignes, en-tête correct.

## Remarques (non bloquantes)
- `packages/noyau/src/associes/compte-courant.ts:53` : le `type` du lien n'est pas vérifié ; un lien `{ type: 'autre', id: 'x' }` venu d'un JSON compte comme expliqué. Restreindre à `ecriture`, `piece`, `ligne_bancaire`.
- `compte-courant.ts:61` : la garde de dépassement du solde n'est pas couverte par un test (mutant survivant).
