VERDICT: OK

Relu : diff contre origin/main (5 fichiers, tous dans fichiers_autorises ; 211 lignes sur 300 au plus), journal de 6 lignes.
Tests : `node --test outils/gardes/test/formats.test.mjs` donne 9/9 ; `node outils/gardes/formats.mjs` est vert (19 formats, avertissements seulement).
Mutations, chacune rougit un test : saut de la règle « prevu dont le test existe », du contrôle de doublon, de l'erreur « niveau_test vide », du refus des espaces, de la règle 3 (code sans ligne).
Cas limites présents : fichier vide, ligne vide finale, CRLF, BOM, guillemets, espaces.

## Remarques (non bloquantes)
- outils/gardes/test/formats.test.mjs:27 et 28 : le BOM est écrit comme un caractère invisible dans la source ; écrire `'﻿'` pour le rendre lisible et éviter qu'un éditeur le retire.
- outils/gardes/formats.mjs:66-74 : `testsDuDepot` et `codesDuDepot` ne sont couverts par aucun test. Un nom de test qui contient une apostrophe entre guillemets doubles est coupé (exemple vu sur le dépôt : `rejouer la même clé ne crée qu\`). Les formes `it.each` et `test.skip` ne sont pas reconnues.
- Toutes les lignes sont en P7 / DEC-044 faute de spec dans le dépôt (le journal le signale) : à revoir quand chaque lot de format passera sa ligne à `actif`.
- `pnpm verifier` n'a pas été lancé : le cloud tourne en Node 22.
