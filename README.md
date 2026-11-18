# Pionero Capital Save Game Editor

A browser-based editor for **Pionero Capital** save files.

> **Unofficial tool, for testing purposes only.** Made with Claude. Not affiliated with or endorsed by the developers of Pionero Capital. Editing a save can break it, so always keep a backup of your save slot folder and use it at your own risk.

## How to use

- Close the game and make sure no `java.exe` is left running.
- Back up your save slot folder in `%LOCALAPPDATA%\PioneroCapital\Saved\LocalServer\Slots` (`slot0`, `slot1`, …).
- Open the editor and drop in the slot's `savegame.gz`.
- Change the values you want. Every change is listed under **Save Changes**.
- Click **Export savegame.gz**. The editor re-reads the exported file and checks every change before it confirms.
- Replace the `savegame.gz` in the same slot folder with the exported file.
- Everything runs locally in your browser; the save file never leaves your computer.

## Features

### Character
- Personal money, experience and skill points
- Needs level, with a button to restore it to full
- Personal permits: unlock or remove by tier, individually or all at once
- Optional skill point charge and refund for permit changes

### Company
- Company money and experience
- Employees:
  - Skill level (1 to 3), individually or for everyone at once
  - Property assignment (only properties that accept the role and have free places)
  - Salary, with − / + buttons in steps of 10
  - Inventory slots (6 to 10), individually or for everyone at once
  - Sortable table, grouped by property and role by default
- Add employees by property, role, gender, skill level and quantity
- Employee count per property as an `x/y` bar, with free slots

### Vehicles
- Repair (engine and body) and refuel to a full tank
- Change colour (21 colours)
- Change model, for one vehicle or for all company or personal vehicles
- Cargo slots, up to 48
- Add personal or company vehicles, with permit and company limits applied

### Storage
- Stock vs. capacity per item and per property, with a fill bar
- Refill an item, or everything in a property, to its shelf capacity
- Stack sizes: consumables 12, products 6, packed items 1

### Sales
- Summary: orders created, delivered and pending, backlog in days, revenue
- Units sold vs. produced per day, for all packed products or one item
- Orders delivered per day
- Resources per packed product: sold, daily rate, pending, stock, days of cover, box and product stock
- Sortable by any column

## Notes

- Employee inventory slots have been checked in the game: changed employees show and use the new number of slots.
- Built for the current version of the game. An update may change the save format; if a field cannot be found, the editor disables it instead of guessing.
- The save does not record daily order arrivals, only the running total, so past daily backlog cannot be reconstructed.
- Stock counts only what is on storage shelves, not items in vehicles, hands or workshops.
- The only external request is the Inter typeface, loaded from Google Fonts.
