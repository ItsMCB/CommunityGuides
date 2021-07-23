# Creating a Java Server

### About

Minecraft is a great game! However, it wouldn't be what it is today without it's [multiplayer features](https://help.minecraft.net/hc/en-us/articles/360035131391-How-to-Play-Minecraft-Multiplayer). Playing on servers with friends is a lot of fun, but what if you want to make your own server? From choosing your server software to setting up plugins \(or mods\), this guide will extensively cover how to create different types of Minecraft: Java Edition servers.

### Prerequisites

...

### Useful Resources

Check out these resources to aid you in your server ownership journey. Feel free to let them know we sent you there 😎

* [Discord - Vexelosity](https://discord.com/invite/QW2m6bYG4S)
* [Minecraft - How to Play Minecraft Multiplayer](https://help.minecraft.net/hc/en-us/articles/360035131391-How-to-Play-Minecraft-Multiplayer)
* [Reddit - Admincraft](https://www.reddit.com/r/admincraft/)

## Server Basics

### Choosing The Right Software

Choosing the right software is very important as it will define your limitations for features and performance. Luckily, there are tons of options to choose from. Before I give you a list of software, lets go over some important terms.

### What are "forks"?

This is a [Git ](https://en.wikipedia.org/wiki/Git)\(a [version control](https://en.wikipedia.org/wiki/Version_control) technology which is very popular in the development space\) term that refers to taking code and making a variant of it. An example of this is how the Minecraft modding platform called Forge uses code from the official Minecraft server software, but then adds their own code into the project to allow for mods to work. This means that the difference between the fork \(Forge\) and the original is the code they created. However, without the original code, Forge wouldn't run because it's built on top of the original.

### What is "vanilla" Minecraft?

Vanilla refers to the [default software](https://www.minecraft.net/en-us/download/server) provided by Mojang. Think of a normal singleplayer world, but your friends can join. It doesn't have any support for mods or plugins \(which we'll cover below\).

### What is "modded" Minecraft?

Modded often refers to the use of mods \(shorthand for modifications\) that are typically client-side features. Mods can add new menus, blocks, entities, etc. directly into the game. The following video from 2012, while a bit dated, explains the concept in greater detail.

{% embed url="https://youtu.be/UMXnHhk-7sA" %}

{% hint style="warning" %}
Most mods require all players that join to have downloaded the mods to their client. This means that players who don't use that modding platform and or don't have those mods can't play on your server. This is often a turnoff for inexperienced players, and as a result, a large portion of servers decide to use a plugin platform.
{% endhint %}

{% hint style="info" %}
A popular example of a mod is [Pixelmon Reforged](https://reforged.gg/), which is [Pokémon ](https://www.pokemon.com/us/parents-guide/)recreated in Minecraft.
{% endhint %}

### What are "plugins"?

Plugins are pieces of software that are added onto the server only. Plugins do not change the game itself, which is unlike a mod. The biggest advantage to plugins is that they are server-side, meaning that players don't need to download anything to join.

{% hint style="info" %}
A popular example of a plugin is [Essentials X](https://essentialsx.net/), a suite of useful server commands for players and server staff.
{% endhint %}

## Software Options

Here are some popular Minecraft: Java Edition server software options.

### [Minecraft Server \(Vanilla\)](https://www.minecraft.net/en-us)

{% tabs %}
{% tab title="Information" %}
The official Minecraft server software.

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| Mojang | Closed | Alive | Minecraft |
{% endtab %}

{% tab title="Reasons to Use" %}
* Default game experience.
* Easy to setup.
* No plugin configurations.
* Players don't have to download anything to join.
{% endtab %}

{% tab title="Upstream\(s\)" %}
N/A
{% endtab %}
{% endtabs %}

### [CraftBukkit](https://bukkit.org/)

{% tabs %}
{% tab title="Information" %}
A forked version of vanilla Minecraft that includes support for Bukkit plugins.

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| Mojang | "It's complicated" | Dead | Bukkit API |

{% hint style="warning" %}
Bukkit was acquired by Mojang on February 28, 2012. However, this project has been ceased since Q3 2014 because of a DMCA takedown dispute. The project is dead, so use a continued forked version instead.
{% endhint %}
{% endtab %}

{% tab title="Upstream\(s\)" %}
Built on Vanilla
{% endtab %}
{% endtabs %}

### [Spigot](https://www.spigotmc.org/)

{% tabs %}
{% tab title="Information" %}
The continuation of the CraftBukkit project that supports Spigot plugins.

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| SpigotMC Pty. Ltd. | [Open](https://hub.spigotmc.org/stash/projects/SPIGOT) | Alive | Bukkit & Spigot API |

{% hint style="warning" %}
Spigot is unoptimized in comparison to it's forks. Some say Spigot is "doing the bare minimum" \(only updating the upstream for the downstream when a new update comes out\). It is recommended that you use a better-optimize fork such as Paper or Purpur.
{% endhint %}
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
* CraftBukkit
{% endtab %}
{% endtabs %}

### [Paper](https://papermc.io/)

{% tabs %}
{% tab title="Information" %}
"Paper is the next generation of Minecraft server, compatible with Spigot plugins, offering uncompromising performance."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| The PaperMC Team | [Open](https://github.com/PaperMC/Paper) | Alive | Bukkit, Spigot, and Paper API |
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
* CraftBukkit
* Spigot
{% endtab %}
{% endtabs %}

### [Tuinity](https://github.com/Tuinity/Tuinity)

{% tabs %}
{% tab title="Information" %}
"Fork of Paper aimed at improving server performance at high playercounts."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| Tuinity | [Open](https://github.com/Tuinity/Tuinity) | Alive | Bukkit, Spigot, and Paper API |
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
* CraftBukkit
* Spigot
* Paper
{% endtab %}
{% endtabs %}

### [Airplane](https://airplane.gg/)

{% tabs %}
{% tab title="Information" %}
"A stable, optimized, well supported 1.16.5 Paper fork."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| TECHNOVE | [Open](https://github.com/TECHNOVE/Airplane) | Alive | Bukkit, Spigot, and Paper API |
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
* CraftBukkit
* Spigot
* Paper
{% endtab %}
{% endtabs %}

### [Purpur](https://purpur.pl3x.net/)

{% tabs %}
{% tab title="Information" %}
"Purpur is a drop-in replacement for Paper servers designed for configurability, new fun & exciting gameplay features, and high performance built on top of Tuinity"

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| pl3xgaming | [Open](https://github.com/pl3xgaming/Purpur) | Alive | Bukkit, Spigot, and Paper API |
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
* CraftBukkit
* Spigot
* Paper
* Tunity
{% endtab %}
{% endtabs %}

### [Yatopia](https://yatopiamc.org/)

{% tabs %}
{% tab title="Information" %}
"Blazing fast Tuinity fork with best in class performance."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [YatopiaMC](https://github.com/YatopiaMC) | [Open](https://github.com/YatopiaMC/Yatopia) | Dead | Bukkit, Spigot, and Paper API |

![YatopiaMC Discord Announcement](https://i.imgur.com/IM3ATxJ.png)
{% endtab %}

{% tab title="Upstream\(s\)" %}
"Yatopia combines the code from many [Paper](https://github.com/PaperMC/Paper) forks and optimization mods, as well as many unique optimizations."

Code has been borrowed from:

* [Akarin](https://github.com/Akarin-project/Akarin)
* [EMC](https://github.com/starlis/empirecraft)
* [Lithium](https://github.com/jellysquid3/lithium-fabric)
* [Origami](https://github.com/Minebench/Origami)
* [Airplane](https://github.com/Technove/Airplane)
* [Cadmium](https://github.com/LucilleTea/cadmium-fabric)
* [Tic-Tacs](https://github.com/Gegy/tic-tacs)
{% endtab %}
{% endtabs %}

### [Fabric](https://fabricmc.net/)

...

### [Forge](https://files.minecraftforge.net/net/minecraftforge/forge/)

...

### [Sponge](https://www.spongepowered.org/)

...

### [Magma](https://magmafoundation.org/)

...

### [Glowstone](https://glowstone.net/)

...

## Hosting Options

...

## Creating a Purpur Server

...

### Grabbing The Jar

...

### Creating a Start File

...

### Accepting The EULA

...

### Exploring The Configs

Add links to info about server.properties, bukkit.yml, spigot.yml, paper.yml, purpur.yml, etc.

...

## Server Security

Explain how one shouldn't use illegitimate mods, plugins, server software, or clients, explain online mode, etc.

...

## FAQ \(Frequently Asked Questions\)

### Q: "How can I change the server port?"

A: Find the `port` value in `server.properties` and set it to the desired port number.

...

## Projects

Projects are step-by-step text and video tutorials that are used to better understand a topic.

...

