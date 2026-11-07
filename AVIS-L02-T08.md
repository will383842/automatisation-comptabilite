VERDICT: OK

Relecture de `lot-02/L02-T08` (commit aee102e) par le relecteur qualité.

## Vérifications
- Fichiers modifiés : tous dans `fichiers_autorises` (montants.ts, son test, fiche, journal).
- Taille : 194 lignes ajoutées, 1 retirée (maximum 260).
- Les 9 tests nommés sont présents ; cas limites `1e5`, `Infinity`, `NaN`, `--1`, `-0,00` (`Object.is(x, 0)`), espaces en tête et en queue, espaces insécables (U+00A0, U+202F) : présents.
- Aucun `parseFloat`, aucun littéral décimal, aucune valeur légale en dur ; données fictives ; aucun mot interdit ni prix.
- Journal : 5 lignes, commence par `# Journal L02-T08`.
- vitest : 40 tests verts ; eslint et `tsc` du noyau propres ; gardes fictif, textes et tests vertes.
- Mutations faites à la main (toutes détectées) : suppression du signe négatif, `>` en `>=` sur la limite, retrait de l'espace insécable, plafond des décimales à 3.

## Remarques
- `packages/noyau/src/banque/import/montants.ts:54` : le séparateur de milliers est accepté sans contrôle des groupes de 3 chiffres (« 1.2,00 » est lu 12,00 en format FR). À durcir dans une fiche ultérieure si besoin.
- `montants.ts:73` : le mode `suffixe_moins` fait exactement comme `signe` (le suffixe est déjà lu par `lireMontant`) ; acceptable.
- Deux tests nommés sont des `it.each` suffixés par `%j` : ils restent repérables par `-t`.
