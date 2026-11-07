VERDICT: OK

Relecture Opus de `lot-15/L15-T25` (a3c83e1).

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`.
- Taille : 199 lignes (max 260).
- Les 10 tests nommés sont présents et passent (vitest, Node 22).
- Cas limites couverts : bornes 1/2/200/201, emoji compté pour 1, vide et espaces, espaces insécable et fine, montant au-delà de `MAX_SAFE_INTEGER` ignoré, point décimal refusé, 8 et 10 chiffres, entrées hostiles. Aucun `parseFloat` : le montant passe par `BigInt`.
- Bornes passées par l'appelant, rien en dur.
- Mutations faites à la main, toutes détectées : `padEnd` remplacé par `padStart`, contrôle du maximum retiré, retrait des diacritiques supprimé, préfixe remplacé par une égalité.
- Mots interdits, prix, données réelles : aucun (les « € » des tests sont des saisies de recherche). Journal : 5 lignes, il commence par `# Journal L15-T25`.

## Remarques
- `origin/main` a été réécrit : la branche n'a plus de base commune avec main. Il faut la rebaser avant la PR.
- `packages/noyau/src/recherche/requete.ts:63` : `correspondMot(texte, '', true)` rend vrai, car un mot vide est le préfixe de tout. Un garde `mot !== ''` serait plus sûr.
- `requete.ts:51` : `dernierEnPrefixe` vaut toujours vrai dès qu'il y a un mot. C'est cohérent avec RE-R1, mais le champ ne porte alors aucune information.
