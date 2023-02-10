# SiegeConquest
A SiegeWar add-on for originally made for MineEarth.co, with optional, old-school Conquering/Annexing.

**SiegeConquest adds a choice to the standard SiegeWar invasion system.**

Upon placement of the Invasion banner, the player is prompted to select either Annexation or Occupation. Occupation is the normal SiegeWar route while Annexation is a new path, closer to original SiegeWar: the town becomes part of the winning nation, (and if the town is a capital of a nation, so do the rest of the nation's towns.)

Upon annexation, the town(s) become(s) Conquered via the normal Towny mechanic, for a configurable amount of days.

Annexed towns cannot:
- delete themselves (optional,)
- set a new mayor (optional,)
- have their mayor leave the town (optional,)
- go into ruin.
- leave their nation.

Annexed towns:
- have their ability to unclaim plots rate-limited (optional.)

When a non-annexed town leaves their nation they:
- lose their peaceful status if they have one (optional,)
- lose their siege immunity, if they have any (optional.)

There are config options to prevent deleting a town or nation under siege, or toggling neutral on a town which is sieged.

Optionally, peaceful towns with no nation can be annexed/conquered when a nation subverts them.

### Config Nodes
```
  
version:
  # This is the current version.  Please do not edit.
  version: '1.7'
  
annexation_settings:
  
  # When a nation subverts a peaceful town, if that town has no nation, and is a nationless and peaceful town, do they get annexed instead of occupied?
  # Setting this to true means that peaceful towns with no nation are made full members of the Subverting nation, with the conqered status set for the number of days set below.
  are_peaceful_nationless_towns_annexed: 'false'
  
  # When annexation is chosen, how many days are towns conquered for?
  conquered_days: '7'
  
conquer_settings:
  
  # When true, conquered towns wont be able to delete their town.
  disallow_town_delete: 'true'
  
  # When true, conquered towns' mayors wont be able to /t leave their town.
  disallow_town_leave_for_mayor: 'true'
  
  # When true, conquered towns' mayors wont be able to /t set mayor.
  disallow_transfering_mayor: 'true'
  
  # When true, conquered towns' mayors wont be able to freely /t unclaim.
  limit_unclaiming: 'true'
  
  # How many townblocks can be unclaimed simultaneously.
  # The town will be able to have X unclaimed plots before the first unclaimed plot's cooldown must end to allow another unclaim.
  unclaiming_cap: '4'
  
  # How many minutes does a townblock's unclaim cooldown last?
  unclaiming_cooldown_in_minutes: '20'
  
nation_leave_settings:
  
  # When true, a town that does /n leave, loses their peaceful status.
  town_loses_peaceful_status: 'true'
  
  # When true, a town that does /n leave, loses their siege immunity.
  town_loses_siege_immunity: 'true'
  
nation_settings:
  
  # Are Nations that have towns which are sieged unable to be deleted.
  prevent_sieged_nations_being_deleted: 'true'
  
town_settings:
  
  # Are towns which are sieged unable to be deleted.
  prevent_sieged_town_being_deleted: 'true'
  
  # Are towns which are sieged unable to toggle peaceful.
  prevent_sieged_town_toggle_peaceful: 'true'
```

### Multi-language
The same multi-language that exists in Towny, SiegeWar and other TownyAdvanced plugins is also available in SiegeConquest.

See the [Towny wiki for details.](https://github.com/TownyAdvanced/Towny/wiki/How-Towny-Works#multi-language)


### Commands

`/ta reload siegeconquest` - Reloads the config and language files.
