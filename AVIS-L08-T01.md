VERDICT: A CORRIGER

Relu : packages/noyau/src/rgpd/types.ts, packages/noyau/src/rgpd/__tests__/types.test.ts, fiche, journal (6 lignes). Périmètre et taille (178 lignes) respectés. 7 tests nommés verts ; 3 mutations tuées (borne 500, pluriel, date réelle).

## Défauts
1. packages/noyau/src/rgpd/types.ts:74-86 (`donneesPermises`) : la fiche demande de refuser toute clé qui **contient** `texte`, `nom`, `email`, `iban`, `montant` ou `contenu`. Le découpage par mots en camelCase et le test `endsWith` laissent passer les clés collées : `nompersonne`, `emailclient`, `NOMPERSONNE`, `textelibre`, `montantttc`, `nom1` sont toutes acceptées. Pour une garde RGPD, la lecture la plus stricte s'applique. Correction demandée : chercher le fragment en sous-chaîne dans la clé en minuscules, avec une courte liste d'exceptions explicite (au minimum `nombre`, pour que `nombrePieces` reste accepté comme l'exige la fiche).
2. packages/noyau/src/rgpd/__tests__/types.test.ts:59 : ajouter ces clés collées au test `evenement-sans-contenu-de-demande` (`nompersonne`, `emailclient`, `NOMPERSONNE`, `textelibre`), qui doivent rendre `valeur_interdite`.

## Remarques
- Critère « stryker >= 80 » non lancé par l'auteur (journal) : à vérifier en CI.
- `origin/main` a été réécrite (nouvelle racine) : la branche n'a plus de base commune avec `origin/main` (`git merge-base` vide). Rejouer les commits de la fiche sur l'actuel `origin/main` avant d'ouvrir la PR. Diff relu contre la base d'origine de la branche.
