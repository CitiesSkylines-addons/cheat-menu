# Cheat Menu for Cities: Skylines 1

A local, toggleable helper mod based on the supplied feature list. Every boost starts **off**. Settings persist between sessions.

## Install / use

1. The built DLL belongs in:
   `%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\BigCityBoosts`
2. Install the bundled **Cities Harmony**, **81 Tiles 2**, and **Traffic Manager: President Edition** folders beside BigCityBoosts. Cheat Menu automatically enables these engine dependencies when it is enabled.
3. Start Cities: Skylines and enable **Cheat Menu** in Content Manager → Mods.
4. Fully restart the game after installing or updating, then load a city. Press **F9** to show or hide the draggable panel.
5. Toggle only the boosts you want.

The compact game-style panel uses a left category rail, dense single-line feature rows, subtle cyan enabled states, responsive sizing, an enabled-feature counter, **Builder preset**, and **Turn all off** controls. While the pointer is over the panel, mouse-wheel scrolling and movement are captured by the menu so the city camera does not zoom underneath it.

**Unlimited Raw Resources** lets oil pumps, ore/rock extractors, forestry buildings, and farm extractors operate on empty land. It generates the required resource beneath each extractor and keeps its outgoing raw-material buffer at 15,000 units.

**Max Workers** fills the actual `CitizenUnit` work slots used by commercial, industrial, office, and service buildings, so their info panels reach full staffing. Dedicated highly educated workers are created in throttled batches of 256 per simulation pass; the feature also clears worker-shortage timers and maintains full production. Because these are real simulation records, very large numbers of workplaces consume part of the game's citizen limit.

**Instant Construction** completes growing and newly placed buildings without waiting for their construction timer.

**Instant Level-Up** processes eligible zoned buildings in safe batches and rapidly upgrades them to the highest level for which the game has an appropriate building available.

**Unlimited Goods** fills the correct incoming buffer for commercial buildings, generic and specialized zoned industry, Industries processing facilities, and unique factories.

**Unlimited Warehouse Storage** gives every Industries DLC warehouse CS1's maximum safe capacity of 6,553,500 units. The real `WarehouseAI` capacity is changed, so warehouse percentages, transfer decisions, fill modes, and incoming-goods limits all use the larger amount. Switching the feature off restores each prefab's normal capacity. This control is locked when the Industries DLC is not owned.

DLC-only controls are detected automatically. **Unlimited Warehouse Storage** requires Industries, and **Max House Heating** requires Snowfall. When the needed expansion is not owned, the control displays **DLC**, stays disabled, and cannot remain active through saved settings or the Builder preset.

**U-Turns Everywhere** uses TM:PE's routing and junction-restriction system to permit U-turns at every compatible end of a two-way road. It continually handles newly constructed roads. Trams, monorails, trolleybuses, one-way exits, and heavy trucks still obey their engine safety restrictions.

**Instant Deliveries — No Trucks** keeps commercial buildings, generic and specialized zoned industry, Industries processing facilities, and unique factories supplied with raw materials, processed products, food, goods, and luxury products as appropriate. It also clears stale incoming-supply warnings, then removes only heavy `CargoTruckAI` delivery vehicles. Emergency, deathcare, garbage, maintenance, postal, public-transport, passenger, rail and service traffic is untouched. Disable the toggle to let cargo trucks spawn normally again.

**Maximum Land Value** directly maintains the maximum value in CS1's current and next LandValue simulation grids. This prevents the game's normal resource update from overwriting the boost and covers the full playable map.

**+1,000 Residential Capacity** adds 1,000 real household slots to every completed residential building. Existing and newly spawned homes are handled automatically in throttled batches of 250 units per simulation pass. These added slots remain in the save after the toggle is switched off and consume the game's global `CitizenUnit` pool, so use this especially large boost carefully in very large cities.

**Super Population Growth** keeps residential demand at 100 and fills vacant household slots with valid residents in throttled batches of 256 citizens per simulation pass. New households receive a balanced mix of adults, young adults, teens, and children. It works with normal homes as well as the additional slots created by **+1,000 Residential Capacity**.

**Full Map — All 81 Tiles** permanently unlocks the complete 9×9 map, including the outer ring beyond CS1's standard 25-tile purchase grid. It uses the maintained 81 Tiles 2 engine patches so terrain, zoning, districts, utilities, disasters and expanded save data work across the full map. Enabling this feature changes the save format; keep the dependencies enabled whenever loading a city that uses outer tiles.

The mod applies simulation changes on the game's simulation thread. Citizens are processed in batches to avoid a large frame spike in very big cities.

New buildings are handled immediately through the game's building-created event, so active electricity, water, sewage, heating, production, health, and happiness boosts also apply to newly constructed or spawned buildings. A fast periodic pass provides a fallback for upgrades and other state changes.

## Important behavior

- Turning a boost off stops enforcing it; already changed simulation values normalize as the game updates them.
- **Unlock Everything** permanently unlocks progression for the current save and cannot be reversed by switching the toggle off.
- Residential capacity already added to buildings is persistent; switching its toggle off only stops further additions.
- Residents created by Super Population Growth remain in the city after it is switched off; the toggle only stops accelerated move-ins and releases residential demand back to the normal simulation.
- Tiles claimed by Full Map are permanently unlocked in that save and cannot be reclaimed by switching the toggle off. Do not load an 81-tile city without its bundled dependencies.
- The Easy Build Preset intentionally leaves Rainy Weather and Unlock Everything off.
- Back up an important city before first use. Gameplay mods can permanently affect a save.

## Rebuild

Run:

```powershell
.\build.ps1 -Install
```

The script compiles against the assemblies in the locally installed Cities: Skylines 1 copy, using the Mono compiler shipped with the game.

## Full-map components

Full 81-tile support bundles [81 Tiles 2](https://github.com/algernon-A/EightyOne2) v1.0.5 by algernon (MIT license) and [Cities Harmony](https://github.com/boformer/CitiesHarmony) v2.2.2-0 by boformer. Traffic routing support bundles [Traffic Manager: President Edition](https://github.com/CitiesSkylinesMods/TMPE) v11.9.4.1 (MIT license). Their code and binaries remain under their respective licenses; license files are included where distributed.
