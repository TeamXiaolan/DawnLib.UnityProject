# v0.1.0

Hello World!

## DawnLib

- Added registering content through `DawnLib`
- Added `WeightTable` and `CurveTable` so that weights can be updated dynamically in-game.
- Added `ITerminalPurchasePredicate` to allow some items to not be bought based on conditions.
  - `TerminalPurchaseResult.Success()`: Acts like normal
  - `TerminalPurchaseResult.Failed()`: Player is unable to purchase the item and a different terminal node is displayed. Also allows overriding the name in this state with `.SetOverrideName(string)`
  - `TerminalPurchaseResult.Hidden()`: Does not show up in `store`, and player is also unable to purchase the item.
- `ITerminalPurchase` interface for (currently only some) possible terminal purchases:
  - `ITerminalPurchasePredicate Predicate`: see above, set with `builder.SetPredicate(predicate)`
  - `IProvider<int> Cost`: allows cost to be easily updated, set with `builder.SetCost(int)` or `builder.SetCost(provider)`
- Removed `VanillaEnemies` and added `LethalContent`
- Added `tags`
- Allow registering new tilesets to dungeons
- Added `PersistentDataContainer`
- 

## DuskMod

**MIGRATING FROM CODEREBIRTHLIB:** 
You will need to remake your `Content Container`, `Mod Information` and content definitions. 
The general flow has not changed overall.

- Reworked `Content Container`:
  - `Entity Name` (from content definitions) and `Entity Name Reference` have been removed. Instead, content can just be referenced.
  - `Asset Bundle Name` is now a dropdown.
  - Button to dump all `NamespacedKey`s to a `.json` file to be used with the `TeamXiaolan.DawnLib.SourceGen` package.
- Added 4 types of `Achievements`: `Discovery`, `Instant`, `Stat`, `Parent`
- Content definitions can now apply `tags`
- Added `DuskModContent` for the `Achievement` registry.
- Moved `.RegisterMod()` from `CRLib` to `DuskMod`
- Added `DuskAdditionalTilesDefinition`
- Added 2 `DuskTerminalPredicate`s:
  - `ProgressivePredicate`: Allows for a shop item to be unlocked through progression
  - `AchievementPredicate`: Requires that the player purchasing the item has an achievement
- Added 1 `DuskPricingStrategy`:
  - **NOTE:** Setting a pricing strategy in a content definition *overrides* the price set in the config.
  - `DailyPricingStrategy`: Price of shop item changes as the quota progresses.

## Utilities / Misc

- Added `NetworkAudioSource`, `AssetBundleUtils`
- Removed `ExtendedLogging` and split it into `DebugLogSources` (yes this uses SoundAPI code)
