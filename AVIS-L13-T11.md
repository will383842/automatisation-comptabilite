VERDICT: OK

Relecture de `lot-13/L13-T11` (commit 26228ab). Périmètre respecté, 242 lignes pour 260 au plus, journal valide (5 lignes). Les 10 tests nommés et 2 tests en plus sont verts. Aucun numéro de compte n'est écrit en dur dans `src`. L'espion vérifie qu'il n'y a aucun appel à l'IA tant que les rangs 1 à 3 répondent. Le rang 4 reste `a_verifier`. Le cas « aucune source » ne rend aucun compte.

3 mutations sur 4 sont tuées : départage par le numéro de compte inversé, contre-passée retenue, IA en `sur`. Stryker lancé par le relecteur sur `rang.ts` : 91,61, au-dessus du seuil de 80.

## Remarques
- `packages/noyau/src/classement/rang.ts:70` : la mutation « garder la date la plus ancienne » au lieu de la plus récente survit. Aucun test ne met à égalité deux comptes qui ont chacun plusieurs pièces. Ajouter par exemple A [01-01, 05-01] contre B [03-01, 04-01] : le résultat attendu est A.
- `rang.ts:6` : le statut s'appelle `contre_passee`, alors que la fiche écrit `contre_passe`. Il faudra aligner le nom avec le type des pièces quand il existera.
- `rang.ts:54` : une date invalide n'est détectée que si les rangs 1 et 2 ne répondent pas. La fiche dit « Date invalide ou vide dans l'historique : ErreurClassement » sans condition. Valider l'historique dès l'entrée serait plus sûr.
- Les entrées `exercices.courant` et `exercice` ne sont pas contrôlées (NaN, Infinity, 1,5). Ce n'est pas dangereux, puisque ces pièces ne sont pas retenues, mais un refus codé suivrait mieux les règles du noyau.
- Le journal indique que `pnpm verifier` n'a pas été lancé. Il faudra le confirmer par la CI.
