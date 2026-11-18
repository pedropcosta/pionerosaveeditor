# Pionero Capital – Save Game Editor

Unofficial, single-file (`editor-save-pionero.html`) save editor for the single-player game **Pionero Capital**. Everything runs in the browser; the save never leaves your computer.

## How to use
1. Close the game (and make sure no `java.exe` is left running).
2. Back up the slot folder: `%LOCALAPPDATA%\PioneroCapital\Saved\LocalServer\Slots\slotN\`.
3. Open the editor, load `savegame.gz`, change values, click **Export savegame.gz**.
4. Replace the `savegame.gz` in the same slot folder with the exported file.

Every change is re-parsed after export; the editor refuses to save if anything does not match ("Exported and verified OK").

## Features by tab

### Character
- Personal money, level (Citizen 1–29, with XP cap), experience, skill points
- Needs bar, with "Restore to full"
- **Personal Permits**
  - Unlock or remove tiers, with dependencies handled
  - Optional skill-point charge/refund
- **Personal Vehicles**
  - Repair, refuel, change model, colour, cargo slots (up to 48)
  - Add vehicles (limit = 1 + Personal Vehicle permits)
- **Side Jobs**
  - Trucker and Lumberjack level (1–9) and experience

### Grants
- Grouped and named as in the game, with `claimed/total` per group
- Edit counters and set individual grants to Claimable
- Bulk buttons to complete several grants at once

### Company
- Company money, level (Startup I … Monopoly) with XP cap, experience
- Employees grouped by property (`Grand Depot · 26/26`)
  - Change property, skill level, salary and inventory slots
  - Bulk "set all to" for level and inventory slots
  - Sorting applies inside each group
- Add new employees to a property (within its limit)

### Company vehicles
- Grouped by property (`Iron Yard · 6 vehicles`)
  - Property is inferred from where the vehicle is parked (the save has no filled-in property field)
  - Vehicles not at a property appear under "Elsewhere"
- Repair, refuel, change model and colour, cargo slots
- Bulk actions: select all damaged / to refuel, change model of all
- Add company vehicles (limit 25)

### Storage
- Stock per item against shelf capacity, in one table grouped by property
- Refill per item or "Refill everything" per property
- **Warehouse manager shelves** (separate block, grouped by property)
  - Add or remove the shelves each manager looks after
  - Beyond the game's limit of 4 is experimental

### Production & Sales
- Read-only: summary cards and charts of units sold vs. produced per day, per item (nothing is edited here)

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
