VERDICT: OK

Fiche L13-T36, branche lot-13/L13-T36.

## Contrôles
- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 151 lignes pour 220 permises.
- Les 7 tests nommés passent ; registre lu sans modification ; document sans `paths` testé.
- Mutations à la main : retrait d'un fragment, interrupteur ouvert accepté, paramètre de chemin traité comme requête : chacune rougit.
- Aucun mot interdit, aucun prix, données fictives. Journal : 6 lignes, en-tête correct.

## Remarques (non bloquantes)
- `packages/contrat/src/__tests__/routes-externes.test.ts:89` : le cas `Télétransmettre` contient déjà `transmettre` sans accent, donc la normalisation NFD n'est pas prouvée (remplacer `NFD` par `NFC` laisse les 7 tests verts). Ajouter un cas où l'accent est dans le fragment, par exemple `Publiér` ou `Notifiér`, ou un e-mail écrit `Émail`.
- `routes-externes.test.ts:11` : la classe de caractères `[̀-ͯ]` contient des diacritiques combinants bruts ; préférer `[̀-ͯ]`, plus lisible et sans risque d'être abîmé par un éditeur.
