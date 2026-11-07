VERDICT: OK

Fiche L13-T43, branche lot-13/L13-T43.

## Contrôles
- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 238 lignes pour 240 permises.
- Les 7 tests nommés passent. Stryker ciblé sur `ventilation.ts` : 82,98 (seuil 80). `repartir` réutilisé, pas réécrit.
- Mutations à la main (classe 4 acceptée, section inactive acceptée, somme non contrôlée, version non incrémentée) : chacune rougit.
- MOT81-1 (33 334 / 33 334 / 33 333) et MOT81-3 vérifiés ; avoir négatif ; poids NaN, 1,5, négatif, tous nuls.
- Aucun mot interdit, aucun prix, données fictives. Journal : 7 lignes, en-tête correct.

## Remarques (non bloquantes)
- `packages/noyau/src/analytique/ventilation.ts:122` : `ajouterVersion` n'exige pas que la ventilation porte sur la même ligne que l'historique ; un contrôle `ligneId` éviterait de mêler deux lignes.
