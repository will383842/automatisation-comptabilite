VERDICT: A CORRIGER

Relecture Opus de `lot-15/L15-T69` (b7062fd).

## Défauts
1. Taille dépassée : `git diff --numstat` donne 327 ajouts et 3 retraits, soit 330 lignes pour un maximum de 250. Correction : réduire le diff sous 250 lignes. Par exemple, une seule suite commune paramétrée au lieu de 8 fichiers `suite-<d>.ts` de 10 lignes (si la fiche le permet), commentaires et `void` superflus retirés dans les 21 fichiers de domaine. Sinon, faire relever `taille_max_lignes` dans la fiche par Will avant la PR.
2. Mot interdit : `pilotage/journal/L15-T69.md:6` contient une expression interdite par la règle 12 de CLAUDE.md (le mot « sans » suivi du mot « erreur », en fin de ligne après « tsc des 3 paquets »). Correction : écrire par exemple « tsc des 3 paquets passe ».
3. Branche à rebaser : `origin/main` a été réécrit et la branche n'a plus de base commune avec lui. De plus, `packages/contrat/src/routes.ts` et `apps/serveur/src/app.ts` ont changé sur main depuis la base de la branche. Il s'agit de fichiers communs à plusieurs lots : rebaser sur le main actuel, résoudre les conflits, puis relancer `pnpm verifier` et la suite commune sur les deux serveurs.

## Vérifié
- Périmètre : tous les fichiers sont dans `fichiers_autorises` ; `openapi.json` est inchangé.
- Les 3 tests nommés passent. La suite commune passe (42 tests et 16 `todo`), comme les tests du serveur (11).
- Mutations faites à la main, toutes détectées : `notifications` retiré de `contrat`, domaine `alertes` non vide.
- Journal : 6 lignes, il commence par `# Journal L15-T69`. Aucun prix, aucune donnée réelle.

## Remarques
- `packages/contrat/src/routes.ts:15` : la constante s'appelle `exports`, un nom qui évoque l'objet CommonJS. C'est valide en ESM ; `exportsDomaine` serait plus clair, mais la fiche impose le nom.
