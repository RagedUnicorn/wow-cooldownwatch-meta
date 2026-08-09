# CooldownWatch
&nbsp;  
![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/ragedunicorn_wow_banner.png)
&nbsp;  
_CooldownWatch aims to track your enemies cooldowns and making them visible to the player_

## Providers

[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/curseforge.svg)](https://www.curseforge.com/wow/addons/cooldownwatch)
[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/wago.svg)](https://addons.wago.io/addons/cooldownwatch)

## Source/Issues
[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/issues.svg)](https://github.com/RagedUnicorn/wow-classic-cooldownwatch/issues)
[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/source.svg)](https://github.com/RagedUnicorn/wow-classic-cooldownwatch)

## What is CooldownWatch?

In PvP the fight is often decided by cooldowns — who still has their escape, their interrupt, their trinket. CooldownWatch watches the combat log for those spells and shows you when your target used one and when it comes back up, so you no longer have to keep that timer in your head.

Everything is derived from the combat log, so there is nothing to configure before it works: CooldownWatch recognizes the spell, resolves the caster (including pets back to their owner), and starts counting down the cooldown on the Targetcooldownbar of that player. Switch targets and the bar follows, showing what that enemy has burned and what is still available to them.

## Features of CooldownWatch

* **Tracks enemy cooldowns from the combat log** — no addon required on the other side.
* **Per-target cooldown bar** that follows your current target and can be placed anywhere on screen.
* **A curated spell catalog** covering all nine classes plus racials, items and miscellaneous cooldowns — every entry verified against Wowhead, including all ranks of a spell.
* **Worst case handling** for enemies with talents or gear that shorten a cooldown, globally or per spell.
* **Manual cooldown overrides** per spell when you want the exact number yourself.
* **Pet cooldowns resolved back to their owner**, so a pet ability counts against the player who owns it.
* **Season aware** — Season of Discovery and TBC spells are applied on top of the base catalog for the branch you are playing.
* **Configuration profiles** with export/import for moving a setup between characters or sharing it.

### Cooldowns vs Proximity Cooldowns

Proximity cooldowns are cooldowns that were detected within a certain proximity but could not be matched to a caster. This means that we know that a certain spell was cast but we don't know by what player. It can however still be very helpful to see a notification about those spells. If the spell is specific to a class the player can often guess himself who cast the spell. Only if there are multiple enemy players with the same class it might get tricky to guess which one of them just used his cooldown.

## Configuration

CooldownWatch can be configured through the in-game interface options. Access the configuration by:

1. Opening the game menu (ESC key)
2. Selecting "Options"
3. Navigating to "AddOns"
4. Finding "CooldownWatch" in the list
&nbsp;  
Alternatively, you can use the slash command: `/cooldownwatch opt` or `/rgcw opt`

### Placing the Targetcooldownbar

Type `/rgcw conf enable` to bring an example Targetcooldownbar on screen and drag it wherever you like — as long as **Lock Targetcooldownbar** is disabled. `/rgcw conf disable` hides it again. Enable **Lock Targetcooldownbar** once you are happy with the position so it can no longer be moved by accident.

### Choosing what to track

Tracked cooldowns are grouped into categories — one per class (Priest, Rogue, Mage, Hunter, Warlock, Paladin, Druid, Shaman, Warrior) plus **Racials**, **Items** and **Misc**. Every spell can be enabled or disabled on its own, so you can narrow tracking down to the handful of cooldowns that actually matter to you.

Each spell also carries two per-spell settings:

- **Use worst case**: assume the enemy has the talents or gear that shorten this cooldown. The bar then counts down the shortest realistic cooldown instead of the base value.
- **Cooldown override**: manually set the tracked cooldown in seconds. It takes precedence over all worst case settings, and can only lower the tracked time — values above the base cooldown are capped.

**Assume worst case for all cooldowns** applies the worst case to everything at once. Worst case settings on individual cooldowns still take precedence.

### Profiles

CooldownWatch lets you save your configuration as named profiles, so you can switch between different setups or carry your settings to another character. Profiles are managed under the **Profiles** tab of the configuration interface.

A profile captures all of your CooldownWatch settings – which cooldowns are tracked per category, the per-spell worst case and cooldown override values, the *Assume worst case for all cooldowns* default, the lock state of the Targetcooldownbar and its on-screen position.

- **Save current as...**: Snapshots your current settings into a new named profile (or overwrites an existing one of the same name).
- **Apply**: Loads the selected profile and applies its settings. This overwrites your current settings and reloads the UI.
- **Rename**: Renames the selected profile.
- **Delete**: Removes the selected profile.

#### The Default Profile

Every character starts with a profile named **Default**. It holds CooldownWatch's shipped settings and is created automatically – you never have to save it yourself. It cannot be deleted, renamed or overwritten, so there is always a clean baseline to go back to: select **Default** and click **Apply** to reset CooldownWatch to its factory settings. The Rename and Delete buttons are greyed out while it is selected.

#### Sharing Profiles (Export / Import)

Profiles can be shared as portable strings, making it easy to copy a setup between characters or hand it to another player.

- **Export**: Generates a copy-pasteable profile string for the selected profile in the *Profile String* field.
- **Import**: Paste a profile string into the field and import it as a new profile. Imported strings are validated, so an invalid, corrupted, or non-CooldownWatch string is rejected without changing any of your settings.

> Note: Profiles are stored per character. Use export/import to move a profile to another character.

## Issues

[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/issues.svg)](https://github.com/RagedUnicorn/wow-classic-cooldownwatch/issues)

Wrong or missing spell data is the most common report and the most valuable one — the issue tracker has a dedicated **Spell Data Report** template for it.

## Source

[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/source.svg)](https://github.com/RagedUnicorn/wow-classic-cooldownwatch)

## FAQ

#### A cooldown counts down with the wrong duration. What now?

CooldownWatch ships the base cooldown of every spell it knows. If the enemy has a talent or item that shortens it, enable **Use worst case** for that spell (or **Assume worst case for all cooldowns** globally). If the number is still wrong, it is a data issue — open a GitHub Issue with the **Spell Data Report** template and it will be corrected in the spell catalog.

#### I get a red error (Lua Error) on my screen. What is this?

This is what we call a Lua error, and it usually happens because of an oversight or error by the developer (in this case me). Take a screenshot off the error and create a GitHub Issue with it, and I will see if I can resolve it. It also helps if you can add any additional information of what you were doing at the time and what other addons you have active. Additionally, if you are able to reproduce the error make sure to check if it still happens if you disable all others addons.
