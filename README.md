# MineWorld-SDK

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![.NET](https://img.shields.io/badge/.NET-9.0-purple.svg)](https://dotnet.microsoft.com/)
[![Status](https://img.shields.io/badge/Status-In%20Development-yellow.svg)]()

**Official modding toolkit for creating content and plugins for MineWorld.**

MineWorld-SDK provides CLI tools, schemas, templates, and documentation specifically for MineWorld modders, texture artists, and content creators. It extends BlockCore-SDK with game-specific features and workflows.

---

## 🎯 What is MineWorld-SDK?

MineWorld-SDK is the **game-specific toolkit** for creating MineWorld content. It helps you:

- **Create mods** - Add custom blocks, items, recipes, biomes
- **Make texture packs** - Replace textures, sounds, UI
- **Build plugins** - Add gameplay features (teleport, economy, minigames)
- **Share content** - Package and distribute your creations

**Think of it as**: The official "MineWorld Mod Tools".

---

## 🚀 Quick Start

### Installation

```bash
# Install globally via dotnet tool
dotnet tool install -g MineWorld.SDK

# Or download standalone binary
# Windows: mineworld-sdk-win-x64.zip
# Linux: mineworld-sdk-linux-x64.tar.gz
# macOS: mineworld-sdk-osx-x64.tar.gz
```

### Create Your First Mod

```bash
# Scaffold a new plugin
mwtool new plugin MyMod --lang lua

# Add custom blocks
mwtool new data CustomBlocks --type blocks

# Create a texture pack
mwtool new resource MyTexturePack

# Validate your mod
mwtool validate ./MyMod --game MineWorld:^0.4

# Package for distribution
mwtool pack ./MyMod --out MyMod-1.0.0.zip
```

---

## 📦 What Can You Create?

### 1. Gameplay Plugins
Add new gameplay features:
- Teleport commands (`/home`, `/spawn`, `/warp`)
- Economy systems (shops, currency)
- Mini-games (parkour, PvP arenas)
- Custom game rules

**Example**: Home teleport plugin with `/home` and `/sethome`

### 2. Content Mods (Data Packs)
Add new game content:
- Custom blocks and items
- New recipes
- New biomes
- Custom ores and features

**Example**: Add copper ore and copper tools

### 3. Texture/Resource Packs
Change visuals and audio:
- Block textures (HD, stylized, themed)
- UI redesigns
- Sound replacements
- Custom music

**Example**: Medieval texture pack

### 4. Shader Packs
Custom visual styles:
- Cartoon/toon shading
- Realistic lighting
- Retro pixel art look

**Example**: Cinematic shader with bloom and HDR

---

## 📚 Documentation

- **🎓 Learning Path**: [Comprehensive guides](docs/learning/README.md) for developers transitioning from enterprise development to game modding tool development
- [Planning & Roadmap](docs/planning/overall.md) - SDK vision and roadmap
- [v0.1 Development Plan](docs/planning/v0.1.md) - Current milestone
- [Modding Guide](docs/modding/README.md) - Complete modding documentation
- [Plugin API Reference](docs/api/README.md) - Plugin development API
- [Content Creation Tutorials](docs/tutorials/README.md) - Step-by-step guides

---

## 🛠️ CLI Commands

| Command | Description |
|---------|-------------|
| `mwtool new <type> <name>` | Create mod/pack/plugin |
| `mwtool validate <path>` | Validate content |
| `mwtool pack <path>` | Package for distribution |
| `mwtool install <zip>` | Install to local MineWorld |
| `mwtool dev --watch` | Auto-reload on changes |

### Examples

```bash
# Create a teleport plugin
mwtool new plugin Teleport --lang lua

# Create custom blocks data pack
mwtool new data NewOres --type blocks

# Create HD texture pack
mwtool new resource HDTextures

# Validate plugin
mwtool validate ./Teleport --game ^0.4 --engine ^0.6

# Package mod
mwtool pack ./Teleport --out Teleport-1.0.0.zip

# Install for testing
mwtool install Teleport-1.0.0.zip --game-path ~/MineWorld
```

---

## 📋 Mod Types

### Plugin Manifest

```json
{
  "id": "author:mod_name",
  "name": "My Mod",
  "version": "1.0.0",
  "type": "plugin",
  "engine": "^0.6",
  "game": { "MineWorld": "^0.4" },
  "entry": "main.lua",
  "side": "server",
  "permissions": ["commands.register", "players.teleport"],
  "capabilities": ["chat", "storage"]
}
```

### Data Pack Example (Custom Block)

```json
{
  "mineworld:copper_ore": {
    "displayName": "Copper Ore",
    "model": "cube_all",
    "textures": {
      "all": "mymod:blocks/copper_ore"
    },
    "hardness": 3.0,
    "tool_required": "pickaxe",
    "tool_level": "stone",
    "drops": {
      "default": "mineworld:raw_copper"
    },
    "tags": ["ore", "stone"]
  }
}
```

---

## 🎓 Tutorials

- [Your First Plugin (5 minutes)](docs/tutorials/first-plugin.md) - Create a simple plugin
- [Adding Custom Blocks](docs/tutorials/custom-blocks.md) - Add new block types
- [Creating a Texture Pack](docs/tutorials/texture-pack.md) - Custom textures and models
- [Biome and Worldgen Modding](docs/tutorials/biome-modding.md) - Modify world generation
- [Publishing Your Mod](docs/tutorials/publishing.md) - Share your creations

---

## 🌟 Featured Mods

- **Home Teleport** - `/home` and `/sethome` commands
- **Copper Expansion** - Adds copper ore and tools
- **Medieval Textures** - Complete medieval theme pack
- **Minimap Plugin** - Client-side minimap

*(All coming with v0.1 release as examples)*

---

## 🤝 Contributing

We welcome contributions! Whether you're improving the SDK or creating example mods:

### Development Setup

```bash
# Clone the SDK repository
git clone https://github.com/DandelionBold/MineWorld-SDK.git
cd MineWorld-SDK

# Build the CLI tool
dotnet build

# Run tests
dotnet test

# Install locally for testing
dotnet pack
dotnet tool install --global --add-source ./nupkg MineWorld.SDK
```

---

## 🔗 Related Projects

- [**MineWorld**](https://github.com/DandelionBold/MineWorld) - The game itself
- [**BlockCore**](https://github.com/DandelionBold/BlockCore) - The engine
- [**BlockCore-SDK**](https://github.com/DandelionBold/BlockCore-SDK) - Engine extension toolkit

---

## 📄 License

MineWorld-SDK is licensed under [MIT License](LICENSE).

Example mods and templates are licensed under [CC BY 4.0](LICENSE-CC-BY-4.0).

---

## 🌟 Related Projects

### Game Target
- **[MineWorld](https://github.com/DandelionBold/MineWorld)** - Game that MineWorld-SDK extends
  - Game-specific content and mechanics
  - Modding API and hooks
  - [Game Documentation](https://github.com/DandelionBold/MineWorld/blob/main/docs/learning/README.md)

### Engine Foundation
- **[BlockCore](https://github.com/DandelionBold/BlockCore)** - Game engine powering MineWorld
  - Core rendering and physics
  - Plugin architecture
  - [Engine Documentation](https://github.com/DandelionBold/BlockCore/blob/main/docs/learning/README.md)

### Engine-Level Tools
- **[BlockCore-SDK](https://github.com/DandelionBold/BlockCore-SDK)** - Engine extension toolkit
  - Advanced plugin development
  - Engine-level modifications
  - [SDK Documentation](https://github.com/DandelionBold/BlockCore-SDK/blob/main/docs/learning/README.md)

---

## 💬 Community

- GitHub Issues: Bug reports and feature requests
- Discussions: Modding questions and showcase
- Discord: Modding community

---

**Create. Mod. Share. Welcome to MineWorld-SDK.**

