VERDICT: OK

Relu : diff contre origin/main (4 fichiers, tous dans fichiers_autorises ; 140 lignes sur 220 au plus), journal de 6 lignes.
Tests : `node --test outils/gardes/test/registre-legal.test.mjs` donne 8/8 ; `node outils/gardes/registre-legal.mjs` est vert (93 fichiers).
Mutations, chacune rougit des tests : retrait du retrait des accents (5 rouges), retours à la ligne non normalisés (2 rouges), inclusion dans A ou B réduite au début (1 rouge), espaces non fusionnées (2 rouges).
Cas limites présents : fichier vide, BOM, espace insécable (ligne 36), A suivie de « registre légal » sur la même ligne (1 erreur).

## Remarques (non bloquantes)
- outils/gardes/test/registre-legal.test.mjs:22-23 : le cas BOM ne teste qu'un texte sans occurrence. Ajouter `'﻿' + MOT` qui doit donner `['x.md:1']`, et écrire le BOM en `﻿` plutôt qu'en caractère invisible.
- `pnpm verifier` n'a pas été lancé : le cloud tourne en Node 22.
