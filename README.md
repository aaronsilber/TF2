[![](https://img.shields.io/codacy/grade/e201fa6b35074864b200eaf558563a22.svg)](https://hub.docker.com/r/cm2network/csgo/) [![Docker Build Status](https://img.shields.io/badge/docker%20build-passing-brightgreen.svg)](https://hub.docker.com/r/cm2network/csgo/)<sup><sup>1</sup></sup> [![Docker Stars](https://img.shields.io/docker/stars/cm2network/csgo.svg)](https://hub.docker.com/r/cm2network/csgo/) [![Docker Pulls](https://img.shields.io/docker/pulls/cm2network/csgo.svg)](https://hub.docker.com/r/cm2network/csgo/) [![](https://images.microbadger.com/badges/image/cm2network/csgo.svg)](https://microbadger.com/images/cm2network/csgo)
# Supported tags and respective `Dockerfile` links
-	[`latest` (*buster/Dockerfile*)](https://github.com/CM2Walki/TF2/blob/master/buster/Dockerfile)
-	[`metamod` (*buster-metamod/Dockerfile*)](https://github.com/CM2Walki/TF2/blob/master/buster-metamod/Dockerfile)
-	[`sourcemod` (*buster-sourcemod/Dockerfile*)](https://github.com/CM2Walki/TF2/blob/master/buster-sourcemod/Dockerfile)

# What is Team Fortress 2?
Nine distinct classes provide a broad range of tactical abilities and personalities. Constantly updated with new game modes, maps, equipment and, most importantly, hats!
This Docker image contains the dedicated server of the game.

>  [TF2](https://store.steampowered.com/app/440/Team_Fortress_2/)

<img src="http://www.teamfortress.com/workshop/images/tf_logo.png" alt="logo" width="300"/></img>

# How to use this image
## Hosting a simple game server

Running on the *host* interface (recommended):<br/>
```console
$ docker run -d --net=host --name=tf2-dedicated -e SRCDS_TOKEN={YOURTOKEN} cm2network/tf2
```

Running multiple instances (increment SRCDS_PORT and SRCDS_TV_PORT):
```console
$ docker run -d --net=host -e SRCDS_PORT=27016 -e SRCDS_TV_PORT=27021 -e SRCDS_TOKEN={YOURTOKEN} --name=tf2-dedicated2 cm2network/tf2
```

`SRCDS_TOKEN` **is required to be listed & reachable;** [https://steamcommunity.com/dev/managegameservers](https://steamcommunity.com/dev/managegameservers)<br/><br/>
**It's also recommended to use "--cpuset-cpus=" to limit the game server to a specific core & thread.**<br/>
**The container will automatically update the game on startup, so if there is a game update just restart the container.**

# Configuration
## Environment Variables
Feel free to overwrite these environment variables, using -e (--env): 
```dockerfile
SRCDS_RCONPW="changeme" (value can be overwritten by tf2/cfg/server.cfg) 
SRCDS_PW="changeme" (value can be overwritten by tf2/cfg/server.cfg) 
SRCDS_PORT=27015
SRCDS_TV_PORT=27020
SRCDS_FPSMAX=300
SRCDS_TICKRATE=66
SRCDS_MAXPLAYERS=14
SRCDS_REGION=3
```
## Config
The config files can be found in the following directory: */home/steam/tf2-dedicated/tf2/cfg*

If you want to learn more about configuring a TF2 server check this [documentation](https://wiki.teamfortress.com/wiki/Dedicated_server_configuration).

# Image Variants:
The `tf2` images come in three flavors, each designed for a specific use case.

## `tf2:latest`
This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is a bare-minimum TF2 dedicated server containing no 3rd party plugins.<br/>

## `tf2:metamod`
This is a specialized image. It contains the plugin environment [Metamod:Source](https://www.sourcemm.net) which can be found in the addons directory. You can find additional plugins [here](https://www.sourcemm.net/plugins).

## `tf2:sourcemod`
This is another specialized image. It contains both [Metamod:Source](https://www.sourcemm.net) and the popular server plugin [SourceMod](https://www.sourcemod.net) which can be found in the addons directory. [SourceMod](https://www.sourcemod.net) supports a wide variety of additional plugins that can be found [here](https://www.sourcemod.net/plugins.php).