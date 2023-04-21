# TownyHistories

What happens when a Town is deleted? Where Towny leaves off, TownyHistories takes over. Towns become Ruins, appearing on your Dynmap, Lecterns mark the old spawn point with a book that has recorded some historical information about the now defunct Town, and more... 

When Towns are deleted, they generate a Ruin. Ruins appear on your Dynmap (if you have it enabled,) with an icon marking the town's old spawn point and the town's old townblocks displayed in a shade of grey. 

At the old spawn point you will find a protected lectern and with a protected book sharing information about the ruin's Town.

Ruins can optionally be preserved from build/destroy actions.

Ruins display an actionbar message when they are entered into. 

Ruins appear on Towny's ASCII map.

Ruins' townblocks which are claimed by a town are removed from the ruin. If a ruin's homeblock is claimed by a town the ruin is removed entirely.

Optionally, you can prevent claiming either only the old homeblocks or any part of the ruin.

Admins can optionally resurrect deleted towns.

Note: this plugin somewhat assumes you have the revert-on-unclaim feature deactivated. This is not a hard-restriction, but future features will likely mean restoring the ruin would be detrimental.

TownyHistories uses Towny's multi-language system, allowing your players to see plugin messages in the language their minecraft client is set.

### Permission nodes
- `townyhistories.admin` - used for the /ruinadmin command.
- `townyhistories.ruin` - used for the /ruin command.

### Commands
```
/ruin list - list the ruins.
/ruin info [name] - ruin information displayed in book form.

/ruinadmin list - list the ruins.
/ra info [name] - ruin information displayed in book form.
/ra delete [name] - deletes the chosen ruin.
/ra purge [days] - purges ruins that have a fallen date older than the given day amount.
/ra reload - reloads lang, config and database.
/ra restore [ruin_name] {mayor} - restores a ruin into a town, to the original mayor or to any player when specified.
/ra spawn [name] - spawn to a ruin's spawn point.
```

### Config
```
  
  
version:
  # This is the current version.  Please do not edit.
  version: 0.0.26
  
third_party:
  dynmap:
  
    # When set to true, and dynmap is found on the server, Ruins will appear on the dynmap.
    enable_dynmap_support: 'true'
  
  
ruin_settings:
  
  # When set to true, a lectern will mark the ruin's old spawn point.
  create_lectern_at_ruin_spawn: 'true'
  
  # When set to true, players will not be able to destroy the lectern marking a ruin.
  preserve_lectern: 'true'
  
  # When set to true, players will not be able to build or destroy inside of ruins.
  preserve_ruins: 'true'
  
  # Setting this to false will allow people to steal the lectern books before the ruin is deleted.
  protect_lectern_book: 'true'
  
  # When set to true, players will not be able to claim any land that belongs to a ruin.
  prevent_claiming_ruin: 'false'
  
  # When set to true, players will not be able to claim the ruin's homeblock.
  prevent_claiming_homeblock: 'false'
  
  # Defaults to ruin, any other dynmap marker can be used: https://github.com/webbukkit/dynmap/tree/v3.0/DynmapCore/src/main/resources/markers 
  marker_icon: ruin

```
