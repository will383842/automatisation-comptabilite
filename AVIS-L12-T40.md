VERDICT: OK

Relecture de `lot-12/L12-T40` (commit 78e38d4). Périmètre respecté (4 fichiers autorisés), 148 lignes pour 260 au plus, journal valide (6 lignes). Les 6 tests nommés sont verts et 4 mutations sur 4 sont tuées : contrôle de la graine retiré, résultat d'un m changé en OK, heure possible à 24, SIREN hors liste. Graine NaN, Infinity et 1,5 refusée. Les SIREN et les noms viennent de la liste fictive. Les horodatages sont en ISO UTC.

## Remarques
- `packages/donnees-fictives/src/catalogue-controles.ts:43-53` : des gravités ne suivent pas le catalogue réel (L12-T26). CC-K04, CC-K05 et CC-K06 sont M, pas `I` ou `m`. CC-K07 correspond à TVA-C01. Ce sont des données fictives, mais le faux serveur (L12-T41 à T44) s'en servira. Prendre des identifiants dont la gravité réelle est m (par exemple CC-K10 ou CC-K12H) et I éviterait de montrer une gravité fausse à l'écran.
- `catalogue-controles.ts:64` : `objetId` vaut `F-2026-…` même quand `objetType` est `paiement`. Ce n'est pas bloquant.
- Le CC-K01 `ECARTE` correspond à ce que demande la fiche (« B écarté non écartable »). Il faudra le garder comme cas de refus dans L12-T41 à T44.
