# Spigot Plugins

## About

The goal of this guide is to teach you the basics of the Spigot API and provide a bit of a history lesson along the way. Working with a new API can be scary, but fear not. I promise that you'll be able to create something you're proud of.

## Prerequisites

* Intermediate to advanced knowledge and experience with Minecraft
* Knowledge of how to setup a Minecraft Spigot server
* Basic understanding of a plugin's structure
* You've read the [general guidance](general-guidance.md) page.
* You've installed [Minecraft Dev](https://minecraftdev.org/) Intellij Plugin.

## Useful Resources

Check out these resources to aid you in your development process.

* [Vexelosity Discord](https://discord.com/invite/QW2m6bYG4S)
* [Bukkit Javadocs](https://hub.spigotmc.org/javadocs/bukkit/)
* [SpigotMC Official Website](https://www.spigotmc.org/)
* [SpigotMC - "Tips on creating your very first plugin!"](https://www.spigotmc.org/wiki/tips-on-creating-your-very-first-plugin/)
* [SpigotMC's Plugin.yml Guide](https://www.spigotmc.org/wiki/plugin-yml/)

## Projects

Here's the thing: reading about how to do something is one thing, but actually doing it is another. You need to actively practice coding to build and maintain your skills. This guide will outline some projects to assist you with that.

* [Beginner](spigot-plugins.md#beginner)
  * [My First Plugin](spigot-plugins.md#my-first-plugin)

### Beginner

Start here if you're just beginning your Minecraft plugin development journey.

### My First Plugin

This first project will be a barebones example of a plugin's structure. It will contain:

* 1 Registered Command with tab completion
* 1 Registered Event
* 1 Runnable \(background task\)
* Plugin.yml
* Config.yml
* 1 dependency

#### Creating The Project

Video Tutorial - Coming Soon

Download These First:

* [Intellij Idea](https://www.jetbrains.com/idea/) Community Edition \(free\)
* [Minecraft Dev](https://minecraftdev.org/) Intellij Plugin \(free\)

Open Intellij Idea. You should be greeted with a welcome screen similar to the following screenshot.

![](https://i.imgur.com/Sn6T1M0.png)

Click on "New Project". A window should popup. Select the Minecraft tab. Before continuing, lets make sure you have the right JDK \(Java Development Kit\). If you wish to develop a Minecraft plugin for 1.17+, you must use Java 16. Click on the Project SDK dropdown and view your installed JDKs. If you don't see something along the lines of "JDK 16", then you need to install it. You can do so very easily by clicking "Download JDK" in the dropdown. Intelij will grab a copy from the internet and add it to your project. Your screen should look like the following.

![](https://i.imgur.com/LQe2LoP.png)

Next, checkmark "Spigot Plugin" and then "Next".

{% hint style="warning" %}
"Oracle has licensed their own builds of the JDK under a license that requires you to pay for its use in a commercial setting. Instead, we recommend you download the JDK from [https://adoptopenjdk.net/](https://adoptopenjdk.net/). The builds provided there are roughly identical to those provided by Oracle, and there is virtually no reason to use Oracle's proprietary builds instead. If you need help installing, you can read more in [Paper's extensive guide](https://paper.readthedocs.io/en/latest/java-update/index.html)." - [Purpur ](https://discord.gg/mtAAnkk)Discord
{% endhint %}

You will now be presented with the build settings menu. Here, you can configure you package naming scheme and which build tool you'll be using. Maven is good, Gradle is good. Check out their websites if needed. For this tutorial, we'll be using Maven.

![Project Build Settings](https://i.imgur.com/u2q55jR.png)

The GroupId can be anything you want. However, it's best to keep these naming conventions in mind.

| Type | Typical Format | Example |
| :--- | :--- | :--- |
| Personal | me.&lt;username&gt; | me.itsmcb |
| Organization | org.&lt;organization name&gt; | org.mozilla |
| Network | net.&lt;network name&gt; | net.southhollow |

![](https://i.imgur.com/efjityF.png)

Here are your Spigot settings. Make sure that you select the correct Minecraft version before continuing.

{% hint style="info" %}
You should add relevant information in the optional settings panel if possible. It will automatically add it to relevant locations in your project, which could save you time later down the line.
{% endhint %}

![](https://i.imgur.com/BRIK0PV.png)

Choose a memorable name for your project and hit finish. You're now ready to start coding! Phew... that was a lot, right?

#### Explaining The Main Class

![](https://i.imgur.com/vpv0koF.png)

So you've got a similar screen to the one above. What even is all this? Well, lets break it down.

```java
package me.itsmcb.beginnerproject;
```

This tells Java what package the current file is.

```java
import org.bukkit.plugin.java.JavaPlugin;
```

This is importing a Java class that allows you to extend `JavaPlugin`.

```java
public final class BeginnerProject extends JavaPlugin {...}
```

This tells Java that the current class is extending `JavaPlugin`. This is what allows the plugin to initialize when you server loads up.

```java
    @Override
    public void onEnable() {
        // Plugin startup logic

    }

    @Override
    public void onDisable() {
        // Plugin shutdown logic
    }
```

These methods trigger when the server that the plugin is on starts up and shuts down respectively. You may be asking yourself, "What does `@Override` do?" Well, the `BeginnerProject` class \(subclass\) inherits the attributes and methods from the `JavaPlugin` class \(superclass\). You're telling Java to use your specialized behavior instead of the default/generalized behavior.

#### Using The Logger

While you can use `System.out.println("Example message");` to print messages to the console, it's generally frowned upon. You should be using a logger. While there are a handful to choose from, you can keep it simple and use the built-in [Bukkit Logger](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/plugin/PluginLogger.html).

Find the `onEnable()` method and log a message of your choice. For this example, we'll be logging "Hello World" to the console. We used `.info()` because we're logging general information. Try out `.warn()` or `.severe()` and see how the message changes.

```java
    @Override
    public void onEnable() {
        // Plugin startup logic
        this.getLogger().info("Hello world!");
    }
```

#### Building The Project

So far, the only thing this plugin does is log a message to the console. To ensure everything is good to go, lets build the project. If you're using Intellij, you can click the build button. If you see "BUILD SUCCESS", everything worked successfully. Congrats!

![](https://i.imgur.com/K54wou4.gif)

If you're using Maven, the plugin jar will be outputted to the project's `target` folder.

![](https://i.imgur.com/d7HxLtq.png)

#### Testing The Plugin

After you located the newly built jar, drag and drop it into the `plugins` folder on your Minecraft server. After you restart the server, you should see a message similar to the following with your plugin's name:

```java
[INFO]: [BeginnerProject] Enabling BeginnerProject v1.0-SNAPSHOT
```

If you're following the tutorial, you should see the message you logged in your code too. If you don't see any errors, then you know it loaded correctly. Congrats on making it this far!

{% hint style="info" %}
You can execute `/plugins` to view the plugins that the server tried to load last start up. Green indicates it loaded correctly while red indicates that it didn't.
{% endhint %}

#### Making Your Life Easier

Building a project, waiting for it to finish, shutting down the server, opening the directory that has the newly built plugin, dragging and dropping it into the plugins folder, and then finally restarting the server wastes so much time. Wouldn't it be great if there was a way to automatically copy the new jar? Well, there is. All you need to do is add a command that copies the file into your server start script.

Most operating systems can open Bash files. If you're on MacOS or Linux \(Windows too if you have a program that supports it like Git Bash\), you can use the following script **template** to do so. Please make sure to **edit the values before using the script**.

```bash
#!/bin/bash
while true; do
    rm "C:\Users\ItsMC\Desktop\Local Velocity Network\Server2\plugins\BeginnerProject-1.0-SNAPSHOT.jar" # Delete old plugin jar
    echo "[i] Copying the plugin..."
    cp -a "C:\Users\ItsMC\Desktop\Github\BeginnerProject\target\BeginnerProject-1.0-SNAPSHOT.jar" "C:\Users\ItsMC\Desktop\Local Velocity Network\Server2\plugins\\" # Copy jar from output folder to server's plugins folder
    java -Xms3G -Xmx3G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true -jar *.jar nogui #Launch the jar file in the directory w/3 gigs of RAM and implementing Aikar's Flags
    echo "[i] Restarting..." # Line ran after Java process has been stopped
    sleep 3 # Waits 3 seconds before restarting the server
done;
```

All you need to do is build the project, wait for it to finish, and then restart your server. So much easier than before, right?

#### Creating Commands

To ensure our project doesn't get messy, we'll be putting all our commands in a commands package \(folder\).

![](https://i.imgur.com/9pwAyqY.gif)



Commands can be executed from the player or the console.

...

#### Registering a Command

You will need to register a command executor in the main class and add the command to your plugin's `plugin.yml` file.

First, navigate to your main class. Under the `onEnable()` method, set a command executor.

```java
getCommand("spawnrandom").setExecutor(new SpawnRandom(this));
```

We getting the `spawnrandom` command and setting it's execution \(triggers when command is submitted\) to the class which handles it. We're passing the `this` Plugin instance so it can be accessed non-statically.

Lastly, navigate over to the `plugin.yml` file under the `resources` folder. You'll need to add your command in for it to register correctly. I suggest you include the following information:

```yaml
permissions:
  beginnerproject.spawnrandom:
    description: Allows you to spawn random mobs!
    default: op
commands:
  spawnrandom:
    description: Spawns a random mob!
    aliases: sr
    usage: /spawnrandom <amount>
    permission: beginnerproject.spawnrandom
    permission-message: Oops, you don't have permission to execute that command!
```

To get a better understanding of what these values mean, and to see even more of them, please visit [SpigotMC's Plugin.yml Guide](https://www.spigotmc.org/wiki/plugin-yml/).

#### Tab Completion

...

#### 

#### Registering Tab Completion

...

#### Creating Events

...

#### Registering an Event

...

#### Bukkit Runnables

...

#### Generating a Configuration file

...

#### Adding Dependencies

...

#### Common Issues

```java
[15:07:01 ERROR]: Could not load 'plugins\BeginnerProject-1.0-SNAPSHOT.jar' in folder 'plugins'
org.bukkit.plugin.InvalidPluginException: Unsupported API version 1.17...
```

You are trying to load the plugin on an unsupported server. If you're making a plugin with the 1.17 API, please make sure the Minecraft server jar is running Minecraft 1.17 and not 1.16 or below.

This guide is a work in progress. Feel free to [contribute](../contributing.md).

