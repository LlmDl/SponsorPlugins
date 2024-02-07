# TownyCamps

TownyCamps allows a town-less player to place down a campfire in the wilderness which will then "claim" a camp, providing them 1 plot for a configured amount of time.

A town-less player is able to place a campfire in the wilderness to "claim" a chunk of land. They do need the townycamps.campfire permission node. 

Camps are limited to the min-distance-from-townblocks Towny setting, so player cannot park a camp too close to another town. Towns can claim right up to Camps.

Players that own the Camp can make a town at that location.

Camps are protected from Build/Destroy/Switch/Itemuse. Camp owners can allow their friendlist to interact based on the owners perm line.

PVP, Explosion and Burning actions are optionally protected (via the config.)

Chunk Notifications are shown when players enter and exit Camps.

Camp-owners can use LWCx in their camp. LWCx protections are removed when a camp is removed.

Camps appear in-game on Towny's ASCII map.

Camps are removed when:
- the campfire is broken,
- the campfire duration passes (defaults to 48 hours, is configurable,)
- the player joins or makes a town.

It uses Towny resident metadata so there's no database, it has a lang file and a config that updates itself just like Towny's.

Camp information can appear on your /res status screen (via the config.)

Camps appear will appear on your server's Dynmap, (optional via the config.)

Camps have an optional (via the config,) cooldown setting, preventing players from making new Camps until x hours have passed.

Camps have an optional (via the config,) CombatLogX support.


### Permission Nodes:
- `townycamps.campfire`


### Config Nodes:
```
version:
  # This is the current version.  Please do not edit.
  version: 0.0.46
# The language file you wish to use.
# Available: en-US.yml, zh-CN.yml
# You can add your own localization using the correct locale filename and placing
# your file into the townycamps\lang\override\ folder.
language: en-US.yml
  
  
camps:
  
  # How long a camp can exist for, before being de-activated.
  # De-activated camps can be re-lit to reset their time.
  # Soft-expired camps will no long provide PVP protection.
  soft_expiration_duration: 24h
  
  # How long a camp can exist for, before being deleted.
  # Set to -1 to have camps last forever.
  duration: 24h
  
  # How long after making a camp does a player have to wait to make a new one.
  # Set to 0h, to use no cooldown.
  creation_cooldown: 0h
  
  # When set above zero, this is determine the amount of money required to claim a camp.
  creation_cost: '0.0'
  
  # Should the camp location be shown on the /resident status screen page.
  show_location_on_status_screen: 'true'
  
  # When showing location on the status screen, should the minecraft coordinate of the campfire be used,
  # instead of the Towny chunk coordinates. Set true to use minecraft coords, false to use Towny coords.
  show_location_as_minecraft_coords: 'false'
  
  # Overrides Towny's min_plot_distance_from_town_plot setting when checking for camp proximity to other towns.
  # Set to -1 to use the value of min_plot_distance_from_town_plot.
  min_plot_distance_camp_override: '1'
  
  
  protections:
  
    # Is PVP disabled in camps?
    disable_pvp: 'false'
  
    # Is fire disabled in camps?
    disable_fire: 'true'
  
    # Are explosions disabled in camps?
    disable_explosion: 'true'
  
  
  home_setting:
  
    # When enabled, player that have the specified permission node to use /set home, will be prompted to set their home via a Confirmation,
    # when they create their Camps.
    enabled: 'true'
  
    # This permission node will be tested for when a player creates a camp and home_setting has been enabled.
    # If the player has this node they will receive a confirmation, which will cause the player to run /sethome, if they accept.
    permission_node: essentials.sethome
  
  
third_party:
  dynmap:
  
    # When set to true, and dynmap is found on the server, Camps will appear on the dynmap.
    enable_dynmap_support: 'false'
  
    # Which layer should the Camps appear on in your web browser?
    dynmap_layer_name: TownyCamps
  combatlogx:
  
    # When set to true, and CombatLogX is enabled on the server, players will be unable to create camps while in combat.
    enable_combatlogx_support: 'false'
  papi:
  
    # The format for the %townycamps_has_camp% placeholder.
    has_camp_placeholder: '[hasacamp]'

```

### PAPI placeholders
- %townycamps_has_camp% - Displays [hasacamp] if the player has a camp but is configurable.

### API Events:
- `NewCampEvent` - a cancellable event when a camp is created.
- `RemoveCampEvent`- an event thrown when a camp is deleted. 
