VERDICT: OK

Relu : diff contre origin/main (4 fichiers, tous dans fichiers_autorises ; 250 lignes sur 250 au plus, pile à la limite), journal de 7 lignes.
Tests : vitest sur `src/juridique/__tests__/rapport-gestion.test.ts` donne 15/15 (8 tests nommés et 7 de plus).
Mutations, chacune rougit des tests : mode strict traité comme large, `>` remplacé par `>=` sur le nombre de seuils dépassés, exclusion d'activité ignorée, borne haute de `maxSeuilsDepasses` retirée, question « effectif » retirée.
Cas limites présents : NaN, Infinity, nombres non entiers, valeurs négatives, `bilan_negatif`, `maxSeuilsDepasses` hors 0 à 3, listes vides.
Aucun seuil, aucune forme ni activité en dur dans src.

## Remarques (non bloquantes)
- packages/noyau/src/juridique/rapport-gestion.ts:86-94 : la fiche demande cet ordre : forme, puis activité absente, puis exclusion, puis données manquantes. Le code vérifie l'exclusion d'abord, puis met la question « activite » en dernier dans la liste. Le résultat est le même pour une seule donnée manquante. À confirmer si l'ordre des questions compte pour l'écran.
- rapport-gestion.ts:91 : la condition `bilan === null || ca === null || effectif === null` sert seulement au typage ; elle fait doublon avec `questions.length > 0`.
- Stryker : 93,98 % selon le journal, non relancé ici. `pnpm verifier` n'a pas été lancé : le cloud tourne en Node 22.
