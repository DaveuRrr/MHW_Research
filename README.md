# Monster Hunter World Research: Map Editing
010 Templates of Map Editing Research. Be sure to credit your source (Dave uRrr) for making this possible for your future Map (Environmental) Mods. Don't forget the Author of the Chunk Tool you used.

## About
Making my findings public and posting YouTube tutorials on **How To MHW Mod: Map Editing.** While this is a just the elemantry modding, in the future there will be a MHW Map Editor as a plugin with Blender.

## Prerequisites
If you plan to mod the game using my templates you should now there are some prerequisites you need to have before starting.
1. The game, Monster Hunter World. Hopefully you bought the game and are a support of the game. If you are not, don't talk to me.
2. You need a Chunk Tool. I recommend the WorldChunkTool by MHVuze https://www.nexusmods.com/monsterhunterworld/mods/6
3. You will need the 010 editor, it comes with a 30 day trial. While it's not free it's a great tool for hex editing. There are others but my template only works with 010 editor. If you find other editors that a free that read templates. Please let me know so I can update my tutorials. https://www.sweetscape.com/
4. If you like to struggle you are good to go but you can optionally download and install Cheat Engine. Now I personally don't condone cheating but Squall8 and Seikur0 have made an excellent Teleport tool that I've used for a while now. If it ends up breaking I will try to figure out how to get it back to work when Iceborne hits but honestly...I can't guarantee it. (You will have to try to figure this one out for yourselve) If all else fails google it.

## SOBJ (SetObject)
SOBJ files are what spawns Objects, Players, Monsters, Creatures, items, etc. Each category has it's own specific command. There are a vast number of them and we will take a look at each one.

> ### NPCs (cSetVillageNpcSetter)
> We'll start with the first one which is **cSetVillageNpcSetter.** This sobj command is used to set NPCs with specific parameters tied to the NPC. There is also a **cQuestNpcSetter** that uses the same struct as **cSetVillageNpcSetter**, you can use it to spawn certain npcs to your quest.
