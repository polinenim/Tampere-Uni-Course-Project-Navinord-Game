## License & Rights

This is a university project developed by four people and all the code rights are reserved for Tampere University i will update the content soon...

# NaviNord Game Project

NaviNord Game Project is a Unity-based virtual reality game project created for the Software Engineering Project course 610-620, Spring 2026. 
The project builds on the previous NaviNord research project, which was focused on multimodal research in a nordic forest VR setting.

The game is a roguelite VR looter-shooter set in a procedurally generated forest. The player navigates through the forest, finding different points of interest.
Through these points, the player fights enemies and loots items. With every location visited and every enemy killed, the player gains experience,
which can be used to acquire upgrades. Once the player makes it far enough, they encounter the final boss.

As time passes in the game, a wall (wall of gas) starts to advance further and further. If the player touches the gas, they take damage.
Usually, if the player is killed by enemies, they respawn at their most recent base, however, if their base is overrun by the gas,
they get sent back to the main menu, ending their current run.

In the main menu, the player can use their collected experience to upgrade their character.


## Project contents

- `Assets/GameImplementation/` - game-specific scenes, prefabs, player setup, items, gameplay code and more. Importantly containing:
  - `Assets/GameImplementation/Scenes/` - current game scenes
  - `Assets/GameImplementation/MVP_assets/` - earlier prototype and testing scenes
- `Assets/ThrirdParty/` - third-party assets and sample content included in the project
- `Assets/XR/` - XR platform, loader, OpenXR/Oculus and simulation config
- `Assets/Misc/` - miscellaneous settings and some shared assets

In general, the project is structured around the `Assets/GameImplementation/` folder. However


## Scenes

The game consists of three scenes:
- `vrMainMenu` - the main menu scene, where the player can spend their experience points on upgrades and start a new run.
- `miniProceduralLevel` - the main gameplay scene, where the player explores the procedurally generated forest, fights enemies and collects loot.
- `tutorial` - **UNFINISHED**, intended to be a tutorial scene that introduces the player to the game.

**Note:** If the game is run from the `miniProceduralLevel` scene, there will be errors, since in such a case the player upgrade
system is not loaded, which will result in non-existent upgrades and broken spawners (at least itemSpawners). Therefore, 
it is recommended to always launch it from the `vrMainMenu`.

Moreover, the project also includes a number of older scenes that were used for development and testing.
These can be found in the `Assets/GameImplementation/MVP_assets/` folder. 


## Implemented Systems and Content

### Core Gameplay Scripts

- `Scripts/PlayerState.cs` - Player health, spawn/respawn, death handling, audio feedback, and saveable player state.
- `Scripts/Player/` - Player movement, damage handling, hand calibration, and debug avatar tools.
- `Scripts/Enemy/` - Enemy AI, encounter spawning, bossfight logic, and enemy spawners.
- `Scripts/Items/` - Item definitions, inventory, health items, magazines, rarity, and item spawning.
- `Scripts/Player/Upgrades/` - XP, upgrade tokens, upgrade purchasing, upgrade effects, and upgrade UI.
- `Scripts/Saving/` - Binary world save/load, save metadata, saveable interfaces, and save helpers.
- `Scripts/UI/` - Scene loading, movement switching, and watch indicators for health, weight, and XP.
- `Scripts/RifleScope/` - Scoped weapon rendering.
- `Scripts/` - General gameplay scripts.

### Procedural World and Run Structure

- `chunkManager.cs` - Generates terrain chunks using seeded noise and multiple terrain resolutions.
- `riverGenerator.cs` - Generates river paths used by terrain shaping.
- `POIgenerator.cs`, `POIScriptableObject.cs`, `poiStructure.cs` - Handle point-of-interest data and placement.
- `WorldSeed.cs` - Manages world seed data.
- `dangerZone.cs` - Controls the advancing danger/wall pressure system.

### Content Assets

- `ItemS/` - Item ScriptableObjects, weapon assets, health item prefabs, icons, and enemy weapon assets.
- `Enemy/` - Enemy prefabs, materials, and animation/controller assets.
- `Player/` - Player prefab and related player assets.
- `POIs/` - Point-of-interest prefabs and structures.
- `EnvironmentAssets/`, `river/`, `MVP_assets/` - Environment art and world support assets.
- `Sounds/` - Gameplay audio clips.
- `UpgradeAssets/` - Icons used by the upgrade UI.

### VR, game UI and Interaction Support

- `HandPoses/` - UltimateXR hand pose assets for controllers and grab poses.
- `ItemSlot/` - Quick-access and item slot assets.
- `ArmMonitor/` - Wrist watch model, materials, and textures.
- `VrSim/` - VR simulator prefabs for development and testing.

### Editor Tools

- `Editor/` - Custom editor tools for terrain/procedural testing, inventory icon generation (right-click on a prefab and
see an option to auto create an icon of it), hierarchy coloring, pool manager editing, and forest stress testing.

### Important Notes

- Item setup has a dedicated README at `Scripts/Items/ItemsReadMe.txt`.
- Blender is required for some asset imports to work properly.


## Tech Stack

- Unity `6000.3.6f1`
- C#
- Universal Render Pipeline (URP)
- OpenXR
- Unity Input System
- UltimateXR


## Getting Started

### Requirements

- Windows development environment
- Unity Hub
- Unity Editor `6000.3.6f1`

### Open the Project

1. Open Unity Hub.
2. Add this repository as an existing project.
3. Install Unity Editor version `6000.3.6f1` if Unity Hub requests it.
4. Open the project and let Unity import packages and assets completely.
