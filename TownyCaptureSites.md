# TownyCaptureSites

TownyCaptureSites is a plugin created by LlmDl, which converts Towny Towns into CaptureSites, which then act as Capturable locations that Towns can take control of, and gain money from.

#### Installation
CaptureSites is installed easily:
- Add the TownyCaptureSites.jar file to your plugin folder and start your server.
- Run `/ta capturesite installperms` in game to give the permission nodes.
    - By default all town members will be able to use `/t defend` which teleports them to CaptureSites with active battles.
    - Mayors, Assistants and Sheriffs will also receive the node for using `/t capture` to initiate CaptureSites battles.
    - You can optionally give all town members this permission using the following command: `/ta townyperms group towns.default addperm towny.command.town.capture`.
    - You could also create a new town rank that has the `towny.command.town.capture` permission node.
- Configure the new config.yml file.
    - The config is found in the `plugins\TownyCaptureSites\` folder.
    - Edit the file without using tabs (which would break the yaml formatting,) and then save the file.
    - Use `/ta reload townycapturesites` to reload the config file in game.
- (Optional) Install [Dynmap](https://dev.bukkit.org/projects/dynmap) and [Dynmap-Towny](https://github.com/TownyAdvanced/Dynmap-Towny/releases) in order highlight CaptureSite locations on the Dynmap plugin map.

#### CaptureSite Creation
CaptureSites are created by admins using the following steps:
- While at a location you like use `/ta town new NAME npc`, in order to make a town. You can add plots to your town using `/ta plot set NAME`. Alternatively you can create the town like normal and not use any admin commands until the end when you run `/ta set mayor NAME npc`.

- CaptureSites have an HP stat which must be attacked, this HP is only dropped in the Town/CaptureSite's homeblock, so make sure you have set your homeblock where you want, you can use `/t set homeblock` to move a homeblock that isn't where you want it.

- When you have everything set you will use `/ta capturesite addsite`. If you wish to have CaptureSites revert back after battles use `/ta capturesite makesnapshot`.

- You are done, this CaptureSite can be taken over using `/t capture`.

#### CaptureSite Battles
CaptureBattles are started when a Town member with the `towny.command.town.capture` permission node uses `/t capture` while standing within a CaptureSite, and that CaptureSite has a defender.

Once the command is used, that player's Town cannot use `/t capture` again for a configurable amount of time, and a battle starts.

Battles last a configurable length of time or until the CaptureSite runs out of configurable amount of HP.

When a Battle starts, all members of the defending and attacking towns will receive two boss bars, one showing the remaining time, and one showing the CaptureSite HP. 

The CaptureSite's backing Town will have the AdminEnabledPVP setting flipped to true meaning PVP will happen regardless of the Town's normal setting (this is undone when the Battle ends.)

A CaptureSites's HP is altered by players standing within the CaptureSite's Homeblock. The HP is harmed when attackers outnumber the defenders. When defenders outnumber the attackers, the HP is healed.

If the HP stat goes down to 0, the attackers win. If the timer runs out, the defenders win.

When a battle ends, there is a configurable cooldown placed on the CaptureSite.

If a snapshot was made of the CaptureSite, it will start to regenerate back to the original state.

#### CaptureSites
CaptureSites are converted Towns, which are fought over by players with Towns. A controlling town can receive a configurable amount of money every hour.

Players are not allowed to build/destroy inside of CaptureSites, however CaptureSites can be damaged by explosions. If a snapshot is made of a CaptureSite, any damage that does occur will be reverted after a battle.

You can view a list of CaptureSites using the `/towny capturesites` command.

A town that controls one or more CaptureSites will have a `[CaptureSites]` component to their town status screen, which has a list of CaptureSites controlled when you hover your mouse over it.

You can view information about a specific CaptureSite using the `/t [SiteName]` command.

#### Dynmap-Towny Integration
If you have [Dynmap-Towny](https://github.com/TownyAdvanced/Dynmap-Towny/releases) installed then the Towns which have been converted to CaptureSites will appear with altered InfoWindows when clicked upon.

Their colouring will also be affected:
  - The fill colour is replaced with a hex colour set in the config.
  - The border colour will be replaced by the colour in the config, or if there is a controlling town, it will use the town's colour.

#### Commands
```
/t [SiteName] - Shows a StatusScreen with useful information on the CaptureSite.

/t capture - Used to capture a CaptureSite. If there is no defender, it is taken over without a battle.
             If the CaptureSite is already controlled a CaptureBattle begins.

/t defend - Teleports a member of a CaptureSites defending-town to a CaptureSite with an active battle.

/t defend {SiteName} - Teleports a member of a CaptureSite's defending-town to the specified CaptureSite with an active battle.

/towny capturesites - Opens a book which lists all the CaptureSites, their controller and their location. 
                      This is followed by a guide explaining how CaptureSites work as well as what config settings have been used.

/ta capturesite
    addsite - Converts a Town at your location into a CaptureSite.
    installperms - Installs the permission nodes.
    makesnapshot - Creates a snapshot of the CaptureSite, used to regenerate when a battle is over, at your location.
    regenerate - Uses the snapshot to regenerate a CaptureSite at your location.
    removecooldown - Removes the after-battle cooldown on a CaptureSite at your location.
    removedefender - Removes the defending town on a CaptureSite at your location.
    removesite - Removes a CaptureSite at your location.
  
/ta reload townycapturesites - reloads the lang file, config file and database.
```

#### Permissions

towny.command.town.capture - used for /t capture.

towny.command.town.defend - used for /t defend.
