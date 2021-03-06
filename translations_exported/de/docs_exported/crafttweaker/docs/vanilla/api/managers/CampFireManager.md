# CampFireManager



This class was added by a mod with mod-id `crafttweaker`. So you need to have this mod installed if you want to use this feature.

## Diese Klasse importieren
It might be required for you to import the package if you encounter any issues (like casting an Array), so better be safe than sorry and add the import.
```zenscript
crafttweaker.api.CampFireManager
```

## Implemented Interfaces
CampFireManager implements the following interfaces. That means any method available to them can also be used on this class.
- [crafttweaker.api.brackets.CommandStringDisplayable](/vanilla/api/brackets/CommandStringDisplayable)
- [crafttweaker.api.registries.ICookingRecipeManager](/vanilla/api/managers/ICookingRecipeManager)
- [crafttweaker.api.registries.IRecipeManager](/vanilla/api/managers/IRecipeManager)

## Methoden
### addJSONRecipe

Adds a recipe based on a provided IData. The provided IData should represent a DataPack JSON, this effectively allows you to register recipes for any DataPack supporting IRecipeType systems.

```zenscript
campfire.addJSONRecipe(name as String, data as crafttweaker.api.data.IData);
campfire.addJSONRecipe("recipe_name", {ingredient:{item:<item:minecraft:gold_ore>.registryName},result:<item:minecraft:cooked_porkchop>.registryName,experience:0.35 as float, cookingtime:100});
```

| Parameter | Type                                                   | Beschreibung                    |
| --------- | ------------------------------------------------------ | ------------------------------- |
| name      | String                                                 | name of the recipe              |
| data      | [crafttweaker.api.data.IData](/vanilla/api/data/IData) | data representing the json file |


### addRecipe

Adds a recipe based on given params.

```zenscript
campfire.addRecipe(name as String, output as crafttweaker.api.item.IItemStack, input as crafttweaker.api.item.IIngredient, xp as float, cookTime as int);
campfire.addRecipe("wool2diamond", <item:diamond>, <tag:minecraft:wool>, 1.0, 0);
```

| Parameter | Type                                                                | Beschreibung                    |
| --------- | ------------------------------------------------------------------- | ------------------------------- |
| name      | String                                                              | Name of the new recipe          |
| output    | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)   | IItemStack output of the recipe |
| input     | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | IIngredient input of the recipe |
| xp        | float                                                               | how much xp the player gets     |
| cookTime  | int                                                                 | how long it takes to cook       |


### getRecipeByName

Rückgabetyp: [craftweaker.api.recipes.WrapperRezept](/crafttweaker/api/recipes/WrapperRecipe)

```zenscript
campfire.getRecipeByName(Name als String);
```

| Parameter | Type   | Beschreibung            |
| --------- | ------ | ----------------------- |
| name      | String | No description provided |


### getRecipesByAusgabe

Retourentyp: Liste&lt;[crafttweaker.api.recipes.WrapperRezept](/crafttweaker/api/recipes/WrapperRecipe)&gt;

```zenscript
campfire.getRecipesByOutput(Ausgabe als crafttweaker.api.item.IIngredient);
```

| Parameter | Type                                                                | Beschreibung            |
| --------- | ------------------------------------------------------------------- | ----------------------- |
| output    | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | No description provided |


### removeAll

Remove all recipes in this registry

```zenscript
campfire.removeAll();
```

### removeByModid

Remove recipe based on Registry name modid

```zenscript
campfire.removeByModid(modid as String);
campfire.removeByModid("minecraft");
```

| Parameter | Type   | Beschreibung                   |
| --------- | ------ | ------------------------------ |
| modid     | String | modid of the recipes to remove |



Entfernen Sie Rezept basierend auf Registry-Name Modid mit einer zusätzlichen Ausschluss-Prüfung, so dass Sie die ganze Mod neben einigen angegebenen entfernt können.

```zenscript
campfire.removeByModid(modid as String, except as crafttweaker.api.recipeFilter);
campfire.removeByModid("minecraft", (name as string) => {return name == "orange_wool";});
```

| Parameter    | Type                                                                     | Beschreibung                   |
| ------------ | ------------------------------------------------------------------------ | ------------------------------ |
| modid        | String                                                                   | modid of the recipes to remove |
| ausschließen | [crafttweaker.api.recipe.RecipeFilter](/vanilla/api/recipe/RecipeFilter) | zu entfernende Rezepte.        |


### removeByName

Remove recipe based on Registry name

```zenscript
campfire.removeByName(Name als String);
campfire.removeByName("minecraft:furnace");
```

| Parameter | Type   | Beschreibung                      |
| --------- | ------ | --------------------------------- |
| name      | String | registry name of recipe to remove |


### removeByRegex

Remove recipe based on regex

```zenscript
campfire.removeByRegex(regex als String);
campfire.removeByRegex("\\d_\\d");
```

| Parameter | Type   | Beschreibung           |
| --------- | ------ | ---------------------- |
| regex     | String | regex to match against |


### removeRecipe

Remove a recipe based on it's output.

```zenscript
campfire.removeRecipe(Ausgabe als crafttweaker.api.item.IItemStack);
campfire.removeRecipe(<item:minecraft:glass>);
```

| Parameter | Type                                                              | Beschreibung         |
| --------- | ----------------------------------------------------------------- | -------------------- |
| output    | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack) | output of the recipe |



Removes a recipe based on it's output and input.

```zenscript
campfire.removeRecipe(output as crafttweaker.api.item.IItemStack, input as crafttweaker.api.item.IIngredient);
campfire.removeRecipe(<item:minecraft:diamond>, <tag:minecraft:wool>);
```

| Parameter | Type                                                                | Beschreibung                         |
| --------- | ------------------------------------------------------------------- | ------------------------------------ |
| output    | [crafttweaker.api.item.IItemStack](/vanilla/api/items/IItemStack)   | IItemStack output of the recipe.     |
| input     | [crafttweaker.api.item.IIngredient](/vanilla/api/items/IIngredient) | IIngredient of the recipe to remove. |



## Properties

| Name          | Type   | Has Getter | Has Setter |
| ------------- | ------ | ---------- | ---------- |
| commandString | String | true       | false      |

