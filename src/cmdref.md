# Reference for Minecraft Commands

## What is this?

![readtime](https://img.shields.io/badge/6%20minutes%2033%20seconds-estimated%20read%20time-brightgreen)<br>
This is a documentation for Bedrock Minecraft commands, which is unofficial, written by VideoCarp.<br>
**Visit [Navigate](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#navigate) for easy navigation between commands.**<br>
**Are you a beginner?**<br>
If you've not been redirected from my other guide, click [here](https://gist.github.com/VideoCarp/24addfd65c82cb38009b5c34bfa2c188) for my beginner's guide.<br>
To show your appreciation, you can star this gist, or comment with feedback.<br>
Hate? Give me feedback in the comments, or by contacting me through my server (check below headline)

## Can I distribute this guide?

Please don't. Always put the link to this direct mdbook, the gist or otherwise contact me on discord, at [my server](https://discord.gg/4stpKau).

## Unofficial Mcfunction Documentation

This is also for commands, so do take it for that reason, this is not an official guide.
<span style="color: #ff0000">A dictionary is at the lowest part of the documentation, take a look at that if you do not understand some words.</span>

## Navigate

- [Entity Related](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#fully-entity-related-commands)
  - [Execute](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#execute)
  - [Testfor](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#testfor)
  - [Spreadplayers](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#spreadplayers)
  - [Tag](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#spreadplayers)
- [Block Related](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#block-related-commands)
  - [Testforblock](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#testforblock)
  - [Setblock](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#setblock)
  - [Fill](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#fill)
- [Other](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#other)
  - [Effect](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#effect)
  - [Teleport](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#teleport)
  - [Summon](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#summon)
  - [Clear](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#clear)
  - [Give](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#give)
  - [Tellraw](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#tellraw)
  - [Title](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#title)
  - [Particle](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#particle)
  - [Scoreboard](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#scoreboard)
- [Non-Commands](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#non-commands)
  - [Conditional](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#conditional)
  - [Manifest](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#manifest)
  - [Functions](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#functions)
- [Dictionary](https://gist.github.com/VideoCarp/eeaf915a2361d93f0fd8cf2c72d6db64#dictionary)

# Fully Entity Related Commands:

## Execute

<span style="color: #ff0000">The execute command is used to force entities to run commands. The command’s syntax is as the following without detect.</span><br>
`/execute <target> <location> <command> <selected command syntax>`<br>
The syntax with a detect is as the following:<br>
`execute <origin: target> <position: x y z> detect <detectPos: x y z> <block> <data: int> <command>`<br>
If the entity detects the block to detect on the detect position, the command will be executed.<br>
Gamepedia: [Click here to see gamepedia.](https://minecraft.gamepedia.com/Commands/execute)<br>

## Testfor

<span style="color: #ff0000">This command tests for entities, it can be used to activate conditional command blocks. If the testfor command finds the entity, the command is successful.</span><br>
This command can also be used to count entities.<br>
Command syntax:<br>
`/testfor <target>`<br>

## Spreadplayers<br>

<span style="color: #ff0000">This command teleports entities to surface within a specified area.</span><br>
Syntax:<br>
`/spreadplayers <x: value> <z: value> <spreadDistance: float> <maxRange: float> <victim: target>`<br>

## Tag<br>

<span style="color: #ff0000">Controls scoreboard tags for entities.</span><br>
Other Info regarding ”tag”:<br>
This can also be used to add certain tags on entities in the `[tag=tagname]` entity selecting part.<br>
Syntax:<br>
`tag <entity: targets> <add|remove> <name: string><br> tag <entity: targets> list`<br>
This command could be used to set-up a restriction for users other than OP. However, regular commands cannot change<br>
permissions

# Block Related Commands<br>

## Testforblock<br>

<span style="color: #ff0000">This command tests for whether a certain block is in a specific location. See testforblocks<br>
(with an S) for multiple block testfor. This command can be used to activate conditional command blocks.</span><br>
Command syntax:<br>
`testforblock <position: x y z > <Block> [dataValue]`<br>

## Testforblocks

<span style="color: #ff0000">This command tests whether the blocks in two regions match.You can use this for conditional command blocks.</span><br>
Command syntax:<br>
`testforblocks <begin: x y z> <end: x y z> <destination: x y z> [masked|all]`<br>
Arguments in masked/all.<br>
Specifies how to match blocks. Must be one of:<br>
all — every block in the source and destination regions must match exactly.<br>
masked — air blocks in the source region will match any block in the destination region.<br>
If not specified, defaults to all.<br>

## Setblock

<span style="color: #ff0000">Setblock is a command that places a block at the specified location.</span><br>
Syntax: <br>
`/setblock <location> <block> [data]`}<br>

## Fill

<span style="color: #ff0000">Fill is a command that places blocks from a specified location to another.</span>
`/fill <from: x y z> <to: x y z> <block> [data]`.<br>

## Other

## Effect

<span style="color: #ff0000">This command can add or remove status effects on players and other entities.<br>
You know what effects are, they’re just potion stuff.</span>
Syntax:<br>
Clear Effects<br>
`effect <player: target> clear`<br>
Add or remove an effect<br>
`effect <player: target> <effect: Effect> [seconds: int] [amplifier: int] [hideParticles: true/false]`<br>
Amplifier is the level of the effect. eg: strength 5 (amplifier).<br>

<br>
<br>

## Teleport

<span style="color: #ff0000">The teleport command teleports entities to a specified location, or another entity.<span style="color: #ff0000"><br>
<span style="color: #00ff00">Syntax Laws:<br>
Entity/ies can be teleported at once to one target.<br>
If an entity is requested to teleport to more than one target, the condition will fail.<br>
This can be used to determine if a mob has died.<br>
Multiple entities can teleport to one coordinate.</span><br>
Command Syntax:<br>
`teleport <victim> (location | target)`<br>
Advanced usage of the syntax is very complicated, click [here](https://minecraft.gamepedia.com/Commands/teleport#Syntax)<br>
for more information regarding advanced usage of the syntax.<br>

## Summon

<span style="color: #ff0000">The summon command is used to spawn in new entities into the world.<br>
Entities such as TNT can also be summoned with the /summon command.</span><br>
Syntax:<br>
With spawn event<br>
<br>
`summon <entityType: EntityType> [spawnPos: x y z] [spawnEvent: string] [nameTag: string]`
<br>
Without spawn event<br>
<br>
`summon <entityType: EntityType> [nameTag: string] [spawnPos: x y z]`
<br>

## Clear

<span style="color: #ff0000">The clear command is a command used to remove items from a player’s inventory.</span><br>
Syntax:<br>
<br>
`/clear <target> <item name> <data: integer> <maxCount>`
<br>
The data interval makes sure that the item matches the data interval, or the command will fail, this will not a trigger a<br>
conditional command block.<br>
To test for an item in a player’s inventory, use the following syntax:<br>
<br>
`/clear <target> <item name> <data> 0`<br>
<br>
The 0 will replace the command instead of deleting an item from a player’s inventory, it will check for one.<br>
<br>
<br>
<br>

## Give<br>

<span style="color: #ff0000">The give command allows users to obtain items normally unobtainable, or items that already<br> are through commands.</span><br>
Syntax:<br>
`give <player: target> <itemName: Item> [amount: int] [data: int] [components: json]`<br>
The cans for that are: (on bedrock)<br>
`{“can_place_on”:{“blocks”:[“BLOCK”]}}`<br>
`{“can_destroy”:{“blocks”:[“BLOCK”]}}`<br>
[Available arguments (gamepedia)](https://minecraft.gamepedia.com/Commands/give#Arguments)<br>

## Tellraw

This command sends a raw json message to the specified target. This appears without any external text, the message appears in chat alone, unlike a /say message.
Command Syntax (bedrock):
`/tellraw <target> <raw json message>`
The raw json message field is to be filled with something like this
`{“rawtext”:[{“text”:”your text”}]}`

## Title

<span style="color: #ff0000">The title command shows text onto the middle of the player’s screen, their action bar or under it as a subtitle.</span>
Syntax:
<br>
`/title <target> (title | subtitle | actionbar) <text>`
<br>
[View gamepedia syntax](https://minecraft.gamepedia.com/Commands/title#Syntax)

## Particle

Particle is an extremely useful and decorative command in Minecraft. It just adds cool particles and overall<br>
adds character. The syntax for it is:<br>
`/particle <effect> <location>`.<br>
But what if you wanted to use the location as a target entity? You can use the execute command for that.<br>
You can see a list of effects you can use [here](https://minecraft.gamepedia.com/Particles#Types_of_particles).

## Scoreboard

Scoreboard is an interesting command. It's also a very confusing one. Scoreboard is used to store the score of<br>
players in Minecraft, or maybe even entities if that's possible.<br>
To add an objective, use:<br>
`/scoreboard objectives add <objective: string> dummy [displayName: string]`<br>
and to change the value of an objective, use:<br>
`scoreboard players <set|add|remove> <player: target> <objective: string> <count: int>`.<br>
There are a lot of things, but those are the most basic.<br>
See [gamepedia](https://minecraft.gamepedia.com/Commands/scoreboard#Syntax) for more information.

# Non-Commands

## Conditional

<span style="color: #ff0000">Conditional command blocks are command blocks usually used in chains are command blocks that<br>
only work if the condition is met.<br>
These can be used in chains for shop systems and such.</span><br>
Scroll down in [official gamepedia](https://minecraft.gamepedia.com/Command_Block#Modification) a little bit<br>
until the Condition headline.

## Manifest

<span style="color: #ff0000">The manifest is a key file in all resource packs, worlds, behavior packs, etc. The manifest is what allows the pack to show on the list.</span>
Sources:<br>
[Bedrock Manifests](https://minecraft.gamepedia.com/Bedrock_Edition_add-on_documentation#manifest.json)<br>
[Bedrock Resources Manifest](https://pastebin.com/DXjv75sb)<br>
[Bedrock Behaviors Manifest](https://pastebin.com/zUFzsuVU)<br>

## Functions

Functions are a way to kinda import a ton of commands into new worlds easily, unlike command blocks however, they cannot be conditional.<br>
When you run the `function` command, it executes the .mcfunction file named by your argument.<br>
<br>
For example, a file named `cool_file.mcfunction` will execute if you return the argument as `cool_file` in other words,<br>
`/function cool_file` , however, if a different argument is written, the game will search for the .mcfunction named by<br> that, if none, the command will fail.<br>
<br>
.mcfunction files are always filled with nothing but commands.<br>
<br>
Now for the folder setup.<br>
<br>
Bedrock Edition:
<span style="color: #ff0000"></span>

> `(your pack name)`:open_file_folder:<br>
>
> > `(functions)`:open_file_folder:, `<manifest.json>`📄 , `<pack_icon.png>`📄<br>
> >
> > > `<filename.mcfunction>`:page_facing_up: <br>

##### Don't understand what each bracket means? Read the dictionary at the bottom.

# Dictionary

**How to Read Guide:**<br>
**1.** Syntax<br>
This means the format the command is used in.<br>
**2.** Manifest<br>
This is the file in which you’ll have for things such as texture packs or bedrock edition addons.<br>
**3.** <> bracketing in syntax<br>
This means that this part of the command is required for the specified use.<br>
**4.** () bracketing in syntax<br>
Separated by |, this means that this part of the syntax must be one of the things within the brackets.<br>
**5.** \[] bracketing in syntax<br>
This means that the part of the syntax is optional.<br>
**6.** Target<br>
This is the entity the command is being executed on.<br>
**7.** Entity<br>
An entity is a mob, a player, a dropped item, an armor stand, falling gravel/sand or anything in the game<br>
that isn’t in a completely solid state and fixed to it’s location.<br>
This may not be the best explanation for an entity, but you get the point.<br>
**8.** File Bracketing<br>
I use this to define a folder. Eg: `<file>, (folder)`<br>
In some cases I may also have an icon. ":page_facing_up:" means file, :open_file_folder: means folder.<br>
**9.** Integer
Normal integers are really just digits. In this case, integers are numbers still, but must be valid data values.

### Tags

Google search tags: `gist github mcfunction minecraft commands bedrock edition mcpe mcbe mc pe pocket edition learn commands function-pack videocarp guide syntax execute documentation docs carp video game minecraft learn commands syntax bedrock minecraft`
