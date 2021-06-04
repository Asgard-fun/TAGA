# The Asgard Game API

API for creating mini-games in minecraft.
Made by [The Asgard](https://asgrad.fun/) with love 💙 

[latest-version]: v1.1.0

[discord-invite]: https://discord.gg/QXSGvGrzDj
[discord-shield]: https://discord.com/api/guilds/646285836500860929/widget.png

[discord]: https://img.shields.io/badge/Our-discord-blue?style=for-the-badge&logo=discord

[version]: https://img.shields.io/badge/Version-v1.1.0-success?style=for-the-badge&logo=wiki
[download]: #how-to-use

[wiki]: https://img.shields.io/badge/-Our%20wiki-yellow?style=for-the-badge&logo=wiki
[wiki-url]: https://github.com/TheAsgard/TAGA/wiki

[docs]: https://img.shields.io/badge/Our%20documentation-v1.1.0-important?style=for-the-badge&logo=wiki
[docs-url]: https://github.com/TheAsgard/TAGA/wiki/Documentation

[![version][]][download]
[![wiki][]][wiki-url]
[![docs][]][docs-url]
[![discord][]][discord-invite]

## How to use

#### Requires **[PaperMC 1.16.5](https://papermc.io/downloads)** or **higher**.

> ###### For Maven
```xml
<repositories>
  <repository>
    <id>papermc-repo</id>
    <url>https://papermc.io/repo/repository/maven-public/</url>
  </repository>
  <repository>
    <id>sonatype</id>
    <url>https://oss.sonatype.org/content/groups/public/</url>
  </repository>
</repositories>
```
```xml
<dependencies>
  <dependency>
    <groupId>com.destroystokyo.paper</groupId>
    <artifactId>paper-api</artifactId>
    <version>1.16.5-R0.1-SNAPSHOT</version>
    <scope>provided</scope>
  </dependency>
  <dependency>
    <groupId>fun.asgard</groupId>
    <artifactId>TAGA</artifactId>
    <version>v1.1.0</version>
  </dependency>
</dependencies>  
```

____

> ###### For Gradle
```gradle
repositories {
  mavenCentral()
  maven {
    url 'https://papermc.io/repo/repository/maven-public/'
  }
}
```
```gradle
dependencies {
  compileOnly 'com.destroystokyo.paper:paper-api:1.16.5-R0.1-SNAPSHOT'
  implementation 'fun.asgard:TAGA:v1.1.0'
}
```

## Brief Guide

**PLEASE READ [ OUR DOCUMENTATION ][docs-url] ALSO! THIS GUIDE IS NOT ALL THE POSSIBILITIES OF OUR API!**

### Initialization

```java
public static TAGA taga;

@Override
public void onEnable() {
  taga = new TAGA(this);
}  
        
```

____

### Game manager

> ##### Create the Game

```java
//                                              |Get the world|         |Game name|    |Game time|
Game game = taga.getGameManager().createGame(Bukkit.getWorld("world"), "ExampleGame", 5 * 60 * 1000);

// If you want when a player is kicked, he is disconnected from the game ( Default is false )
game.setKickOnLeave(true);
```

> ##### Get the Game

```java
//                                          |Game name|
Game game = taga.getGameManager().getGame("ExampleGame");
```

> ##### Get all games

```java
//      |Name| |Game|
HashMap<String, Game> games = taga.getGameManager().getGames();
```

____

### Game

> ##### Connect a player to the game

```java
//               |The player|
game.connectPlayer(player);
```

> ##### Disconnect a player from the game

```java
//                  |The player|
game.disconnectPlayer(player);
```

> ##### Get game players

```java
game.getPlayers();
```

> ##### Start the Game

```java
game.start()
```

> ##### Stop the Game

```java
game.stop()
```

> ##### Shutdown the Game

```java
// If you don't want the GameStopEvent to work
game.shutdown()
```

> ##### Creating a task for the game

```java
game.runGameTask(() -> {
  game.getPlayers().forEach(player -> player.sendMessage("1 minute of the game has passed"))
//|Delay| |Period|
}, 1000, 60 * 1000)
```

**If you have any problems, write to us in the** 
[ ![discord-shield][] ][discord-invite]
