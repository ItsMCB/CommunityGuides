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
![](https://i.imgur.com/igYbvzR.png)

A forked version of vanilla Minecraft that includes support for Bukkit plugins.

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| Mojang | "It's complicated" | Dead | Bukkit API |

{% hint style="warning" %}
Bukkit was acquired by Mojang on February 28, 2012. However, this project has been ceased since Q3 2014 because of a DMCA takedown dispute. The project is dead, so use a continued forked version instead.
{% endhint %}
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
{% endtab %}
{% endtabs %}

### [Spigot](https://www.spigotmc.org/)

{% tabs %}
{% tab title="Information" %}
![](https://static.spigotmc.org/img/spigot.png)

The continuation of the CraftBukkit project that supports Spigot plugins.

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| SpigotMC Pty. Ltd. | [Open](https://hub.spigotmc.org/stash/projects/SPIGOT) | Alive | Bukkit & Spigot API |

| [bStats](https://bstats.org/global/bukkit) |
| :---: |


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
![](https://papermc.io/forums/uploads/default/original/1X/2231fcb14b1617df7d695126a68d3d86b45974cc.png)

"Paper is the next generation of Minecraft server, compatible with Spigot plugins, offering uncompromising performance."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [PaperMC](https://github.com/PaperMC) | [Open](https://github.com/PaperMC/Paper) | Alive | Bukkit, Spigot, and Paper API |

![](https://bstats.org/signatures/server-implementation/Paper.svg)

| [bStats](https://bstats.org/plugin/server-implementation/Paper/580) |
| :---: |
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
![](https://raw.githubusercontent.com/Tuinity/Tuinity/master/tuinity-logo.webp)

"Fork of Paper aimed at improving server performance at high playercounts."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [Tuinity](https://github.com/Tuinity) | [Open](https://github.com/Tuinity/Tuinity) | Alive | Bukkit, Spigot, and Paper API |

![](https://bstats.org/signatures/server-implementation/Tuinity.svg)

| [bStats](https://bstats.org/plugin/server-implementation/Tuinity/9505) |
| :---: |
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
![](https://blog.airplane.gg/static/4451c090fa09b673bbbb4196516c0745/a30db/hero.png)

"A stable, optimized, well supported 1.16.5 Paper fork."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [TECHNOVE](https://github.com/TECHNOVE) | [Open](https://github.com/TECHNOVE/Airplane) | Alive | Bukkit, Spigot, and Paper API |
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
![](https://repository-images.githubusercontent.com/184300222/14b11480-3303-11eb-8ca4-ea5711d942fb)

"Purpur is a drop-in replacement for Paper servers designed for configurability, new fun & exciting gameplay features, and high performance built on top of Tuinity"

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [pl3xgaming](https://github.com/pl3xgaming) | [Open](https://github.com/pl3xgaming/Purpur) | Alive | Bukkit, Spigot, and Paper API |

![](https://bstats.org/signatures/server-implementation/Purpur.svg)

| [bStats](https://bstats.org/plugin/server-implementation/Purpur) |
| :---: |
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
![](https://yatopiamc.org/static/img/yatopia-shiny.gif)

"Blazing fast Tuinity fork with best in class performance."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [YatopiaMC](https://github.com/YatopiaMC) | [Open](https://github.com/YatopiaMC/Yatopia) | Dead | Bukkit, Spigot, and Paper API |

![](https://bstats.org/signatures/server-implementation/Yatopia.svg)

| [bStats](https://bstats.org/plugin/server-implementation/Yatopia/8840) |
| :---: |


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

Upstream\(s\):

* Vanilla
* CraftBukkit
* Spigot
* Paper
* Tuinity​
{% endtab %}
{% endtabs %}

### [Fabric](https://fabricmc.net/)

{% tabs %}
{% tab title="Information" %}
![](https://fabricmc.net/assets/logo.png)

"Fabric is a lightweight, experimental modding toolchain for Minecraft."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [FabricMC](https://github.com/FabricMC) | [Open](https://github.com/FabricMC/fabric) | Alive | Fabric API |
{% endtab %}

{% tab title="Upstreams\(s\)" %}
* Vanilla
{% endtab %}
{% endtabs %}

### [Forge](https://files.minecraftforge.net/net/minecraftforge/forge/)

{% tabs %}
{% tab title="Information" %}
![](https://forums.minecraftforge.net/uploads/monthly_2021_03/forge_logo.png.d1ecf3ff5345b3d06cb4e8ae78c4406e.png)

"Forge is a free, open-source modding API all of your favourite mods use!"

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [MinecraftForge](https://github.com/MinecraftForge) | [Open](https://github.com/MinecraftForge/MinecraftForge) | Alive | Forge API |
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
{% endtab %}
{% endtabs %}

### [Sponge](https://www.spongepowered.org/)

{% tabs %}
{% tab title="Information" %}
![](https://docs.spongepowered.org/stable/en/_images/logo-spongepowered.png)



"A community-driven open source Minecraft: Java Edition modding platform."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [SpongePowered](https://github.com/SpongePowered) | [Open](https://github.com/SpongePowered/Sponge) | Alive | Sponge API |

| [bStats](https://bstats.org/global/sponge) |
| :---: |
{% endtab %}

{% tab title="Upstream\(s\)" %}
Sponge Vanilla:

* Vanilla

Sponge Forge:

* Vanilla
* Forge
{% endtab %}
{% endtabs %}

### [Magma](https://magmafoundation.org/)

{% tabs %}
{% tab title="Information" %}
![](https://i.imgur.com/zTCTCWG.png)

"Magma is the most powerful Forge server providing you with mods and Plugins using Spigot and Paper for Performance and Stability."

<table>
  <thead>
    <tr>
      <th style="text-align:left">Owner</th>
      <th style="text-align:left">Source Status</th>
      <th style="text-align:left">Project Status</th>
      <th style="text-align:left">Implements</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="https://github.com/MagmaFoundation">MagmaFoundation</a>
      </td>
      <td style="text-align:left"><a href="https://github.com/magmafoundation/Magma">Open</a>
      </td>
      <td style="text-align:left">Alive</td>
      <td style="text-align:left">
        <p>Bukkit, Spigot, and Paper API</p>
        <p>Forge API</p>
      </td>
    </tr>
  </tbody>
</table>

![](https://bstats.org/signatures/bukkit/magma.svg)

| [bStats](https://bstats.org/plugin/bukkit/Magma/5445) |
| :---: |
{% endtab %}

{% tab title="Upstream\(s\)" %}
* Vanilla
* CraftBukkit
* Spigot
* Paper
* Forge
{% endtab %}
{% endtabs %}

### [Glowstone](https://glowstone.net/)

{% tabs %}
{% tab title="Information" %}
![](https://raw.githubusercontent.com/GlowstoneMC/Glowstone/dev/etc/logo/logo.png)

"A fast, customizable and compatible open source server for Minecraft: Java Edition."

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [GlowstoneMC](https://github.com/GlowstoneMC) | [Open](https://github.com/GlowstoneMC/Glowstone) | Alive | ... |
{% endtab %}

{% tab title="Upstream\(s\)" %}
N/A - Glowstone's code is completely original.
{% endtab %}
{% endtabs %}

## Hosting Options

...

## Creating a Purpur Server

...

### Downloading The Jar

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

