VERDICT: OK

Relecture de `lot-02/L02-T46` (commits b03e0d7 et 9bc5b98) par le relecteur qualité.

## Vérifications
- Fichiers modifiés : tous dans `fichiers_autorises` ; taille 231 lignes ajoutées, 1 retirée (maximum 240).
- Les 8 tests nommés sont présents (T13-1 : 2 factures, 3 200,00, 1 alerte) ; cas limites liste vide (total 0), reste nul exclu, reste `NaN`, négatif, non entier, `Infinity`, horizon `NaN`, négatif, non entier : présents.
- Aucune fonction `payer` ; `horizonJours` en argument ; IBAN seulement hachés ; total par `ajouter`.
- Aucun mot interdit ni prix ; données fictives ; journal de 6 lignes commençant par `# Journal L02-T46`.
- vitest : 17 tests verts ; eslint et `tsc` du noyau propres ; gardes fictif, textes et tests vertes.
- Mutations faites à la main (toutes détectées) : escompte du jour même refusé, horizon exclusif, reste nul gardé, facture à IBAN changé laissée dans la liste.

## Remarques
- `packages/noyau/src/banque/fournisseurs/a-payer.ts:68` : un seul IBAN connu par fournisseur (le dernier de la liste l'emporte) ; un fournisseur avec deux IBAN légitimes déclencherait une fausse alerte.
- `a-payer.ts:79` : une facture dont l'escompte est encore valable mais dont l'échéance dépasse l'horizon n'est pas listée ; l'escompte peut être perdu.
- Les dates `aujourdhui`, `echeance` et `escompteJusquau` ne sont pas validées.
