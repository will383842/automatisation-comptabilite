VERDICT: OK

Relecture Opus de `lot-15/L15-T21` (a8db373), fiche sensible.

- Périmètre : 4 fichiers, tous dans `fichiers_autorises`.
- Taille : 197 lignes (max 200).
- Les 9 tests nommés sont présents et passent (vitest, Node 22).
- Cas limites couverts : NaN, Infinity, -Infinity, 1.5, '12', '=1', 2 ** 60, bigint, dates invalides (30 février, 1900 non bissextile), vide, null/undefined, objet refusé (`type_invalide`).
- Mutations faites à la main, toutes détectées : retrait de U+FF0D de la liste, `isSafeInteger` remplacé par `isInteger`, borne d'année retirée, règle bissextile cassée.
- Mots interdits, prix, valeur légale en dur, données réelles : aucun. Journal : 7 lignes, il commence par `# Journal L15-T21`.

## Remarques
- `origin/main` a été réécrit : la branche n'a plus de base commune avec main (`git diff origin/main...` échoue). Il faut la rebaser sur le main actuel avant d'ouvrir la PR.
- `packages/noyau/src/exports/neutraliser.ts:23` : la fiche demande des caractères écrits en `\u…` ; ici ce sont des points de code hexadécimaux passés à `String.fromCodePoint`. L'effet est le même, mais on s'écarte de la lettre de la fiche.
- `booleen` : seuls `true` et `false` donnent un nombre ; les nombres `1` et `0` deviennent du texte. Lecture stricte, défendable, à confirmer.
