# Pionero Capital – Save Game Editor

Unofficial, single-file (`editor-save-pionero.html`) save editor for the single-player game **Pionero Capital**. Everything runs in the browser; the save never leaves your computer.

## How to use
1. Close the game (and make sure no `java.exe` is left running).
2. Back up the slot folder: `%LOCALAPPDATA%\PioneroCapital\Saved\LocalServer\Slots\slotN\`.
3. Open the editor, load `savegame.gz`, change values, click **Export savegame.gz**.
4. Replace the `savegame.gz` in the same slot folder with the exported file.

Every change is re-parsed after export; the editor refuses to save if anything does not match ("Exported and verified OK").

## Tabs
- **Character**
  - Personal money, level (Citizen 1–29, with XP cap), experience, skill points, needs.
  - **Personal Permits**: tiers with dependency handling; optional skill-point charge/refund.
  - **Personal Vehicles**: repair, refuel, model, colour, cargo slots; add vehicles (limit = 1 + Personal Vehicle permits).
  - **Side Jobs**: Trucker and Lumberjack level (1–9) and XP.
- **Grants** (in-game achievements): grouped and named as in the game, with `claimed/total` per group. Counters can be edited, individual grants set to Claimable, and bulk buttons are available.
- **Company**: money, company level (Startup I … Monopoly) with XP cap, employees and skills. Employees are grouped by property (header such as `Grand Depot · 26/26`, employees/limit); sorting applies inside each group and moving an employee to another property regroups the list immediately.
- **Company vehicles**: list, repair, refuel, model, colour, cargo; add vehicles (limit 25). Grouped by property (`Iron Yard · 6 vehicles`). The save has no filled-in property field for vehicles, so the property is inferred from where the vehicle is parked (the same world cell as that building's employees). Vehicles not parked at a property appear under "Elsewhere".
- **Storage**: stock per item against shelf capacity, in one table grouped by property (`Grand Depot · 46 shelves`, with a per-property "Refill everything"). Below it, a separate **Warehouse manager shelves** block, grouped by property, to add or remove the shelves each manager looks after (experimental, see below).
- **Production & Sales**: production and sales editing.

## Tested in-game
- Grant completion via counters/status and claiming.
- Trucker and Lumberjack level 9 (level grants triggered and claimed).
- Character and company level changes (levels displayed correctly, grants triggered).
- Company vehicle edits and adding vehicles (also validated in the editor test suite).

## Not tested in-game yet
- Job levels 2–8.
- Whether level edits skip unlock rewards.
- Money-type grants in progress.
- Personal vehicle additions (same code path as company vehicles, tested in the editor only).
- **Manager shelves above 4**: the game only checks the 4-shelf limit when adding via the UI, so more shelves in the save may work; `server-8-estantes.jar` (limit patched to 8) is the alternative. Both are experimental.

## Notes
- Sending newly created company vehicles to a property (the game's recover mechanic) is not supported yet; new vehicles appear in front of the character.
- New vehicles need the character to have been saved standing outdoors; otherwise adding is disabled.
- Hidden or unknown fields are disabled rather than guessed. A game update may change the save format.
- Use at your own risk and keep backups.
