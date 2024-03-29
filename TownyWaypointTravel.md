# TownyWayPointTravel

Are you tired of your players not exploring the map? 

Wish public spawning had more hangups?

Wish that players couldn't join a Town before visiting it? 

TownyWayPointTravel is the solution you didn't know you needed!

TownyWayPointTravel brings a feature from many classic RPGs: you have to visit a location before you can fast travel to it.

### Config
```
version:
  # This is the current version.  Please do not edit.
  version: '1.9'
  
prevent:
  
  # When true, a player has to have visited a town to use /t spawn or /n spawn.
  spawning_to_unvisited_towns: 'true'
  
  # When true, a player is always allowed to visit their nation's capital using /t spawn or /n spawn.
  spawning_allowed_to_nation_capital: 'false'
  
  # When true, other Bukkit plugins that use Bukkit TeleportEvents will also have their spawns cancelled, if the destination is a town which the player has not discovered.
  teleports_from_3rd_party_plugins: 'true'
  
  # When true, a player has to have visited a town to be able to join a town.
  joining_unvisited_towns: 'true'
  
lang:
  you_cannot_spawn: You have not visited %s yet, you cannot fast travel to this location.
  you_cannot_join: '%s has not visited %s yet, they cannot join the town.'
  you_discovered: You have discovered the town of %s.
  
towns:
  
  # A list of town names that players will be allowed to spawn to by default.
  # If you want to have a server city accessible to all from the start, this is where you would put that town name.
  default_towns: ''
  
discovery_commands:
  
  # When true the below commands will be run when a player discovers a town.
  enabled: 'true'
  
  # When discovery commands are enabled, the list of commands that are ran when a player discovers a town for the firs time.
  # Optionally you can use {playername} to use the player's name in the commands, or {townname} to use the town name which the player discovered.
  commandlist: /op {playername}, /commandusing {playername}, /commandusing {townname}

```

### API Events
`TownyWayPointsDenyTeleportEvent` - Plugins that want to override TownyWayPoints denying a teleport may do so.
