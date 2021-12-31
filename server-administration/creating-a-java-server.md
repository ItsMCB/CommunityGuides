# Creating a Java Server

### About

Minecraft wouldn't be what it is today without it's [multiplayer features](https://help.minecraft.net/hc/en-us/articles/360035131391-How-to-Play-Minecraft-Multiplayer). Playing on servers with friends is a lot of fun, but what if you want to make your own server? From choosing your server software to setting up plugins \(or mods\), this guide will extensively cover how to create different types of Minecraft: Java Edition servers.

### Prerequisites

* A beginner to advanced understanding of Minecraft.
* Experience playing on a Minecraft server.

### Useful Resources

Check out these resources to aid you in your server ownership journey. Feel free to let them know we sent you there 😎

* [Discord - Martin's Community](https://discord.com/invite/QW2m6bYG4S)
* [Minecraft - How to Play Minecraft Multiplayer](https://help.minecraft.net/hc/en-us/articles/360035131391-How-to-Play-Minecraft-Multiplayer)
* [Reddit - Admincraft](https://www.reddit.com/r/admincraft/)

## Server Basics

### Choosing The Right Software

Choosing the right software is very important as it will define your limitations for features and performance. Luckily, there are tons of options to choose from. Before I give you a list of software, lets go over some important terms.

### What are "forks"?

This is a [Git ](https://en.wikipedia.org/wiki/Git)\(a [version control](https://en.wikipedia.org/wiki/Version_control) technology which is very popular in the development space\) term that refers to taking code and making a variant of it. An example of this is how Spigot uses code from Bukkit, but then adds their own code into the project. This means that the difference between the fork \(Spigot\) and the original is the code they created. However, without the original code \(The Bukkit plugin API\), Spigot wouldn't work properly because it's built on top of the original.

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

### What are "patches"?

Patches are code changes that optimize, fix things, or add new features.

#### Why Use Patches?

Patches are used as a work-around to avoid DMCA takedowns. For example, when you first run a Spigot server, it will download the Minecraft Jar and Bukkit code, then it'll inject the Spigot patches into them and then start the server. This is legal because they're not actually distributing the protected code, but rather just downloading the needed files and then injecting their changes into it.

#### When Did Projects Start Using Patches?

Projects like Spigot started using patches after the Bukkit DMCA takedown fiasco.

### What is "upstream" and "downstream"?

This is a Git term that refers to where a fork relative to the project or another fork. Lets use CraftBukkit and Paper as an example.

CraftBukkit -&gt; Spigot -&gt; Paper

CraftBukkit is upstream relative to Spigot and Paper. Paper and Spigot are downstream relative to CraftBukkit.

This becomes important when you start using forked versions of server software. For example, when Minecraft 1.17 came out, Paper couldn't begin work on migrating their patches. This is because they had to wait for Spigot to finish their updating first because Paper's patches are built on top of Spigot's.

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
| Mojang | It's complicated | Dead | Bukkit API |

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

The widely accepted continuation of the CraftBukkit project.

| Owner | Source Status | Project Status | Implements |
| :--- | :--- | :--- | :--- |
| [SpigotMC Pty. Ltd.](https://github.com/SpigotMC) | [Open](https://hub.spigotmc.org/stash/projects/SPIGOT) | Alive | Bukkit & Spigot API |

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

All you need to run a Minecraft server is a running computer with an operating system. While this gives you many options, not all will be satisfactory to your needs.

#### Home Hosting

The term "home hosting" refers to running or "hosting" your Minecraft server off a personal computer. A potential issue is that you'll need to share your computer's IP address \(reveals your approximate physical location\) so others can connect. While you could use something to mask it, such as TCP Shield \(which costs money\), there are other issues, such as your computer needing to be running 24/7 \(if you want the server to stay online\) and having to setup port forwarding. Home hosting is a popular option for those looking to experiment with setting up servers, are coding plugins, or only have a few trusted friends joining.

#### Shared Hosting

Shared hosting typically means you'll be renting cloud computing hardware to run your server. However, other servers will be running off the same computer. Performance may be degraded as the other servers could be hogging processing resources. However, sharing your hardware often means sharing the cost. You'll typically find it to be much cheaper than other options. Keep in mind that these services don't give you full system control, and you typically can run one server per plan. Shared hosting is a popular option for those looking for a cheaper server hosting solution for a single server.

#### Dedicated Hardware

Dedicated hardware typically means renting cloud computing hardware. However, you have full control \(root access\) over the system and aren't sharing it's resources with anyone. This is great as you can run as many things as the hardware can handle. It's worth noting that while one may be enough for smaller server networks, bigger ones, such as Hypixel, have a fleet of connected dedicated computers. This is a popular option for serious Minecraft server networks who are hosting more than one server at once with high player counts.

#### Other Options And Considerations

While those are the most widely used options, there are other ways to host a server that can be found online. The important thing to remember is that your server can scale, meaning that you can start off home hosting or shared hosting, and then move up to dedicated, or vice versa.

## Important Information About JDKs

Java is unsurprisingly the platform typically used to run Minecraft: Java Edition servers. Java is an evolving language, and that means new versions come out as time goes on. Code written for a specific version may not be compatible with an older or newer version. Your JDK, or Java Development Kit, includes a JVM, or Java Virtual Machine, that executes the Java bytecode. When you play Minecraft \(using the new launcher\), it loads up the correct JDK automatically. Server software doesn't come with a JDK, meaning you may need to set a compatible one up manually if it's not already installed.

### Where Should I Get My JDK?

Java is primarily developed by [Oracle](https://www.oracle.com/). You're able to download their JDK version from their website. However, it includes a license that states you must **pay** in order to use it in a commercial setting \(which you likely will be\). Luckily, you can instead download the JDK from [https://adoptopenjdk.net/](https://adoptopenjdk.net/). They do not require you to pay for commercial use, and their builds are closely identical to those provided by Oracle. There's virtually no reason to use Oracle's builds instead.

### Which JDK Do I Need?

Minecraft 1.12-1.16.5 requires Java 8 or "newer". Minecraft 1.17+ requires Java 16. However, there is nuance to this. For example, Forge for 1.12 doesn't work with Java 11. Unless you'll be running a 1.17+ server, you may want to install Java 8, Java 11, and Java 16 for when you need them. An easy way of using a particular JDK version is by finding it's directory, then passing your Java command. This works because it will execute with the binary in the directory instead of the system default.

### Linux Example

```bash
# Target the directory where the binary is so the Java command is executed there instead of the system default.

# Execute the "version" Java command with the Java 8 binary
/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -version

# Execute the "version" Java command with the Java 11 binary
/usr/lib/jvm/java-1.11.0-openjdk-amd64/bin/java -version
```

#### Example Output

```bash
openjdk version "1.8.0_292"
OpenJDK Runtime Environment (build 1.8.0_292-8u292-b10-0ubuntu1~20.10-b10)
OpenJDK 64-Bit Server VM (build 25.292-b10, mixed mode)

openjdk version "11.0.11" 2021-04-20
OpenJDK Runtime Environment (build 11.0.11+9-Ubuntu-0ubuntu2.20.10)
OpenJDK 64-Bit Server VM (build 11.0.11+9-Ubuntu-0ubuntu2.20.10, mixed mode, sharing)
```

### What Happens If I Use The Wrong JDK?

If you see an error in the console upon startup, it may be because the JDK isn't compatible. Using the wrong JDK \(typically\) won't break anything, so don't worry if you do.

### Why Use a Newer JDK?

Each new release of Java includes important performance and security improvements. To get the most out of your server, you'll want to use the greatest compatible version. Ex. using Java 11 for a 1.14 server even though it could work with Java 8.

### How Do I Get a JDK for Java 16 on \_ operating system?

Paper has an extensive guide on it that you can view [here](https://paper.readthedocs.io/en/latest/java-update/index.html).

## Running The Server Software

### Downloading The Jar

Each project hosts their server jars differently, which can make finding them a tad complicated. It's often recommended to go to the project's official website and look for a "download" button and or read the `README.MD` of their GitHub repository.

![](https://i.imgur.com/HClBh6d.gif)



Move the jar into a folder. The folder name could be anything, but typically people make it "Minecraft Server" or the name of their server.

### Creating a Start File

To actually run the jar, you'll need to use a command. However, typing that command every time is inefficient. Luckily, you can create a script that will do it for you. Check out [SpigotMC's Installation Guide](https://www.spigotmc.org/wiki/spigot-installation/) for information about how to create a start script. If you're using multiple JDKs, refer to this [example](creating-a-java-server.md#linux-bash-example).

If you're able to use Bash, here is a basic start script that automatically restarts the server when it has stopped. Make sure to edit the RAM values \(`-Xms3G -Xmx3G` — this example allows the JVM to use 3 gigabytes of RAM\).

```bash
#!/bin/bash
while true; do
    java -Xms3G -Xmx3G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true -jar *.jar nogui #Launch the jar file in the directory w/3 gigs of RAM and implementing Aikar's Flags without a GUI
    echo "[i] Restarting in 3 seconds..." # Print msg to console
    sleep 3 # Wait 3 seconds before restarting the server
done;
```

### Accepting The EULA

Your server will not launch if you have not accepted the EULA. Here is how you can accept it:

1. Launch the server once, and when it fails, shut it down.
2. Locate the newly generated `eula.txt` file in the directory of the launched server.
3. Open it, and change "false" to "true", and save the file.
4. Restart your server.

### Editing The Port

By default, Minecraft servers will try to bind to port `25565`. This should be changed if someone is already using that port, such as another Minecraft server. You can do so by finding the `server.properties` file and then changing the `port` to the desired value.

#### Note About Ports

The maximum value for a [port ](https://en.wikipedia.org/wiki/Port_%28computer_networking%29)is `65535`. It's good practice to use a port number somewhere between 25565 and that maximum value, such as or `25570`.

### Exploring The Configs

Upon running the server, configuration files and folders will generate. The following are links to documentation about those files that may generate depending on the server software you're using.

* [server.properties](https://minecraft.fandom.com/wiki/Server.properties)
* [bukkit.yml](https://bukkit.fandom.com/wiki/Bukkit.yml)
* [spigot.yml](https://www.spigotmc.org/wiki/spigot-configuration/)
* [paper.yml](https://paper.readthedocs.io/en/latest/server/configuration.html)
* [tuinity.yml](https://github.com/Tuinity/Tuinity/wiki/Config)
* [purpur.yml](https://purpur.pl3x.net/docs/Configuration/)
* [glowstone.yml](https://docs.glowstone.net/en/latest/Configuration_Guide/glowstone_yml.html)

## Setting Up Plugins

### Finding Plugins

Bukkit plugin API based forks \(Spigot, Paper, etc.\) marketplaces:

* [SpigotMC Resources](https://www.spigotmc.org/resources/)
* [MC-Market](https://www.mc-market.org/)

If you're using Sponge Vanilla or Sponge Forge, check out the following marketplaces:

* [Ore platform](https://ore.spongepowered.org/)
* [SpongePowered Forums](https://forums.spongepowered.org/c/plugins/6)

{% hint style="info" %}
We do not endorse any of the platforms mentioned. They are simply listed for your convenience.
{% endhint %}

### Installing Plugins

Once you find a resource you want, download it, then move that file into the `plugins` directory of your server. If your server uses the Sponge API, put that plugin into the `mods` folder instead. To load the plugin, you'll need to shut down and then reboot your server.

### Editing Configs

Most plugins will have configuration files. Under the `plugins` directory, look for a newly generated folder. It will typically be called the name of the plugin. All the relevant configuration files for that plugin will be in that folder. You can open those files and edit the values to your liking. If you are unsure about a value, look for a configuration explanation on the plugin page. Some plugins will let you reload the config through a command, ex. `/coolplugin reload`. If not, reboot your server.

## Setting Up Mods

### Finding Mods

The two safest ways to get mods are to use [CurseForge ](https://www.curseforge.com/minecraft/mc-mods)or the mod author's official website.

### Editing Configs

Interestingly, most mods will generate folders that hold configurations outside of the mods folder. If you're looking to edit a config of a mod, look in the root of the server's folder.

## Server Security - Single Servers

### Online Mode

In the `server.properties` file, there is an option called `online-mode`. If enabled \(true\), then players will be authenticated through Mojang when they join. This ensures the player connecting has a legitimately purchased account. However, if it is disabled \(false\), the authentication doesn't happen. This means "cracked" or illegal/illegitimate accounts can join your server. For single server setups, it should always be true \(unless you want cracked accounts - which support piracy, and piracy is illegal\).

#### Why Disable Online-Mode?

Online-mode must be disabled for servers that are connected through a proxy such as Bungeecord or Velocity.

### "Cracked" Plugins

While many plugin marketplaces such as SpigotMC's resources section contains free plugins, some developers choose to make people pay for their resource. Certain websites offer "cracked" versions of premium plugins. This means you can download the plugin at a reduced price, or for free. **DO NOT EVEN THINK ABOUT DOING THIS.**

* It is unethical and ILLEGAL.
* If you're paying money, it goes to the person stealing the code instead of the actual developer.
* Those distributed jars contain malicious code; straight up malware, CPU miners, self-destruct scripts \(deletes all your server files\), etc.

There are additionally security concerns that will be covered in "Server Security - Proxy".

## FAQ \(Frequently Asked Questions\)

Based on actual questions I've been asked multiple times.

### Q: "How do I open an SQLite file?"

A: [https://sqlitebrowser.org/](https://sqlitebrowser.org/)

...

## Projects

Projects are step-by-step text and video tutorials that are used to better understand a topic.

### Creating a 1.17 Survival Server

One of the most common types of Minecraft server is a survival server. This project will lead you through which software you'll want to use and how to configure them.

...

### Creating a 1.12 Pixelmon Server

...

## Document Contributor\(s\):

* [ItsMCB](https://github.com/ItsMCB)

