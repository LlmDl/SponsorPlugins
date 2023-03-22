# TownyRTP

*Helping your new players get a home in a town quick!*

A town-less player is able to use the command `/town rtp` which will teleport them to a random town where they can purchase a for-sale plot (the plot is a default/residential type.)

The Town must be open, public, have plots for sale and the player must be able to afford the plot they're being teleported to.

The player will be limited by Towny's features:
  - They must be able to pay the spawn cost if the Town has one (public spawn cost.)
  - They cannot be an outlaw of the Town.
  - They will be limited by Towny's Teleport Warmups and Cooldowns.
  - They will be limited by Towny's config's prevent_town_spawn_in settings.

  
Additionally, when a player joins a town, is stood in the town's area, and doesn't have any land there, they will be offered to be teleported to a plot, which is for sale and that they can afford.


Additionally, the plugin will throw both a TownSpawnEvent that may be cancelled by other plugins, making this a seamless addition when other plugins are limiting Towny's town spawning.
TownyRTP also fires it's own TownyRTPEvent if you want to specifically target RTP teleport events.

### Permission Nodes
- `townyrtp.command.town.rtp` - Given by default, you do not have to add anything.

### Commands
```
/town rtp - teleport to a random plot.
/town rtp -ignore - teleport without a cost warning.
/town rtp -autojoin - auto join the town while you teleport to it.
/town rtp -neutral - limits the towns to only neutral towns.
/town rtp [playername] {-ignore} {-autojoin} - for admin, to teleport someone to a random plot, with optional args.
```

### API Events
- `TownyRTPEevent` - a cancellable event thrown when players are teleported by TownyRTP.
