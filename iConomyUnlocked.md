# iConomyUnlocked

### Overview

iConomy's lineage dates back to the first years of Bukkit Plugins, created by Nijikokun. Having around 7 distinct versions, iConomy had its ups and downs over the years. At one point [iConomy 5](https://github.com/iconomy5legacy/iConomy) was taken over by ElgarL, and then ultimately LlmDl.

Known for its simplicity and resiliance, iConomy 5 served many servers well for years but it was time to abandon it once [VaultUnlocked](https://github.com/TheNewEconomy/VaultUnlocked) arrived.

VaultUnlocked finally adds proper UUID support to the VaultAPI. With that it is finally possible for plugins that use non-player accounts (like Towny,) to integrate with Economy plugins without using Vault's outdated named methods.

iConomyUnlocked has been created to give iConomy 5-using servers an exit path. It support both the VaultAPI and VaultAPI 2, meaning it will work with any Vault plugins and any Vault2 plugins.

----
### Facts

- Supports Vault-based and Vault2(VaultUnlocked)-based plugins that use economies.
- Supports Folia.
- Supports the H2 and MySQL database types.
- Uses CommentedConfiguration for a config which automatically updates while maintaining your settings.
- Can import accounts from iConomy 5.26.

----
### Requirements:

- [VaultUnlocked](https://github.com/TheNewEconomy/VaultUnlocked) or Vault.

----
### Commands:

> <> Required, [] Optional

- /money: View your balance.
  - ?: Help screen.
  - [playername]: View someone else's balance.
  - rank: View your rank in the richest players list.
  - rank \<playername>: View someone else's rank in the richest players list.
  - top [amount]: View the top richest players.
  - pay \<player> \<amount>: Pay someone money.
  - grant \<player> \<amount> \<silent>: Add money to someone's account.
  - grant \<player> -\<amount> \<silent>: Remove money from someone's account.
  - set \<player> \<amount>: Set someone's balance.
  - hide \<player> \<true/false>: Hide or show an account on the top list.
  - create \<player>: Creates an account with the default balance for a player.
  - remove \<player>: Removes an account.
  - reset \<player>: Resets an account to the default balance.
  - purge: Removes all default-balance accounts.
  - empty: Empties all accounts.
  - stats: Checks stats about the economy.
  - importiconomy: Imports accounts from iConomy 5.26.

----
### Permissions:

  - iConomy.admin:
    - default: false
    - children:
      - iConomy.admin.account.create: true
      - iConomy.admin.account.remove: true
      - iConomy.admin.reset: true
      - iConomy.admin.bank.create: true
      - iConomy.admin.empty: true
      - iConomy.admin.purge: true
      - iConomy.admin.stats: true
      - iConomy.admin.grant: true
      - iConomy.admin.hide: true
      - iConomy.admin.set: true
      - iConomy.admin.importiconomy: true
  - iConomy.access:
    - default: true
  - iConomy.payment:
    - default: true
  - iConomy.rank:
    - default: true
  - iConomy.list:
    - default: op


----
### PlaceholderAPI Placeholders:

  - `%iconomyunlocked_top_n%` - Shows the nth-ranked account, with rank #, name and account balance. **Replace n with the number of the position you want to show! ie: `%iconomyunlocked_top_1%` will show the richest account.**

