VERDICT: A CORRIGER

Relecture de `lot-12/L12-T38` (commit 3a7a3e4). Périmètre et taille respectés (93 lignes pour 260 au plus), journal valide, 6 tests nommés verts, 4 mutations tuées.

## Défauts

1. `packages/textes/src/controles/coherence.ts:18-28` : la plupart des messages décrivent un autre contrôle que celui de l'identifiant. Le sens réel des contrôles est donné par les fiches du noyau (spec 12, `02-controles-coherence`) :
   - CC-K05 = somme des lignes ≠ pied de facture (L12-T02), alors que le texte parle d'une facture en double ;
   - CC-K06 = montant dû ≠ TTC non qualifié (acompte, avoir, remise) (L12-T02), alors que le texte parle d'une date hors période ;
   - CC-K07 = TVA ≠ base × taux (TVA-C01, L12-T01), alors que le texte parle d'un fournisseur sans compte ;
   - CC-K08 = facture adressée à un autre que la société (L12-T03), alors que le texte parle d'un compte absent du plan ;
   - CC-K09 = numéro de TVA intracommunautaire invalide (L12-T04), alors que le texte parle d'un total ≠ lignes (c'est en fait CC-K05) ;
   - CC-K10 = vente à un particulier ou à un tiers inconnu (L12-T03), alors que le texte parle d'une rupture de numérotation ;
   - CC-K11 / CC-K11M = date de la pièce (période close, future, hors exercice) (L12-T05), alors que le texte parle de « pièces à vérifier » ;
   - CC-K12 / CC-K12H = nature douteuse (immobilisation, caution, hors activité) / écart avec la nature habituelle du fournisseur (L12-T06), alors que le texte parle d'un relevé bancaire.
   Correction demandée : récrire chaque phrase à partir de la description du contrôle dans la spec et dans la fiche du noyau qui le met en œuvre (L12-T01 à L12-T08, L01-T21). Garder les phrases de la spec déjà reprises (K04, K13, K14) et la formule de K02.
2. `packages/textes/src/controles/coherence.ts:15-16` : CC-K01 contrôle l'équilibre d'une écriture et CC-K02 celui de la balance de l'exercice (L01-T21). « Les écritures de ${nom} » (K01) et « Une écriture du ${date} » (K02) inversent presque les deux sens. À aligner sur la spec.
3. `packages/textes/src/controles/__tests__/coherence.test.ts` : ajouter dans `valeurs-inserees` une assertion par contrôle qui fixe un mot propre à son sens (par exemple « lignes » pour K05, « TVA intracommunautaire » pour K09). Sans cela, des phrases interverties passent tous les tests.

## Remarques
- `ValeursCoherence` rend les cinq champs obligatoires même pour les contrôles qui n'en utilisent aucun (K14). On peut l'accepter, mais un `Partial` par contrôle serait plus juste.
