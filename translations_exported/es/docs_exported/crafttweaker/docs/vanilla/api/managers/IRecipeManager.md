# Gestor de IReceta

Interfaz predeterminada para los manejadores basados en el Registro ya que todos pueden eliminar recetas por Resource Location.

Esta clase fue añadida por un mod con la ID  `crafttweaker`. Necesitas tener este mod instalado si quieres usar esta caracteristica.

## Importar la clase
Puede ser requerido que importes el paquete si encuentras algun problema (como crear un Array).
```zenscript
crafttweaker.api.registries.IRecipeManager
```

## Interfaces implementadas
IRecipeManager implementa las siguientes interfaces. Esto significa que cualquier método disponible también puede ser usado en esta clase.
- [crafttweaker.api.brackets.CommandStringMostrar](/vanilla/api/brackets/CommandStringDisplayable)

## Métodos
### addJSONRecipe

Añade una receta basada en un IData proporcionado. El IData proporcionado debe representar un JSON DataPack, esto le permite registrar recetas para cualquier DataPack que soporte sistemas IRecipeType.

```zenscript
craftingTable.addJSONRecipe(name as String, data as crafttweaker.api.data.IData);
craftingTable.addJSONRecipe("recipe_name", {ingredient:{item:<item:minecraft:gold_ore>.registryName},result:<item:minecraft:cooked_porkchop>.registryName,experience:0.35 as float, cooking kingtime:100});
```

| Parámetro | Tipo                                  | Descripción                           |
| --------- | ------------------------------------- | ------------------------------------- |
| nombre    | Cadena                                | nombre de la receta                   |
| datos     | [data.IData](/vanilla/api/data/IData) | datos que representan el archivo json |


### getRecipeByName

Tipo de devolución: [crafttweaker.api.recipes.WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)

```zenscript
craftingTable.getRecipeByName(nombre como cadena);
```

| Parámetro | Tipo   | Descripción                   |
| --------- | ------ | ----------------------------- |
| nombre    | Cadena | No se proporcionó descripción |


### Obtener recetas por salida

Tipo de retorno: Lista&lt;[crafttweaker.api.recipes.WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)&gt;

```zenscript
craftingTable.getRecipesByOutput(salida como crafttweaker.api.item.IIngredient);
```

| Parámetro | Tipo                                                                | Descripción                   |
| --------- | ------------------------------------------------------------------- | ----------------------------- |
| salida    | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | No se proporcionó descripción |


### eliminar todo

Eliminar todas las recetas de este registro

```zenscript
craftingTable.removeAll();
```

### eliminar por Modo

Eliminar receta basada en la modificación del nombre del registro

```zenscript
craftingTable.removeByModid(modid as String);
craftingTable.removeByModid("minecraft");
```

| Parámetro | Tipo   | Descripción                        |
| --------- | ------ | ---------------------------------- |
| modificar | Cadena | modificar las recetas para remover |



Quitar receta basada en la modificación del nombre del registro con una comprobación de exclusión añadida, por lo que puede eliminar todo el mod además de unos pocos especificados.

```zenscript
craftingTable.removeByModid(modid as String, excluye como crafttweaker.api.recipe.RecipeFilter);
craftingTable.removeByModid("minecraft", (nombre como string) => {return name == "naranja_lana";});
```

| Parámetro | Tipo                                                               | Descripción                            |
| --------- | ------------------------------------------------------------------ | -------------------------------------- |
| modificar | Cadena                                                             | modificar las recetas para remover     |
| excluir   | [crafttweaker.api.receta.Receta](/vanilla/api/recipe/RecipeFilter) | recetas para exluir de ser eliminadas. |


### removeByName

Eliminar receta basada en el nombre del registro

```zenscript
craftingTable.removeByName(nombre como cadena);
craftingTable.removeByName("minecraft:furnace");
```

| Parámetro | Tipo   | Descripción                                   |
| --------- | ------ | --------------------------------------------- |
| nombre    | Cadena | nombre de registro de la receta para eliminar |


### removeByRegex

Eliminar receta basada en regex

```zenscript
craftingTable.removeByRegex(regex as String);
craftingTable.removeByRegex("\\d_\\d");
```

| Parámetro | Tipo   | Descripción                    |
| --------- | ------ | ------------------------------ |
| regex     | Cadena | regex contra el cual emparejar |


### eliminar receta

Elimina una receta basada en su salida.

```zenscript
craftingTable.removeRecipe(output as crafttweaker.api.item.IIItemStack);
craftingTable.removeRecipe(<item:minecraft:glass>);
```

| Parámetro | Tipo                                                              | Descripción         |
| --------- | ----------------------------------------------------------------- | ------------------- |
| salida    | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | salida de la receta |



## Propiedades

| Nombre        | Tipo   | Tiene Obtén | Tiene Setter |
| ------------- | ------ | ----------- | ------------ |
| commandString | Cadena | verdad      | falso        |

