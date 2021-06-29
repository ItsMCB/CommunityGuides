# Spigot Plugins

## About

The goal of this guide is to teach you the basics of the Spigot API and provide a bit of a history lesson along the way. Working with a new API can be scary, but fear not. I promise that you'll be able to create something you're proud of.

## Prerequisites

* Intermediate to advanced knowledge and experience with Minecraft
* Knowledge of how to setup a Minecraft Spigot server
* Basic understanding of a plugin's structure
* You've read the [general guidance](general-guidance.md) page.
* You've installed [Minecraft Dev](https://minecraftdev.org/) Intellij Plugin.

## Important Resources

Check out these resources to aid you in your development process.

* [Vexelosity Discord](https://discord.com/invite/QW2m6bYG4S)
* [SpigotMC Official Website](https://www.spigotmc.org/)
* [SpigotMC - "Tips on creating your very first plugin!"](https://www.spigotmc.org/wiki/tips-on-creating-your-very-first-plugin/)

## Projects

Here's the thing: reading about how to do something is one thing, but actually doing it is another. You need to actively practice coding to build and maintain your skills. This guide will outline some projects to assist you with that.

* [Beginner](spigot-plugins.md#beginner)
  * [My First Plugin](spigot-plugins.md#my-first-plugin)

### Beginner

Start here if you're just beginning your Minecraft plugin development journey.

### My First Plugin

This first project will be a barebones example of a plugin's structure. It will contain:

* 1 Registered Command
* 1 Registered Event
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

Here are you Spigot settings. Make sure that you select the correct Minecraft version before continuing.

{% hint style="info" %}
You should add relevant information in the optional settings panel if possible. It will automatically add it to relevant locations in your project, which could save you time later down the line.
{% endhint %}

![](https://i.imgur.com/BRIK0PV.png)

Choose a memorable name for your project and hit finish. You're now ready to start coding! Phew... that was a lot, right?

#### The Main Class

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

While you can use `System.out.println("Example message");` to print messages to the console, it's generally frowned upon. You should be using a logger.

...

#### Registering a Command

...

#### Registering an Event

...

#### Generating a Configuration file

...

#### Adding Dependencies

...

This guide is a work in progress. Feel free to [contribute](../contributing.md).

