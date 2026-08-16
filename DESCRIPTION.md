# CooldownWatch
&nbsp;  
![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/ragedunicorn_wow_banner.png)
&nbsp;  
_CooldownWatch aims to track your enemies cooldowns and making them visible to the player_

## Providers

[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/curseforge.svg)](https://www.curseforge.com/wow/addons/cooldownwatch)
[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/wago.svg)](https://addons.wago.io/addons/cooldownwatch)

## What is CooldownWatch?

In PvP the fight is often decided by cooldowns - who still has their escape, their interrupt, their trinket. CooldownWatch watches the combat log for those spells and shows you when your target used one and when it comes back up, so you no longer have to keep that timer in your head.
&nbsp;  
![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/cooldownwatch_target_cooldown_bar.png)
&nbsp;  
Everything is derived from the combat log, so there is nothing to configure before it works: CooldownWatch recognizes the spell, resolves the caster (including pets back to their owner), and starts counting down the cooldown on the Targetcooldownbar of that player. Switch targets and the bar follows, showing what that enemy has burned and what is still available to them.

CooldownWatch supports World of Warcraft Classic Era and TBC Anniversary, including Hardcore and Season of Discovery.

## Features of CooldownWatch

* **Tracks enemy cooldowns from the combat log** - no addon required on the other side.
* **Per-target cooldown bar** that follows your current target and can be placed anywhere on screen.
* **Proximity cooldown window** listing the active cooldowns of every enemy around you - not just your target.
* **Friendly cooldown tracking** (opt-in) that shows teammate cooldowns on the target bar and in a window of their own, scoped to your party or raid.
* **A curated spell catalog** covering all nine classes plus racials, items and miscellaneous cooldowns - every entry verified against Wowhead, including all ranks of a spell.
* **Worst case handling** for enemies with talents or gear that shorten a cooldown, globally or per spell.
* **Manual cooldown overrides** per spell when you want the exact number yourself.
* **Pet cooldowns resolved back to their owner**, so a pet ability counts against the player who owns it.
* **Season aware** - Season of Discovery and TBC spells are applied on top of the base catalog for the branch you are playing.
* **Configuration profiles** with export/import for moving a setup between characters or sharing it.

## Configuration

CooldownWatch can be configured through the in-game interface options. Access the configuration by:

1. Opening the game menu (ESC key)
2. Selecting "Options"
3. Navigating to "AddOns"
4. Finding "CooldownWatch" in the list
&nbsp;  
Alternatively, you can use the slash command: `/cooldownwatch opt` or `/rgcw opt`

### Positioning the bar and windows

Every surface is positioned through its own button in the options: **Position Bar** on the Options panel for the Targetcooldownbar, **Position Window** on the Proximity Cooldowns and Friendly Cooldowns panels for the two windows. The button fills the surface with example cooldowns and makes it draggable - drag it where you want it and click **Apply**. Outside this mode nothing can be moved by accident, so there is no lock to manage. The Targetcooldownbar's size is adjusted with the **Bar scale** slider on the same Options panel.

For the Targetcooldownbar, `/rgcw conf enable` brings up the same example preview directly and `/rgcw conf disable` hides it again.

### Choosing what to track

![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/cooldownwatch_cooldown_selection.png)
&nbsp;  
Tracked cooldowns are grouped into categories - one per class (Priest, Rogue, Mage, Hunter, Warlock, Paladin, Druid, Shaman, Warrior) plus **Racials**, **Items** and **Misc**. Every spell can be enabled or disabled on its own, so you can narrow tracking down to the handful of cooldowns that actually matter to you. Each category panel carries an **Enemy** and a **Friendly** tab - the same spell list, configured separately per side, so what you track on enemies is independent of what you track on teammates.

Each spell also carries two per-spell settings:

![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/cooldownwatch_worst_case_override.png)
&nbsp;  
- **Use worst case**: assume the enemy has the talents or gear that shorten this cooldown. The bar then counts down the shortest realistic cooldown instead of the base value.
- **Cooldown override**: manually set the tracked cooldown in seconds. It takes precedence over all worst case settings and accepts any value up to 60 minutes - above the base cooldown too, for when you know the enemy's real cooldown better than the addon does.

**Assume worst case for all cooldowns** applies the worst case to everything at once. Worst case settings on individual cooldowns still take precedence.

### Proximity Cooldowns

The Targetcooldownbar only ever shows your current target. The **Proximity Cooldown Window** lists the active cooldowns of every other enemy around you - one row per cooldown with the spell, the caster's name and the remaining time, newest on top. Your current target is excluded, since its cooldowns are already on the bar.
&nbsp;  
![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/cooldownwatch_proximity_cooldown_window.png)
&nbsp;  
The window is opt-in and configured on the **Proximity Cooldowns** panel: **Hide long cooldowns** keeps cooldowns above 60 seconds out of the window (enabled by default - long cooldowns rarely decide the next engagement), the **Window scale** and **Maximum displayed cooldowns** sliders control its size, and **Reset to Defaults** restores every setting including the window position.

### Friendly Cooldowns

CooldownWatch can watch your own side too. **Track Friendly Cooldowns** tracks friendly players and their pets the same way enemies are tracked - your own cooldowns are excluded. Two displays build on it, each with its own toggle:
&nbsp;  
![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/cooldownwatch_friendly_cooldowns.png)
&nbsp;  
- **Show Friendly Target Cooldowns** shows a targeted teammate's tracked cooldowns on the Targetcooldownbar.
- **Enable Friendly Proximity Cooldown Window** opens a second proximity window for friendly cooldowns, with a **Scope** filter (your group, your raid, or all tracked players) and the same hide-long, scale and size options as the enemy window.

Which spells are tracked per side is chosen on the **Friendly** tab of each category panel.

### Profiles

CooldownWatch lets you save your configuration as named profiles, so you can switch between different setups or carry your settings to another character. Profiles are managed under the **Profiles** tab of the configuration interface.
&nbsp;  
![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/cooldownwatch_profile_configuration.png)
&nbsp;  
A profile captures all of your CooldownWatch settings - which cooldowns are tracked per category and side, the per-spell worst case and cooldown override values, the *Assume worst case for all cooldowns* default, the friendly tracking flags, the proximity window options, and the scale and on-screen position of every surface.

- **Save current as...**: Snapshots your current settings into a new named profile (or overwrites an existing one of the same name).
- **Apply**: Loads the selected profile and applies its settings. This overwrites your current settings and reloads the UI.
- **Rename**: Renames the selected profile.
- **Delete**: Removes the selected profile.

#### The Default Profile

Every character starts with a profile named **Default**. It holds CooldownWatch's shipped settings and is created automatically - you never have to save it yourself. It cannot be deleted, renamed or overwritten, so there is always a clean baseline to go back to: select **Default** and click **Apply** to reset CooldownWatch to its factory settings. The Rename and Delete buttons are greyed out while it is selected.

#### Sharing Profiles (Export / Import)

Profiles can be shared as portable strings, making it easy to copy a setup between characters or hand it to another player.

- **Export**: Generates a copy-pasteable profile string for the selected profile in the *Profile String* field.
- **Import**: Paste a profile string into the field and import it as a new profile. Imported strings are validated, so an invalid, corrupted, or non-CooldownWatch string is rejected without changing any of your settings.

> Note: Profiles are stored per character. Use export/import to move a profile to another character.

## Issues

[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/issues.svg)](https://github.com/RagedUnicorn/wow-classic-cooldownwatch/issues)

Wrong or missing spell data is the most common report and the most valuable one - the issue tracker has a dedicated **Spell Data Report** template for it.

## Source

[![](https://raw.githubusercontent.com/RagedUnicorn/wow-cooldownwatch-meta/master/assets/source.svg)](https://github.com/RagedUnicorn/wow-classic-cooldownwatch)

## FAQ

#### Does CooldownWatch work on TBC Anniversary?

Yes - the addon loads and tracks with the Classic spell catalog as its baseline. Cooldowns that TBC reworked and spell ranks that are new in TBC are not covered yet; TBC-specific data is still being added. A cooldown you miss on TBC is exactly what the **Spell Data Report** issue template is for.

#### A cooldown counts down with the wrong duration. What now?

CooldownWatch ships the base cooldown of every spell it knows. If the enemy has a talent or item that shortens it, enable **Use worst case** for that spell (or **Assume worst case for all cooldowns** globally). If the number is still wrong, it is a data issue - open a GitHub Issue with the **Spell Data Report** template and it will be corrected in the spell catalog.

#### I get a red error (Lua Error) on my screen. What is this?

This is what we call a Lua error, and it usually happens because of an oversight or error by the developer (in this case me). Take a screenshot off the error and create a GitHub Issue with it, and I will see if I can resolve it. It also helps if you can add any additional information of what you were doing at the time and what other addons you have active. Additionally, if you are able to reproduce the error make sure to check if it still happens if you disable all others addons.
