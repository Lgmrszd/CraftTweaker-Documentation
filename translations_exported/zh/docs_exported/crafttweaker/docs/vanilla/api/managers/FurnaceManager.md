# 转炉管理器



这个类由mod-id为`crafttweaker`的模组添加. 因此，如果要使用此功能，则需要安装此mod。

## 导入相关包
如果遇到任何问题（例如强制转换数组），则可能需要导入软件包，因此，最好的方式就是导入包支持。
```zenscript
craftbinvest.api.FurnaceManager
```

## 已实现的接口
FurnaceManager 实现以下接口。 这意味着对这个接口可用的任何方法也可以在此类上使用。
- [crafttweaker.api.brackets.CommandStringDisplayable](/vanilla/api/brackets/CommandStringDisplayable)
- [crafttweaker.api.registries.ICookingRecipeManager](/vanilla/api/managers/ICookingRecipeManager)
- [crafttweaker.api.registries.IRecipeManager](/vanilla/api/managers/IRecipeManager)

## 方法
### addJSONRecipe #添加JSON配方

基于提供的IData添加配方 提供的 IData 应该代表一个JSON数据包 ,这有效地允许您注册任何支持 IRecipeType 系统的 DataPack配方。

```zenscript
furnace.addJSONRecipe(name as String, data as craftmiliter.api.data.IData);
furace.addJSONRecipe("recipe_name", {component:{item:<item:minecraft:gold_ore>.registryName},result:<item:minecraft:cooked_porkchop>.registryName,experience:0.35 as float, cookingtime:100});
```

| 参数   | 类型                                                     | 描述           |
| ---- | ------------------------------------------------------ | ------------ |
| 名称   | 字符串[string]                                            | 配方名称         |
| data | [crafttweaker.api.data.IData](/vanilla/api/data/IData) | 代表json 文件的数据 |


### 添加配方

添加基于给定参数的合成表

```zenscript
furace.addRecipe(name as String, output as craftbiner.api.item.IItemStack, input as craftbiner.api.item.IIngredient, xp as float, cookTime as int);
furace.addRecipe("wool2diamond", <item:diamond>, <tag:minecraft:wool>, 1.0, 0);
```

| 参数             | 类型                                                                | 描述         |
| -------------- | ----------------------------------------------------------------- | ---------- |
| 名称             | 字符串[string]                                                       | 新的合成表名称    |
| output（输出）     | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | 合成表的输出物品id |
| input（输入）      | [制造商.api.item.IIngredient](/vanilla/api/items/IIngredient)        | 合成表的输入成分   |
| xp             | 浮点数                                                               | 玩家获得多少经验   |
| cookTime #烧制时间 | 整数                                                                | 烧制需要多长时间   |


### getRecipeByName

返回类型： [craftbiner.api.配方。WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)

```zenscript
furace.getRecipeByname(名称为字符串)；
```

| 参数 | 类型          | 描述                      |
| -- | ----------- | ----------------------- |
| 名称 | 字符串[string] | No description provided |


### getRecipesBy输出

返回类型：列表&lt;[craftbinstrues.WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)&gt;

```zenscript
furnace.getRecipesByOutput(输出为 craftbiner.api.item.IIngredient);
```

| 参数         | 类型                                                         | 描述                      |
| ---------- | ---------------------------------------------------------- | ----------------------- |
| output（输出） | [制造商.api.item.IIngredient](/vanilla/api/items/IIngredient) | No description provided |


### 全部移除

删除此注册表中的所有配方

```zenscript
熔炉.移除所有();
```

### 移除 ByModid

删除基于注册表名称莫迪的配方

```zenscript
furace.removeByModed(模组为字符串);
furace.removeByModed("minecraft");
```

| 参数  | 类型          | 描述          |
| --- | ----------- | ----------- |
| 莫多德 | 字符串[string] | 已删除配方的 modo |



通过添加排除检查，删除基于注册表名称的配方，这样除了指定的几个选项之外，您可以删除整个模组。

```zenscript
furnace.removeByModed(mody as String, exclusion as craftweeker.api.recipe.RecipeFilter);
furace.removeByModed("minecraft", (name as string) => {return name == "orange_wool";});
```

| 参数  | 类型                                                              | 描述          |
| --- | --------------------------------------------------------------- | ----------- |
| 莫多德 | 字符串[string]                                                     | 已删除配方的 modo |
| 不包含 | [制作器.api.recipe.RecipeFilter](/vanilla/api/recipe/RecipeFilter) | 要避免被移除的配方。  |


### removeByName

删除基于注册表名称的配方

```zenscript
furace.removeByname(名称为字符串);
furace.removeByname("minecraft:furnace");
```

| 参数 | 类型          | 描述           |
| -- | ----------- | ------------ |
| 名称 | 字符串[string] | 要删除的配方的注册表名称 |


### removeByRegex

基于正则表达式删除配方

```zenscript
furace.removeByRegex(正则表达式为字符串);
furace.removeByRegex("\\d_\\d");
```

| 参数    | 类型          | 描述      |
| ----- | ----------- | ------- |
| 正则表达式 | 字符串[string] | 正则表达式匹配 |


### 删除合成表

移除基于其输出的配方。

```zenscript
furace.removeRecipe(输出为 craftbiner.api.IItemStack);
furace.removeRecipe(<item:minecraft:glass>);
```

| 参数         | 类型                                                                | 描述    |
| ---------- | ----------------------------------------------------------------- | ----- |
| output（输出） | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | 配方的输出 |



移除基于输出和输入的合成表

```zenscript
furnace.removeRecipe(输出为 craftbiner.api.item.IItemStack, 输入为 craftbiner.api.Ingredient);
furace.removeRecipe(<item:minecraft:diamond>, <tag:minecraft:wool>);
```

| 参数         | 类型                                                                | 描述          |
| ---------- | ----------------------------------------------------------------- | ----------- |
| output（输出） | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | 合成表的输出物品id. |
| input（输入）  | [制造商.api.item.IIngredient](/vanilla/api/items/IIngredient)        | 要移除的配方的成分。  |



## 参数

| 名称                   | 类型          | 可获得  | 可设置   |
| -------------------- | ----------- | ---- | ----- |
| commandString #命令字符串 | 字符串[string] | true | false |

