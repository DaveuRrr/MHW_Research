# Monster Hunter World Research: Map Editing
010 Templates of Map Editing Research. Be sure to credit your source (Dave uRrr) for making this possible for your future Map (Environmental) Mods. Don't forget the Author of the Chunk Tool you used.

## About
Making my findings public and posting YouTube tutorials on **How To MHW Mod: Map Editing.** While this is a just the elemetry modding, in the future there will be a MHW Map Editor as a plugin with Blender.

## Prerequisites
If you plan to mod the game using my templates you should now there are some prerequisites you need to have before starting.
1. The game, Monster Hunter World. Hopefully you bought the game and are a support of the game. If you are not, don't talk to me.
2. You need a Chunk Tool. I recommend the WorldChunkTool by MHVuze https://www.nexusmods.com/monsterhunterworld/mods/6
3. You will need the 010 editor, it comes with a 30 day trial. While it's not free it's a great tool for hex editing. There are others but my template only works with 010 editor. If you find other editors that a free that read templates. Please let me know so I can update my tutorials. https://www.sweetscape.com/
4. Lastly, and I highly recommend this...If you don't get it it's because you like to struggle. I recommend you downloading and using the HelloWorld overlay for MHW. I ask for a personal request for him to add the Player coordinates so I could have an easier time modding SOBJs. You should be using his overlay. It's useful, it's highely customizable and it's great. Be sure to enable the DebugUI so you can access the Player Coordinates. https://www.nexusmods.com/monsterhunterworld/mods/142

## SOBJL (rSetObject List)
SOBJL is a list file that tell the game what to load. Here is where you can add your custom SOBJ entry instead of overwriting the ones that are currently in the game. This makes it easier for keeping the core game seperate from the mods with only the SOBJL modified. The list is index via int32 and you can tell it which order to load the gimmicks in. If it doesn't matter you can always make it -1.

## SOBJ (rSetObject)
SOBJ files are what spawns Objects, Players, Monsters, Creatures, items, etc. Each category has it's own specific command. There are a vast number of them and we will take a look at each one. To get started, download the git and make sure you place the rSetObject Folder in one place. Most `rSetObjects` will use the first coordinates to spawn the object with the exception of Monsters and Endemic Creatures. You want to be using the IB_SOBJ.bt file as it's the main file that pulls from all the other files. I did this to be better organized.

> ### cAssetBasicSetObject (Gimmick)
> Used to spawn interactable objects in the game. You can find the assets of these in the GM files which is `Assets/GM`. They have their own metadata in the Parameter Struct and each is pretermined by the list that is set in game. At this time, it is unknown how to add new GMs to the game. You can change the GM (Object) name but it doesn't pull from the folder path that you designate it to. Thre is a `mSubID` that is used to find the variation of the GM i.e. gm001_036_00 which the last 0 would be a gm001_036_01. `mGMUniqueID` is the GM identifier, I am unsure where you can find or create the unique id. You can find the GM list in `unit_resource`, it's more of a reference library from what I have gathered but needs more research.

> ### cEmSetter (Monster Boss)
> Used to spawn Monster via Quest, Expedition or custom. If you want to call a monster via quest understand that the file name is how it's called in the Quest. Monster ID, subspecies, stage, variant i.e. em001_00_st101_00.sobj. You can call a monster that doesn't normally spawn by adding it to the SOBJL list in the stage folder of adding it to the zako folder. It seems that the game knows to look at the zako folder for sobjl list. There is a limit for how many monsters can be in the game at once before you experience a Crash to Desktop. Depending on your system it can vary but on mine it's 7. If you want to push it you can go up to 12 but when you open up the map you will experience CTD. Some of the datatypes are still unknown, if you want to mess with them and find out what they are please let me know so I can update the information. Adding custom AIFSM scripts is currently unexplored.

> ### cEmGroupSetter (Smaller Monsters Zako)
> Used to spawn the smaller variant Monsters. They don't use the same structure as the Boss Monsters but they do spawn the same method as the Boss Monsters. I currently don't know what the limit is at this time of how many you can spawn at a time. I believe the last time I spawned about 20 of them.

> ### cEmDesireSetter (Routing)
> Used to assign the non-combat/combat routing. Not all actions are documented but the general one that is known is 9 which is where the monster goes to sleep. There are many action types and each monster has unique action IDs. They can vary from eating, sleeping, scratching, drinking water, etc. The action animation is occurences between the point A coordinates to point B.

> ### cEmRepopSetter (ReSpawn)
> Used to determine where the monster will respawn after the monster *Leaves the Locale*. It follows the same struct as `cEmSetter`.

> ### cFishingFloatSetter (Fishing)
> Unexplored at this time but I assume it's for where your fishing rod can float on the water.

> ### cOtGroupSetter (Grimalkynes)
> Used to spawn the group of 3 Grimalkynes. Only one of the actually interacts with you and joins you on your quest/expedition. If addition `cOtOtasukeSetters` or `OtRandomSetters` are placed you can add an additional `cOtGroupSetter` without experiencing a crash.

> ### cOtOtasukeSetter (Grimalkyne Helpers)
> Used to spawn the Grimalkyne helpers. The type as far as I know is RNG and pulls from your save file of what types are available. Even if you only level up one `Palico Unity` it still pulls from the RNG pull but you will just have no grimalkyne helpers spawn if you are missing a palico unity. Even raising up a `Palico Unity` more than others doesn't seem to effect the RNG.

> ### cOtRandomSetter (Grimalkyne/Palico)
> Used to spawn either a random grimalkyne from the `Palico Unity Set` or from the `Guild Card` friends.

> ### cOtPosSetter (Palico Sit)
> Used to place the Palico in one spot.

> ### cPlJumpPos (Player Spawn)
> Used to assign spawn coordinates to the player including other players (Multiplayer). The ID determines the spawn regardless of the Camps. 0 is often the beginning spawn, 1, 2, and 3 are variations of spawn such as returning from an expedition, quest or room. Higher integers are random assigned spawn points that are used for the HR RNG aka Drunk Bird.

> ### cSetAnimalArea (Endemic Creatures)
> Used to spawn Endemic Creatures but there are 3 types that are involved. One is the Endemic Creatures that you catch, second creatures that you collect for items such as beetles, and third interactable items such as Wedge Beetles. If you wish to add your own additional endemic creatures it's import to update the Radii Setup as it's used like LOD. It's a 5 point Radius system with the 5 point being the center. If you Radii is outside of the spawn coordinates your endemic creature will not appear. I believe it's around 10K that it disappears.

> ## cSetFishArea (Fish for Fishing)
> Used to spawn a variety of Fish in a given spot. The amount of fish can be added in a group by ID, with each fish type given it's own radii to swim around in. It's important for the radii to be updated but it's easier to copy an existing fish spawn. Fish can only spawn and float in areas with water collision. Otherwise they will never appear and fall into oblivion.

> ### cSetVillageNpcSetter (NPC)
> Used to spawn NPCs with specific parameters tied to the NPC. There is also a `cQuestNpcSetter` that uses the same struct as `cSetVillageNpcSetter`, you can use it to spawn certain npcs to your quest. While the NPCs will show up on your quest, adding custome dialogue will require futher tweaking which is beyond my map editing. If there are others that would like to explore this you are more than welcome to it. The first set of coordinates are the spawn coordinates and the second set is for the Camera (player position) to the NPC. Think of it like how Skyrim does it.

> ### cTerrainPoint (Unknown)
> What this command is used for is unknown at this time. Not sure if it's used by the monsters to determine where they are in the map but the Navway files are more so used for the NavigationPath. Nav/navway files are unexplored at this time.

> ### cTraceLogSetter (Unknown)
> Command unknown, could be tied to the footprints from the monsters.

> ### cNpcTraceLogSetter (Unknown)
> Command unknown, could be tied to the footprints from the First Wyverians

> ### cKimenTraceLogSetter (Unknown)
> Command unknown, could be tied to the footprints from the Grimalkynes.

> ### cWildCatTraceLogSetter (Unknown)
> Command unknown, could be tied to the footprints from the Grimalkynes.
