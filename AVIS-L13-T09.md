VERDICT: A CORRIGER

Relecture de `lot-13/L13-T09` (commit 547f80e). Périmètre respecté, taille de 200 lignes pour 200 au plus (limite atteinte), journal valide. Les 7 tests nommés sont verts. 3 mutations sur 4 sont tuées : tri des clés, NaN seul au lieu de « non fini », détection de cycle.

## Défauts

1. `packages/noyau/src/principes/parite.ts:48` : `!(k in a) || !(k in b)` lit aussi la chaîne des prototypes. Une clé présente d'un seul côté et dont le nom est une propriété d'`Object.prototype` (`constructor`, `toString`, `valueOf`, `hasOwnProperty`…) n'est pas signalée comme absente : la fonction compare alors la valeur avec la fonction héritée. Reproduit : `differences({ constructor: 1 }, {})` lève `ErreurParite('valeur_non_serialisable')` au lieu de rendre `['constructor']`.
   Correction demandée : utiliser `Object.hasOwn(a, k)` et `Object.hasOwn(b, k)`, puis ajouter l'assertion `expect(differences({ constructor: 1 }, {})).toEqual(['constructor'])` dans `autre-champ-differe`. Pour rester sous 200 lignes, compacter une assertion existante sans en retirer aucune.

## Remarques
- La mutation `return sortie.sort()` → `return sortie` survit, car `comparer` produit déjà les chemins dans l'ordre. Le tri reste lexicographique : `l[10]` passe avant `l[2]`. La fiche demande seulement une liste « triée », ce qui est donc acceptable. Il faudra le préciser si l'ordre numérique des indices est voulu.
- La branche part d'une base ancienne de `main`. Il faut la remettre à jour avant de fusionner.
