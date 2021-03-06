# Gestionnaire de recettes ICooking

Interface par défaut pour les gestionnaires basés sur le Registre car ils peuvent tous supprimer des recettes par ResourceLocation.

Cette classe a été ajoutée par un mod avec le mod-id `crafttweaker`. Vous devez donc avoir ce mod installé si vous voulez utiliser cette fonctionnalité.

## Importation de la classe
Il pourrait vous être nécessaire d'importer le paquet si vous rencontrez des problèmes (comme lancer un tableau), alors mieux être sûr que désolé et ajouter l'importation.
```zenscript
crafttweaker.api.registries.ICookingRecipeManager
```

## Interfaces implémentées
ICookingRecipeManager implémente les interfaces suivantes. Cela signifie que toutes les méthodes disponibles peuvent également être utilisées dans cette classe.
- [crafttweaker.api.brackets.CommandStringDisplayable](/vanilla/api/brackets/CommandStringDisplayable)
- [crafttweaker.api.registries.IRecipeManager](/vanilla/api/managers/IRecipeManager)

## Méthodes
### addJSONRecipe

Ajoute une recette basée sur un IData fourni. L'IData fourni doit représenter un JSON DataPack, ce qui vous permet d'enregistrer des recettes pour tous les systèmes de DataPack prenant en charge IRecipeType.

```zenscript
furnace.addJSONRecipe(name as String, data as crafttweaker.api.data.IData);
furnace.addJSONRecipe("recipe_name", {ingredient:{item:<item:minecraft:gold_ore>.registryName},result:<item:minecraft:cooked_porkchop>.registryName,experience:0.35 as float, cookingtime:100});
```

| Paramètre | Type de texte                                          | Libellé                              |
| --------- | ------------------------------------------------------ | ------------------------------------ |
| Nom       | Chaîne de caractères                                   | nom de la recette                    |
| données   | [crafttweaker.api.data.IData](/vanilla/api/data/IData) | données représentant le fichier json |


### Ajouter une recette

Ajoute une recette basée sur des paramètres donnés.

```zenscript
furnace.addRecipe(name as String, output as crafttweaker.api.item.IItemStack, input as crafttweaker.api.item.IIngredient, xp as float, cookTime as int);
furnace.addRecipe("wool2diamond", <item:diamond>, <tag:minecraft:wool>, 1.0, 0);
```

| Paramètre        | Type de texte                                                               | Libellé                             |
| ---------------- | --------------------------------------------------------------------------- | ----------------------------------- |
| Nom              | Chaîne de caractères                                                        | Nom de la nouvelle recette          |
| Sortie           | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)           | IItemStack sortie de la recette     |
| input            | [format@@0 crafttweaker.api.item.Igredient](/vanilla/api/items/IIngredient) | Ingrédient de la recette            |
| xp               | flottant                                                                    | combien de xp le joueur obtient     |
| temps de cuisson | Indice                                                                      | combien de temps il faut pour cuire |


### getRecipeByName

Type de retour : [crafttweaker.api.recipes.WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)

```zenscript
furnace.getRecipeByName(name as String);
```

| Paramètre | Type de texte        | Libellé                    |
| --------- | -------------------- | -------------------------- |
| Nom       | Chaîne de caractères | Aucune description fournie |


### Obtenir des recettes par sortie

Type de retour : Liste&lt;[crafttweaker.api.recipes.WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)&gt;

```zenscript
furnace.getRecipesByOutput(sortie en tant que crafttweaker.api.item.Igredient);
```

| Paramètre | Type de texte                                                               | Libellé                    |
| --------- | --------------------------------------------------------------------------- | -------------------------- |
| Sortie    | [format@@0 crafttweaker.api.item.Igredient](/vanilla/api/items/IIngredient) | Aucune description fournie |


### Retirer tout

Supprimer toutes les recettes de ce registre.

```zenscript
Retirer tout ();
```

### Retirer par Modid

Supprimer la recette basée sur la modification du nom du Registre.

```zenscript
furnace.removeByModid(modifie en chaîne de caractères);
furnace.removeByModid("minecraft");
```

| Paramètre | Type de texte        | Libellé                           |
| --------- | -------------------- | --------------------------------- |
| modifier  | Chaîne de caractères | modifier les recettes à supprimer |



Supprimer la recette basée sur le nom du Registre modifié avec une vérification d'exclusion ajoutée, de sorte que vous pouvez supprimer l'ensemble du mod en plus de quelques spécifiés.

```zenscript
furnace.removeByModid(modid as String, exclude as crafttweaker.api.recipe.RecipeFilter);
furnace.removeByModid("minecraft", (name as string) => {return name == "orange_wool";});
```

| Paramètre | Type de texte                                                               | Libellé                                  |
| --------- | --------------------------------------------------------------------------- | ---------------------------------------- |
| modifier  | Chaîne de caractères                                                        | modifier les recettes à supprimer        |
| exclure   | [format@@0 crafttweaker.api.recipeFilter](/vanilla/api/recipe/RecipeFilter) | des recettes pour ne plus être enlevées. |


### removeByName

Supprimer la recette basée sur le nom du Registre.

```zenscript
furnace.removeByName(name as String);
furnace.removeByName("minecraft:furnace");
```

| Paramètre | Type de texte        | Libellé                       |
| --------- | -------------------- | ----------------------------- |
| Nom       | Chaîne de caractères | nom de la recette à supprimer |


### removeByRegex

Supprimer la recette basée sur la regex.

```zenscript
furnace.removeByRegex(regex as String);
furnace.removeByRegex("\\d_\\d");
```

| Paramètre | Type de texte        | Libellé                              |
| --------- | -------------------- | ------------------------------------ |
| regex     | Chaîne de caractères | regex pour faire correspondre contre |


### Supprimer la recette

Supprime une recette en fonction de sa sortie.

```zenscript
furnace.removeRecipe(output as crafttweaker.api.item.IItemStack);
furnace.removeRecipe(<item:minecraft:glass>);
```

| Paramètre | Type de texte                                                     | Libellé              |
| --------- | ----------------------------------------------------------------- | -------------------- |
| Sortie    | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | sortie de la recette |



Supprime une recette en fonction de sa sortie et de son entrée.

```zenscript
furnace.removeRecipe(affiche comme crafttweaker.api.item.IItemStack, entrée comme crafttweaker.api.item.IIngredient);
furnace.removeRecipe(<item:minecraft:diamond>, <tag:minecraft:wool>);
```

| Paramètre | Type de texte                                                               | Libellé                               |
| --------- | --------------------------------------------------------------------------- | ------------------------------------- |
| Sortie    | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)           | IItemStack sortie de la recette.      |
| input     | [format@@0 crafttweaker.api.item.Igredient](/vanilla/api/items/IIngredient) | Ingrédient de la recette à supprimer. |



## Propriétés

| Nom                | Type de texte        | A un Getter | A un Setter |
| ------------------ | -------------------- | ----------- | ----------- |
| Chaîne de commande | Chaîne de caractères | vrai        | Faux        |

