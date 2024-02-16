# Tower Of Babel

Tower Of Babel makes it so that players cannot understand everyone, until they are fluent in every language.

Tower Of Babel modifies the normal chat events after your other chat plugins have had a chance to format things, making it compatible with plugins like TownyChat.

In order to speak in a language, players must have a minimum amount of fluency (by default this is 25%.)

Until they reach 1.0 (100%) some of their messages will become scrambled. Letters which are capitalized will remain capitalized, lower case letters will remain lower case. There is a configurable list of punctuation symbols which will also not be scrambled.

Each race will come with a default language proficiency schema. As players progress in successfully speaking in other languages they will gain proficiency (at a configrable chance and amount.)

If a player changes race, their proficiencies will reset to their new race's default proficiency.

Players can chat in their own language by speaking. If they want to chat in other languages they can:
- use `/language [languagename]` or,
- append their chat with -[languagename] which will allow them to speak in a language without altering their default language.


### Setup:

- Place TowerOfBabel.jar into your plugins folder and start your server. A config.yml will be made in a new TowerOfBabel folder.
- Create a system to hand out races.
  - Your server should create a system that places a player into a configured Race, by default TowerOfBabel comes with Human, Elf, WoodElf and Orc, but you can configure whatever races you would like.
  - You can implement race-selection for players by using CommandBlocks that make use of the `/language [playername] setrace [racename]` command.
  - The TowerOfBabel config.yml also contains a default race value, which will be applied to all players which join and have not had a race set.

### Commands:
```
- /language [languagename] - Sets the language a player speaks in by default.
- /language [playername] setrace [racename] - Sets the player's race, all fluencies are set to the race default. (Admins only.)
- /language [playername] add [languagename] [-|+amount] - Adds or decreases a player's fluency in a language. (Admins only.)
```
- Players can also specify a language to speak into using the chat like so:
  - 'Some Words Here -elvish' <- This will display 'Some Words Here' in Elvish.

> Tip:
> 
> If you would like to use the above admin commands in a Command Block, so you can use the @p selector, get the [CommandHook plugin](https://www.spigotmc.org/resources/commandhook.61415/).

### Permissions:

- `towerofbabel.hear_clearly` - Defaults to OPs, players can understand every language clearly.
- `towerofbabel.admin` - Defaults to OPs, these players can use `/language [playername]` commands.

### API:
TowerOfBabel contains an TowerOfBabelAPI class, accessible via TowerOfBabel.getPlugin().getAPI();
- In it you will find methods that can tell you about a player's race, languages, fluencies, as well as the ability to alter those.
- You will also be able to determine what races and languages are present on the server.

### Config:
```
  
# The plugin makes it so that players cannot understand everyone, until they are fluent in every language.
#
# Ops and players with the towerofbabel.hear_clearly permission node are able to understand every language clearly.
# Ops and players with the towerofbabel.admin permission node can use the admin commands found in /language.
# Commands:
#  - /language [languagename] - Sets the language a player speaks in by default.
#  - /language [playername] setrace [racename] - Sets the player's race, all fluencies are set to the race default.
#  - /language [playername] add [languagename] [-|+amount] - Adds or decreases a player's fluency in a language.
#
# Players can also specify a language to speak into using the chat like so:
# 'Some Words Here -elvish' <- This will display 'Some Words Here' in Elvish.
#
# Read below to learn more about the plugin.
plugin_explanation: ''
  
version:
  # This is the current version.  Please do not edit.
  version: ''
  
# The list of races and their settings.
# The order of properties is:
#  - race key
#    - Race Name - How the race will appear in game.
#    - Primary Language - The language players will speak when they log in.
#    - Fluencies - The fluencies that are given to players that adopt a race.
races:
  human:
    name: Human
    primaryLanguage: Common
    fluencies: Common-1.0,Elvish-0.5,Orcish-0.1
  elf:
    name: Elf
    primaryLanguage: Elvish
    fluencies: Common-1.0,Elvish-1.0,Orcish-0.25
  woodelf:
    name: WoodElf
    primaryLanguage: Elvish
    fluencies: Common-1.0,Elvish-1.0,Orcish-0.15
  orc:
    name: Orc
    primaryLanguage: Orcish
    fluencies: Common-0.5,Elvish-0.1,Orcish-1.0
  
settings:
  
  # The default race given on join.
  default_race: Human
  
  # The fluency required to speak in any language.
  required_fluency: '0.25'
  
  # The chance that when successfully speaking in your non-native language, you will have your fluency increase.
  # This percent only applies when you're not talking to yourself, you must have an audience.
  fluency_increase_chance: '0.01'
  
  # The amount that fluency will increase by when successfully speaking in your non-1.0 language.
  # Supports up to 3 decimal places, allowing as low as 0.001.
  fluency_increase_amount: '0.01'
  
  # The symbols that will not get filtered.
  unfiltered_punctuation: ',./?:;[]<>|\~`!@#$%^&*()_-+=''"'
  
  # When set to true, the player's name will use the DisplayName, a name which is commonly modified
  #  by other plugins which add prefixes. It is known as {modplayername} in TownyChat.
  use_displayname: 'false'
```
