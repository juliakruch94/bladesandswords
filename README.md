# Runes & Swords — Game Project

This repository contains the full Unity project for **Runes & Swords**, a tactical narrative RPG with hex-based exploration, turn-based combat, progression systems, and post-release support (DLC, events, patches).

The repo is intended for programmers, technical designers, and tools engineers. High-level production docs (GDD, QA, publishing, business) live in Confluence and Miro. Here we keep **only the technical and implementation-facing documentation** needed to build and maintain the game.

---

## 📂 Repository Structure (High-Level)

```plaintext
Assets/
  HexRegions/          # Hex grid maps, region definitions, props
  Combat/             # Abilities, FX, animations, status effects
  Encounters/         # JSON encounter files, branching logic, rewards
  Dungeons/           # Procedural generation rules, room templates, biomes
  UI/                 # UI prefabs, layouts, icons
  Characters/         # Hero and enemy models, rigs, textures

Scripts/
  Core/               # Core engine glue, bootstrap, services
  Systems/            # Gameplay systems (exploration, combat, progression)
  ContentRuntime/     # Runtime loaders for encounters, regions, dungeons
  ToolsRuntime/       # In-editor tooling glue, custom inspectors

Tools/
  EventEditor/        # Source code & UI for Event Editor v2
  DungeonGenerator/   # Dungeon generation toolkit
  BuildPipeline/      # Build scripts, CI helpers, version tagging

Docs/
  System_Architecture.md
  Data_Formats_and_File_Structure.md
  Performance_and_Targets.md
  Dependencies_and_Risks.md

BuildPipeline/
  ci_config/          # CI/CD configs, templates
  scripts/            # Build & packaging scripts

ProjectSettings/      # Unity project settings
Packages/             # Unity package manifest
README.md
.gitignore
```

---

## 🧱 System Architecture Overview

The game uses a **modular architecture** built around clearly separated subsystems:

| Subsystem          | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| Exploration System | Handles hex-grid traversal, node discovery, encounter triggers.             |
| Combat System      | Turn-based engine with initiative queue, ability resolution, modifiers.     |
| Progression System | XP, leveling, talents, glyph upgrades, equipment tiers.                     |
| Content System     | Encounters, dialogue scripts, loot tables, region data.                     |
| Dungeon Generator  | Procedural generator for roguelite dungeon layouts, rules, biomes.          |
| Event Editor v2    | Internal tool for branching encounters and story beats.                     |
| Build Pipeline     | Automation for nightly/weekly builds, version tagging, changelog generation.|

Each subsystem is implemented as a set of **Unity components + ScriptableObjects + JSON data**, with minimal hard coupling between modules. Systems communicate through explicit interfaces and data contracts, not direct scene references where avoidable.

---

## 🗃 Data Formats & File Structure

### 3.1 Core File Types

- **JSON** — encounters, events, dungeon layouts, loot tables  
- **ScriptableObjects** — ability definitions, hero data, enemy stats, configuration sets  
- **CSV** — localization tables and text content  
- **PNG/FBX** — UI, 2D art, 3D assets, rigs, animations  

### 3.2 Project Directory Mapping

| Directory             | Purpose                                                                 |
|-----------------------|-------------------------------------------------------------------------|
| `Assets/HexRegions`  | Hex-grid region data, tiles, biomes, environmental props.              |
| `Assets/Combat`      | Combat abilities, VFX, animation clips, status effect assets.          |
| `Assets/Encounters`  | JSON encounter files, branching graphs, rewards, conditions.           |
| `Assets/Dungeons`    | Procedural rules, room templates, biome modifiers, boss room setups.   |
| `Tools/EventEditor`  | Editor window, graph UI, serializers for Event Editor v2.              |
| `BuildPipeline`      | Build scripts, CI configuration, version metadata and tagging helpers. |

---

## 🎯 Technical Requirements & Targets

The project targets **Unity LTS** on PC (Steam) as the primary platform.

### Performance Targets

- **Frame rate:** 60 FPS target on mid-spec PC in combat and exploration  
- **Load times:** `< 5s` for small regions, `< 12s` for large dungeon maps  
- **Memory usage:** ≤ 2.5 GB peak in complex combat scenarios  
- **Ability resolution:** combat ability resolution time `< 0.5s` per action  

### Platform Considerations

- **Primary:** Windows PC (Steam)  
- **Secondary (post-release):** macOS, Steam Deck optimization  

All heavy systems (procedural generation, encounter loading, large combat states) must respect these constraints.

---

## 🔗 System Dependencies

| System            | Depends On         | Notes                                                           |
|-------------------|--------------------|-----------------------------------------------------------------|
| Combat            | Progression, Content System | Abilities & stats come from progression trees and enemy data. |
| Exploration       | HexRegions, Encounters     | Movement on map triggers encounter definitions and events.    |
| Dungeon Generator | Content System     | Uses biome templates, enemy pools, boss definitions.           |
| Event Editor v2   | Content System     | Outputs JSON for encounters and story beats consumed at runtime.|

Dependencies should be **one-directional** where possible to avoid circular references and spaghetti initialization order.

---

## ⚠ Technical Risks & Mitigations

- **Dungeon generation complexity** may cause memory spikes  
  → Use pooling, LOD, and cap maximum active rooms/nodes.  

- **Event Editor v2 delays** can bottleneck content production  
  → Ship minimal viable version early, then iterate; keep JSON schema stable.  

- **Build pipeline failures** can silently slow down QA and milestones  
  → Nightly CI runs with notifications; keep build scripts versioned and documented.  

- **Overuse of ScriptableObjects without clear ownership** can lead to hidden coupling  
  → Establish conventions for who owns which asset groups, and how they are referenced.  

---

## 🧪 Testing & CI

- Core systems should have **play-mode tests** for combat, progression, and generation rules.  
- **Nightly builds** are run from `BuildPipeline/scripts` and pushed to internal branches.  
- Pre-release milestones (Demo, Beta, EA, Release) require green CI status and manual smoke tests.

---

## 👥 Ownership

- **Tech Lead / Architect** — maintains System Architecture & Dependencies docs in `/Docs`.  
- **Gameplay Programmers** — own systems under `Scripts/Systems` and their tests.  
- **Tools Engineer** — owns `Tools/EventEditor`, `DungeonGenerator`, and build tools.  

All changes to core systems should be reflected in the docs inside `/Docs` in the same PR.

