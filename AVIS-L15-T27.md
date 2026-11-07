VERDICT: OK

Relecture Opus de `lot-15/L15-T27` (7ea5cd6).

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`.
- Taille : 257 lignes (max 300).
- Les 11 tests nommés sont présents et passent (vitest, Node 22).
- Cas limites couverts : 33.5, NaN, ±Infinity, '30', null, tableau ; heures 24:00, 7:30, 07:60 ; doublons ; majuscule, chiffre, deux lettres, lettre accentuée (NFC et NFD) ; propriétés en trop ou manquantes ; clés `__proto__`, `constructor`, `toString`.
- Bornes 20 et 50 : constantes nommées, sans le mot « seuil ».
- Mutations faites à la main, toutes détectées : contrôle de doublon de lettre retiré, contrôle du nombre de propriétés retiré, heure 24 acceptée.
- Mots interdits, prix, données réelles : aucun. Journal : 7 lignes, il commence par `# Journal L15-T27`.

## Remarques
- `origin/main` a été réécrit : la branche n'a plus de base commune avec main. Il faut la rebaser avant la PR.
- `packages/noyau/src/preferences/valider.ts:97` : `lettresReservees` est facultatif et vaut `[]` par défaut. Un appelant qui l'oublie désactive sans bruit le contrôle des lettres réservées. La fiche en fait un argument fourni par l'appelant : mieux vaut le rendre obligatoire.
- `valider.ts:48` : les noms d'action de `remap` ne sont pas filtrés par une liste blanche. N'importe quelle clé est stockée, ce qui va contre l'esprit de « aucun champ caché ». À traiter quand la liste des actions sera fixée.
