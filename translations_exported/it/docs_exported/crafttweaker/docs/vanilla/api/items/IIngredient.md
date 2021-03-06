# IIngrediente

Questo è IIngrediente!!!

Questa classe è stata aggiunta da una mod con ID `crafttweaker`. Perciò, è necessario avere questa mod installata per poter utilizzare questa funzione.

## Importare la classe
Potrebbe essere necessario importare il pacchetto, se si incontrano dei problemi (come castare un vettore), quindi meglio essere sicuri e aggiungere la direttiva di importazione.
```zenscript
crafttweaker.api.item.IIngredient
```

## Interfacce Implementate
IIngredient implementa le seguenti interfacce. Ciò significa che ogni metodo presente nell'interfaccia può essere usato anche per questa classe.
- [crafttweaker.api.brackets.CommandStringDisplayable](/vanilla/api/brackets/CommandStringDisplayable)

## Metodi
### anyDamage

Tipo di restituzione: [crafttweaker.api.item.MCIngredientConditioned](/vanilla/api/items/MCIngredientConditioned)&lt;[crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient)&gt;

```zenscript
<tag:ingotIron>.anyDamage();
```

### getRemainingItem

Quando questa pila di ingredienti è creata, cosa rimarrà nella griglia? Non controlla se lo stack corrisponde però! Usato, ad esempio, nella net.minecraft.item.crafting.ICraftingRecipe

Tipo di restituzione: [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)

```zenscript
<tag:ingotIron>.getRemainingItem(stack as crafttweaker.api.item.IItemStack);
<tag:ingotIron>.getRemainingItem(<item:minecraft:iron_ingot>);
```

| Parametro | Tipo                                                              | Descrizione                             |
| --------- | ----------------------------------------------------------------- | --------------------------------------- |
| pila      | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | La pila per fornire questo ingrediente. |


### corrispondenze

Lo stack dato corrisponde all'ingrediente?

Tipo restituito: booleano

```zenscript
<tag:ingotIron>.matches(stack as crafttweaker.api.item.IItemStack);
<tag:ingotIron>.matches(<item:minecraft:iron_ingot>);
```

| Parametro | Tipo                                                              | Descrizione             |
| --------- | ----------------------------------------------------------------- | ----------------------- |
| pila      | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | Lo stack da controllare |



Lo stack dato corrisponde all'ingrediente?

Tipo restituito: booleano

```zenscript
<tag:ingotIron>.matches(stack as crafttweaker.api.item.IItemStack, ignoreDamage as boolean);
```

| Parametro   | Tipo                                                              | Descrizione                            |
| ----------- | ----------------------------------------------------------------- | -------------------------------------- |
| pila        | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | Lo stack da controllare                |
| ignoreDanno | boolean                                                           | I danni dovrebbero essere controllati? |


### Solo Danneggiato

Tipo di restituzione: [crafttweaker.api.item.MCIngredientConditioned](/vanilla/api/items/MCIngredientConditioned)&lt;[crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient)&gt;

```zenscript
<tag:ingotIron>.onlyDamaged();
```

### onlyIf

Tipo di restituzione: [crafttweaker.api.item.MCIngredientConditioned](/vanilla/api/items/MCIngredientConditioned)&lt;[crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient)&gt;

```zenscript
<tag:ingotIron>.onlyIf(uid as String, function as function.Predicate<crafttweaker.api.item.IItemStack>);
```

| Parametro | Tipo                                                                                                    | Descrizione                 | IsOptional | Valore Predefinito |
| --------- | ------------------------------------------------------------------------------------------------------- | --------------------------- | ---------- | ------------------ |
| uid       | Stringa                                                                                                 | Nessuna descrizione fornita | falso      | `null`             |
| funzione  | function.Predicate&lt;[crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)&gt; | Nessuna descrizione fornita | vero       | `null`             |



## Proprietà

| Nome          | Tipo                                                                | Ha Getter | Ha Setter |
| ------------- | ------------------------------------------------------------------- | --------- | --------- |
| commandString | Stringa                                                             | vero      | falso     |
| elementi      | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)[] | vero      | falso     |

## Operatori
### O

```zenscript
<tag:ingotIron> <unk> altro come crafttweaker.api.item.IIngredient
```

| Parametro | Tipo                                                                | Descrizione                 |
| --------- | ------------------------------------------------------------------- | --------------------------- |
| altri     | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | Nessuna descrizione fornita |

## Caster

| Tipo Risultato                                             | Implicito |
| ---------------------------------------------------------- | --------- |
| [crafttweaker.api.data.IData](/vanilla/api/data/IData)     | vero      |
| [crafttweaker.api.data.MapData](/vanilla/api/data/MapData) | vero      |

