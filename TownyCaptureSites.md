# TownyCaptureSites

TownyCaptureSites is a plugin created by LlmDl, which converts Towny Towns into CaptureSites, which then act as Capturable locations that Towns can take control of, gaining money or items as a reward.

#### Installation
CaptureSites is installed easily:
- Make sure you have a Towny installed which is at least version 0.99.0.6
- Add the TownyCaptureSites.jar file to your plugin folder and start your server.
- Run `/ta capturesites installperms` in game to give the permission nodes.
    - By default all town members will be able to use `/t defend` which teleports them to CaptureSites with active battles.
    - Mayors, Assistants and Sheriffs will also receive the node for using `/t capture` to initiate CaptureSites battles.
    - Mayors will be given the node for using `/t collectrewards`, to collect any item rewards.
    - You can optionally give all town members this permission using the following command: `/ta townyperms group towns.default addperm towny.command.town.capture`.
    - You could also create a new town rank that has the `towny.command.town.capture` permission node.
- Configure the new config.yml file.
    - The config is found in the `plugins\TownyCaptureSites\` folder.
    - Edit the file without using tabs (which would break the yaml formatting,) and then save the file.
    - Use `/ta reload townycapturesites` to reload the config file in game.
- (Optional) Install [Dynmap](https://dev.bukkit.org/projects/dynmap) and [Dynmap-Towny](https://github.com/TownyAdvanced/Dynmap-Towny/releases) in order highlight CaptureSite locations on the Dynmap plugin map.
- (Optional) Install [MapTowny](https://github.com/TownyAdvanced/MapTowny) and any of the [supported mappers](https://github.com/TownyAdvanced/MapTowny#dependencies) in order highlight CaptureSite locations on your server mapper.
- (Optional) Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) in order to use the Placeholders listed below.
- (Optional) Install [Slimefun](https://github.com/Slimefun/Slimefun4), [MMOItems](https://www.spigotmc.org/resources/mmoitems-premium.39267/) or [MythicMobs](https://www.spigotmc.org/resources/%E2%9A%94-mythicmobs-free-version-%E2%96%BAthe-1-custom-mob-creator%E2%97%84.5702/) to use their custom Items as rewards for CaptureSites.

#### CaptureSite Creation
CaptureSites are created by admins using the following steps:
- While at a location you like use `/ta town new NAME npc`, in order to make a town. You can add plots to your town using `/ta plot set NAME`. Alternatively you can create the town like normal and not use any admin commands until the end when you run `/ta set mayor NAME npc`.

- CaptureSites have an HP stat which must be attacked, this HP is only dropped in the Town/CaptureSite's homeblock, so make sure you have set your homeblock where you want, you can use `/t set homeblock` to move a homeblock that isn't where you want it. If you want to make the HP stat affected by players site-wide use the `/ta capturesite togglehomeblock` command now.

- CaptureSites default to awarding money to the controlling town. This can be changed to Item-based rewards using `/ta capturesite gui` then selecting the "Set Reward Type" icon, and then the "Set Items Reward" icon.

- When you have everything set you will use `/ta capturesite addsite`. If you wish to have CaptureSites revert back after battles use `/ta capturesite makesnapshot`.

- You are done, this CaptureSite can be taken over using `/t capture`.


#### CaptureSite Battles
CaptureBattles are started when a Town member with the `towny.command.town.capture` permission node uses `/t capture` while standing within a CaptureSite, and that CaptureSite has a defender.

Once the command is used, that player's Town cannot use `/t capture` again for a configurable amount of time, and a battle starts.

Battles last a configurable length of time or until the CaptureSite runs out of configurable amount of HP.

If it is enabled in the config file, CaptureSites can have a dynamic HP setting, determined by how many attacking players are online vs defending players. If the attackers outweigh the defenders, the Site will have a higher HP and vice versa. It is also an option for the HP to rebalance as attacking and defending players log on and off during active CaptureSite Battles.

When a Battle starts, all members of the defending and attacking towns will receive two boss bars, one showing the remaining time, and one showing the CaptureSite HP.

The CaptureSite's backing Town will have the AdminEnabledPVP setting flipped to true meaning PVP will happen regardless of the Town's normal setting (this is undone when the Battle ends.) 

A CaptureSites's HP is altered by players standing within the CaptureSite. Each CaptureSite can be configured to be attacked/healed only from within the HomeBlock or from anywhere in the CaptureSite (using `/ta capturesite togglehomeblock`.) The HP is harmed when attackers outnumber the defenders. When defenders outnumber the attackers, the HP is healed.

If the HP stat goes down to 0, the attackers win. If the timer runs out, the defenders win.

When a battle ends, there is a configurable cooldown placed on the CaptureSite.

If a snapshot was made of the CaptureSite, it will start to regenerate back to the original state.

#### CaptureSites
CaptureSites are converted Towns, which are fought over by players with Towns. A controlling town can receive a configurable amount of money or items every reward-time-period (defaults to an hour.)

Players are not allowed to build/destroy inside of CaptureSites, however CaptureSites can be damaged by explosions. There is a configurable option which allows defenders to use Switches. If a snapshot is made of a CaptureSite, any damage that does occur will be reverted after a battle.

You can view a list of CaptureSites using the `/towny capturesites` command.

A town that controls one or more CaptureSites will have a `[CaptureSites]` component to their town status screen, which has a list of CaptureSites controlled when you hover your mouse over it.

You can view information about a specific CaptureSite using the `/t [SiteName]` command.

CaptureSites can have a required minimum and maximum TownLevel. By default they do not, but if the admin has set a required min or max TownLevels via `/ta capturesites gui`, then in order for a town to initiate a capture battle, their town must be within the min and max settings. If a defending town has their TownLevel drop above or below the requirement they will not receive the rewards, and they will award a no-contest win if another town attempts to capture the site.

After a Town captures a CaptureSite (either via a battle, or no-contest,) there is a configurable cooldown before the CaptureSite can be captured again. When a cooldown ends there is a global announcement.

#### CaptureSites Rewards
By default CaptureSites will reward towns with money. But on a per-Site basis you can alternatively set two types of item-based rewards:
  - Fixed Item(s) - This gives a list of items (which can be just one item,) to the defending town, every hour.
  - Random Item - This gives one item from a list to the defending town, every hour.

Item-based rewards are enabled via the `/ta capturesite gui` command while stood in a CaptureSite. After setting the Reward Type to Fixed/Random Item you can select the "Set Reward Type" icon and fill the inventory with the items you want to give. Click "Save" and your CaptureSite will give either the Fixed or Random Rewards.

The items given as rewards can be Minecraft items, or if you have them installed, custom items from the following plugins: [Slimefun](https://github.com/Slimefun/Slimefun4), [MMOItems](https://www.spigotmc.org/resources/mmoitems-premium.39267/) or [MythicMobs](https://www.spigotmc.org/resources/%E2%9A%94-mythicmobs-free-version-%E2%96%BAthe-1-custom-mob-creator%E2%97%84.5702/).

You can switch back to Money rewards using the same `/ta capturesite gui` -> "Set Reward Type" option. The amount given is set in the config and is the same for every CaptureSite.

The amount of money which is rewarded is set using `/ta capturesite rewardmoney {amount}`, by default money rewards start with what is set in the config.

#### Dynmap-Towny / MapTowny Integration
If you have [Dynmap-Towny](https://github.com/TownyAdvanced/Dynmap-Towny/releases) or [MapTowny](https://github.com/TownyAdvanced/MapTowny) installed then the Towns which have been converted to CaptureSites will appear with altered InfoWindows when clicked upon.

Their colouring will also be affected:
  - The fill colour is replaced with a hex colour set in the config.
  - The border colour will be replaced by the colour in the config, or if there is a controlling town, it will use the town's colour.

#### Commands
```
/t [SiteName] - Shows a StatusScreen with useful information on the CaptureSite.

/t capture - Used to capture a CaptureSite. If there is no defender, it is taken over without a battle.
             If the CaptureSite is already controlled a CaptureBattle begins.

/t collectrewards - Used to collect item rewards.

/t defend - Teleports a member of a CaptureSites defending-town to a CaptureSite with an active battle.

/t defend {SiteName} - Teleports a member of a CaptureSite's defending-town to the specified CaptureSite with an active battle.

/towny capturesites - Opens a book which lists all the CaptureSites, their controller and their location. 
                      This is followed by a guide explaining how CaptureSites work as well as what config settings have been used.

/ta capturesite
    addsite - Converts a Town at your location into a CaptureSite.
    installperms - Installs the permission nodes.
    gui - Opens the GUI which has the below commands and more.
    makesnapshot - Creates a snapshot of the CaptureSite, used to regenerate when a battle is over, at your location.
    regenerate - Uses the snapshot to regenerate a CaptureSite at your location.
    rewardmoney {amount} - Used to set how much money is awarded on a per-site basis.
    removecooldown - Removes the after-battle cooldown on a CaptureSite at your location.
    removedefender - Removes the defending town on a CaptureSite at your location.
    togglehomeblock - Toggles whether the CaptureSite HP is affected only in the homeblock, or site-wide.
    removesite - Removes a CaptureSite at your location.
  
/ta reload townycapturesites - reloads the lang file, config file and database.
```

#### Permissions

towny.command.town.capture - used for /t capture.

towny.command.town.defend - used for /t defend.

towny.command.town.collectrewards - used for /t collectrewards.

#### PAPI Placeholders

`%townycapturesites_next_capture_site_time_remaining%` - Displays how much time is left before the next available capturesite can be captured.

`%townycapturesites_next_capture_site_name%` - Displays the name of the next available CaptureSite.

`%townycapturesites_capture_site_name_SITENAMEHERE%` - Displays the Name of the specified CaptureSite.

`%townycapturesites_capture_site_time_remaining_SITENAMEHERE%` - Displays the amount of time remaining on the specified CaptureSite's after-battle cooldown.

#### Events

CaptureSiteCapturedEvent - thrown when a CaptureSite is taken by an attacker.

CaptureSiteDefendedEvent - thrown when a CaptureSite is defended against.

CaptureSiteCaptureCommandEvent - a cancellable event which is thrown when /t capture is used.
