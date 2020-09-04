---
layout: quake
title: Quake
description: A Minecraft minigame
---

# Overview

Quake is a Spigot minigame developed by Upperlevel (a Github organization of two developers).
It has been created with Hypixel's Quake in mind and though as a public, highly customizable, porting of it.

### Want a preview of it?

Join the following Minecraft server, bring at least one friend and start playing!

QuakeTest -- 51.77.151.174:5000

# Features

Follows an overall list of its features:
* Full-featured Quake deathmatch gameplay (like Hypixel).
* 4 in-game powerups: speed, rapid-fire, dash-boost and invisibility.
* 3 types of database supported: SQLite, MySQL and MariaDB.
* 2 game modalities: local-mode (all on one server), bungee-mode (multiple servers).
* Highly customizable, with 3200+ lines of config.
* In-game shop permits to decorate: gun, armor, dash and kill sound.
* [LeaderHeads](https://www.spigotmc.org/resources/leaderheads.2079/) support through PlaceholderAPI.
* Several ways to join arenas: command, signs and join-gui.

# Usage

### Installation

Once bought, all you have to do is extract the .zip content inside of your server's plugins folder.
Keep in mind the required dependencies, that are:
* [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/)
* [Vault](https://www.spigotmc.org/resources/vault.34315/) (and any Economy plugin supporting it)
* [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)

### Arena setup

The arena setup consists of a series of commands that permits Quake to know where and how it has to interact
with your maps. You may use the following sequence every time you need to create a new map.

* `/q create %arena_name%`
  
  This command will create an empty world named Quake.%arena_name% where the arena should be created.
  You can either create the map from scratch or paste the map's schematic.
  
  If you just have the map's world folder, you can even manually insert it in the server's folder
  being aware of renaming it to Quake.%arena_name%. This should obviously be done after issuing
  the creation command.

* `/q setlobby`

  Set the location where players are teleported once they join the arena.
  This is where they'll wait for other players to join.

* `/q addspawn` 

  Add a game's spawn for the current arena.
  This is where players go when the match starts.

  *You can run this command as much as you need.*

* `/q addpowerup %effect_name% %respawn_ticks%`

  Add a powerup at the player's standing location.
  %effect_name% is the name of the powerup to add (see the Powerups section).
  %respawn_ticks% tells how many ticks should be delayed before respawning the powerup.
  
  *You can run this command as much as you need.*

* `/q setlimits %min_players% %max_players%`

  Tells the limits for the current arena, that is, the %min_players% for the lobby countdown to start.
  And the %max_players% that can be held within the arena.

* `/q info %arena_name%`

  Running this command will tell you if you have something left to set before saving or enabling the arena.

* `/q save %arena_name%`

  Once you've set your arena (buildings and config), **saving it is important and required**.

* `/q toggle`

  Finally you may want to enable the arena (actually make it joinable) using this command.

Obviously there are several more commands, but these are the required ones to get your arenas working.

### Database setup

Quake relies on the database in order to save player's statistics, selected and bought purchases.
These are the supported backends:
* SQLite (for local storage)
* MySQL
* MariaDB

You can configure the desired one in the `db.yml` file, inside of the plugin's folder.
The configuration file will look like this:

```yml
# The type of database to use, could be one of:
# - sqlite
# - mysql
# - mariadb
type: 'sqlite'

# Additional info that may be requested by the chosen database.
# Concretely, are needed only if the database isn't sqlite.
#host: 'localhost'
#port: 3306
#database: "quake"
#user: "quake"
#password: "12345"
```

### Gamemode config

The game can be configured in two modalities: local and bungee mode.

##### Local mode (default) -- One server

In local mode, when players join the Quake's server they get teleported to the, so called, hub.
This is a place where they can choose which arena to join.
In local mode the arenas can only be on the same server as the hub.
When the game inside of an arena ends, all of the players are sent back to the hub location.

You can set the hub location through the command: `/q sethub`.

##### Bungee mode -- Multiple servers

Using bungee mode, you're able to span Quake on multiple servers.
You are requested to set the hub server's name -- where players are sent when they end a match --
and the name of the arena that will be automatically joined when players join the server.

You can change the default modality and these values in `uppercore.yml`.

### Other configs

The strong point of Quake is that, as a public plugin, it has been thought to be highly customizable.
Its main configurations are `config.yml` and `uppercore.yml`, and counts 3200+ lines together.

