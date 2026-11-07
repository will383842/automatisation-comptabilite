VERDICT: OK

Fiche L13-T29, branche lot-13/L13-T29.

## Contrôles
- Périmètre : 4 fichiers, tous dans `fichiers_autorises`. Taille : 232 lignes pour 240 permises.
- Les 8 tests nommés passent (vitest ciblé). `garde:textes` verte.
- Mutations à la main (zéro-padding du taux, valeur absolue du montant, garde n > m, groupe de milliers) : chacune fait rougir au moins un test.
- Cas limites présents : NaN, 1,5, Infinity, date 2026-13-01, montant négatif. Aucun mot interdit, aucun prix, données fictives.
- Journal : 7 lignes, commence par `# Journal L13-T29`.

## Remarques (non bloquantes)
- `packages/textes/src/moteur/messages.ts:70` : `sens: 'aucun'` avec un montant non nul, ou `sens: 'perte'` avec un montant nul, passe en silence. Refuser l'incohérence (et ajouter un test) serait plus sûr.
