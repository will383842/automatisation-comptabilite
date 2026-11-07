VERDICT: OK

Relecture Opus de `lot-15/L15-T49` (8e7cf4a).

- Périmètre : 4 fichiers, tous dans `fichiers_autorises` ; `lecture.tsx` et `api.ts` ne sont pas touchés.
- Taille : 198 lignes (max 200).
- Les 7 tests nommés sont présents et passent (jsdom, `vi.useFakeTimers`, faux serveur `demarrerNoeud`).
- Cas limites couverts : intervalle 0, -1, NaN, ±Infinity (RangeError au premier rendu) ; préfixes vides ignorés ; erreur 4xx sans nouvelle tentative ; onglet caché.
- Même clé `['lecture', chemin]` et même `lire` que `useLecture`, même `EtatLecture`.
- Mutations faites à la main, toutes détectées : `refetchIntervalInBackground: true`, `refetchInterval` retiré, préfixe remplacé par une égalité, contrôle `<= 0` retiré.
- Mots interdits, prix, données réelles : aucun. Journal : 6 lignes, il commence par `# Journal L15-T49`.

## Remarques
- `origin/main` a été réécrit : la branche n'a plus de base commune avec main. Il faut la rebaser avant la PR.
- `apps/web/src/donnees/interrogation.ts:22-25` : la conversion en `EtatLecture` est recopiée depuis `useLecture` (`lecture.tsx`). Si l'une change sans l'autre, elles divergeront. Une fonction commune pourra venir plus tard, `lecture.tsx` étant hors périmètre ici.
