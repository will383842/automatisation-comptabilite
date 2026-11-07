VERDICT: OK

Relecture Opus de `lot-15/L15-T29` (dda3758), fiche sensible (données personnelles).

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`.
- Taille : 258 lignes (max 260).
- Les 10 tests nommés sont présents et passent (vitest, Node 22).
- Cas limites couverts : -1, 1.5, NaN, ±Infinity, '10', null pour la durée ; horodatage en millisecondes, négatif, non entier ; non-objets ; `__proto__` ; secret de 31 et 32 octets (comptage en octets) ; `dureeMaxMs` invalide refusé.
- Liste blanche de 6 champs, événement rejeté jeté, index conservés. HMAC-SHA-256 par `node:crypto`. Le secret de test est visiblement fictif. Le mot proscrit par P4 n'apparaît pas.
- Mutations faites à la main, toutes détectées : contrôle `champ_inconnu` retiré, durée non ramenée au maximum, réglage d'installation ignoré, minimum du secret abaissé.
- Mots interdits, prix, données réelles : aucun. Journal : 7 lignes, il commence par `# Journal L15-T29`.

## Remarques
- `origin/main` a été réécrit : la branche n'a plus de base commune avec main. Il faut la rebaser avant la PR.
- `packages/noyau/src/usage/usage.ts:4` : 8 types seulement (la fiche dit « environ 30 », « au plus 30 »). C'est acceptable comme socle, à compléter avec les fiches d'écran.
