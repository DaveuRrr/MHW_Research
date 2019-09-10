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

## SOBJ (SetObject)
SOBJ files are what spawns Objects, Players, Monsters, Creatures, items, etc. Each category has it's own specific command. There are a vast number of them and we will take a look at each one. To get started, download the git and make sure you place the rSetObject Folder in one place. I'll try to update this weekly so stay tuned for future templates.

> ### NPCs (cSetVillageNpcSetter)
> We'll start with the first one which is **cSetVillageNpcSetter.** This sobj command is used to set NPCs with specific parameters tied to the NPC. There is also a **cQuestNpcSetter** that uses the same struct as **cSetVillageNpcSetter**, you can use it to spawn certain npcs to your quest. While the NPCs will show up on your quest, adding custome dialogue will require futher tweaking which is beyond my map editing. If there are others that would like to explore this you are more than welcome to it.
