VERDICT: A CORRIGER

Relecture de `lot-02/L02-T25` (commit 94ea1f8) par le relecteur qualité.

## Défauts bloquants (fuite de données vers l'IA)
1. `packages/noyau/src/banque/libelles/pseudonymiser.ts:14` (`IBAN_ESPACES`) : seuls les espaces ordinaires sont reconnus entre les groupes. Un IBAN découpé par espaces insécables (U+00A0 ou U+202F, fréquents dans les relevés PDF), par exemple `FR00 1234 5678 9012 3456 7890 123`, sort EN CLAIR. Correction : accepter tout blanc (`\s`, ou au moins `[   ]`) entre les groupes, et ajouter ce cas dans `iban-remplace-avec-et-sans-espaces`.
2. `pseudonymiser.ts:45` (groupe `CARTE`) : `[0-9x]{12,}` ne voit qu'une suite collée. Un numéro de carte écrit par groupes de 4, forme la plus courante (`CB 4974 1234 5678 1234`), sort EN CLAIR. Correction : accepter des groupes de 4 chiffres ou `X` séparés par un blanc (12 à 19 au total), et ajouter ce cas dans `carte-remplacee`.

## Vérifications faites
- Fichiers modifiés : tous dans `fichiers_autorises` ; taille 151 lignes ajoutées, 1 retirée (maximum 260).
- Les 8 tests nommés sont présents ; cas limites (textes vides, personne vide, nom contenu dans un autre, jeton écrit par un tiers échappé) : présents.
- IBAN des tests à clé `00` ; garde fictif verte ; aucun mot interdit ni prix ; journal de 5 lignes commençant par `# Journal L02-T25`.
- vitest : 8 tests verts ; eslint et `tsc` du noyau propres ; gardes fictif, textes et tests vertes.
- Mutations faites à la main (toutes détectées) : tri des noms inversé, échappement des jetons retiré, compteurs de la table existante ignorés, carte à 13 chiffres minimum.

## Remarques
- `retablir` n'est l'inverse exact que si l'original garde la même casse et les mêmes espaces : avec `Jean Dupont` dans les personnes, « jean dupont » écrit après « JEAN DUPONT » est rétabli en « JEAN DUPONT » ; un IBAN compact vu après sa forme espacée est rétabli avec espaces. C'est une limite de la table jeton vers original ; à écrire en commentaire ou à signaler au pilote.
- « DUPONT, JEAN » (avec virgule) n'est pas remplacé ; un IBAN à tirets non plus.
- Le groupe `CARTE` accepte plus de 19 chiffres (22 dans le test) : masquage en trop, sans danger.
