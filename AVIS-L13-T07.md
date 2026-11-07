VERDICT: OK

Relecture de `lot-13/L13-T07` (commit 1dd2081). Fiche sensible : la fusion revient à Will. Périmètre respecté, 246 lignes pour 250 au plus, journal valide (7 lignes). Les 8 tests nommés sont verts. Aucune durée n'est écrite en dur dans `src` : la durée est passée en argument. Les trois instants de PRI-13-02 sont testés, ainsi que les bornes juste avant, juste à l'instant et juste après. NaN, ±Infinity, 1,5, une durée négative et une valeur au-delà de MAX_SAFE_INTEGER sont refusés. Le retour à fermé est accepté pour tout acteur, une tâche comprise. La file est triée et l'entrée n'est pas modifiée.

4 mutations sur 4 sont tuées : `<` changé en `<=` sur la durée, fermeture réservée aux acteurs habilités, filtre de la file inversé, borne de durée négative déplacée. Stryker indiqué par l'auteur : 91,94.

## Remarques
- Le passage d'ouvert à pilote est accepté pour une personne habilitée. La fiche ne l'interdit pas, mais ce cas mérite d'être confirmé quand la spec R20 sera relue.
- La branche part d'une base ancienne de `main` (b85d22c). Il faut la remettre à jour avant de fusionner.
