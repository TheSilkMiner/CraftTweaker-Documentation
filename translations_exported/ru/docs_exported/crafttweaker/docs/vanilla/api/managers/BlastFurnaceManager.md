# BlastFurnaceManager



Этот класс был добавлен модом с mod-id `crafttweaker`. Так что если вы хотите использовать эту функцию, вам нужно установить этот мод.

## Импорт класса
Вам может потребоваться импортировать пакет, если вы столкнетесь с какими-либо проблемами (например, с заливкой массива), так что лучше быть в безопасности, чем извиняться и добавлять импорт.
```zenscript
crafttweaker.api.BlastFurnaceManager
```

## Implemented Interfaces
BlastFurnaceManager implements the following interfaces. That means any method available to them can also be used on this class.
- [crafttweaker.api.brackets.CommandStringDisplayable](/vanilla/api/brackets/CommandStringDisplayable)
- [crafttweaker.api.registries.ICookingRecipeManager](/vanilla/api/managers/ICookingRecipeManager)
- [crafttweaker.api.registries.IRecipeManager](/vanilla/api/managers/IRecipeManager)

## Methods
### addJSONRecipe

Adds a recipe based on a provided IData. The provided IData should represent a DataPack JSON, this effectively allows you to register recipes for any DataPack supporting IRecipeType systems.

```zenscript
blastFurnace.addJSONRecipe(название как строка, данные как crafttweaker.api.data.IData);
blastFurnace.addJSONRecipe("recipe_name", {ingredient:{item:<item:minecraft:gold_ore>.registryName},результат:<item:minecraft:cooked_porkchop>.registryName,experience:0.35 как плавательный, кулинарный время:100});
```

| Параметр | Тип                                                    | Description                     |
| -------- | ------------------------------------------------------ | ------------------------------- |
| name     | String                                                 | name of the recipe              |
| data     | [crafttweaker.api.data.IData](/vanilla/api/data/IData) | data representing the json file |


### addRecipe

Adds a recipe based on given params.

```zenscript
blastFurnace.addRecipe(name as String, output as crafttweaker.api.item.IItemStack, input as crafttweaker.api.item.IIngredient, xp as float, cookTime as int);
blastFurnace.addRecipe("wool2diamond", <item:diamond>, <tag:minecraft:wool>, 1.0, 0);
```

| Параметр | Тип                                                                 | Description                     |
| -------- | ------------------------------------------------------------------- | ------------------------------- |
| name     | String                                                              | Name of the new recipe          |
| output   | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)   | IItemStack output of the recipe |
| input    | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | IIngredient input of the recipe |
| xp       | float                                                               | how much xp the player gets     |
| cookTime | int                                                                 | how long it takes to cook       |


### getRecipeByName

Тип возврата: [crafttweaker.api.recipes.WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)

```zenscript
blastFurnace.getRecipeByName(название как строка);
```

| Параметр | Тип    | Description          |
| -------- | ------ | -------------------- |
| name     | String | Описание отсутствует |


### getRecipesByFrom

Тип возврата: Список&lt;[crafttweaker.api.recipes.WrapperRecipe](/crafttweaker/api/recipes/WrapperRecipe)&gt;

```zenscript
blastFurnace.getRecipesByOutput(выход как crafttweaker.api.item.IIngredient);
```

| Параметр | Тип                                                                 | Description          |
| -------- | ------------------------------------------------------------------- | -------------------- |
| output   | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | Описание отсутствует |


### removeAll

Remove all recipes in this registry

```zenscript
blastFurnace.removeAll();
```

### removeByModid

Remove recipe based on Registry name modid

```zenscript
blastFurnace.removeByModid(modid as String);
blastFurnace.removeByModid("minecraft");
```

| Параметр | Тип    | Description                    |
| -------- | ------ | ------------------------------ |
| modid    | String | modid of the recipes to remove |



Удалите рецепт на основе мода названия реестра с добавленной проверкой исключения, так что вы можете удалить весь мод кроме нескольких указанных модификаций.

```zenscript
blastFurnace.removeByModid(modid as String, exclude as crafttweaker.api.recipe.RecipeFilter);
blastFurnace.removeByModid("minecraft", (название как строка) => {return name == "orange_wool";});
```

| Параметр  | Тип                                                                      | Description                         |
| --------- | ------------------------------------------------------------------------ | ----------------------------------- |
| modid     | String                                                                   | modid of the recipes to remove      |
| исключить | [crafttweaker.api.recipe.RecipeFilter](/vanilla/api/recipe/RecipeFilter) | рецепты для exlude от быть удалены. |


### removeByName

Remove recipe based on Registry name

```zenscript
blastFurnace.removeByName(название как строка);
blastFurnace.removeByName("minecraft:furnace");
```

| Параметр | Тип    | Description                       |
| -------- | ------ | --------------------------------- |
| name     | String | registry name of recipe to remove |


### removeByRegex

Remove recipe based on regex

```zenscript
blastFurnace.removeByRegex(regex as String);
blastFurnace.removeByRegex("\\d_\\d");
```

| Параметр | Тип    | Description            |
| -------- | ------ | ---------------------- |
| regex    | String | regex to match against |


### removeRecipe

Remove a recipe based on it's output.

```zenscript
blastFurnace.removeRecipe(выход как crafttweaker.api.item.IItemStack);
blastFurnace.removeRecipe(<item:minecraft:glass>);
```

| Параметр | Тип                                                               | Description          |
| -------- | ----------------------------------------------------------------- | -------------------- |
| output   | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | output of the recipe |



Removes a recipe based on it's output and input.

```zenscript
blastFurnace.removeRecipe(output as crafttweaker.api.item.IItemStack, input as crafttweaker.api.item.IIngredient);
blastFurnace.removeRecipe(<item:minecraft:diamond>, <tag:minecraft:wool>);
```

| Параметр | Тип                                                                 | Description                          |
| -------- | ------------------------------------------------------------------- | ------------------------------------ |
| output   | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)   | IItemStack output of the recipe.     |
| input    | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | IIngredient of the recipe to remove. |



## Свойства

| Название      | Тип    | Имеет Getter | Имеет Setter |
| ------------- | ------ | ------------ | ------------ |
| commandString | String | true         | false        |

