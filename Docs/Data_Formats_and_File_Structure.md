# Data Formats and File Structure

## Core Formats
- **JSON** — Encounter graphs, dungeon layouts, loot tables, condition blocks, and exported Event Editor payloads.
- **ScriptableObjects** — Abilities, hero classes, enemy archetypes, combat modifiers, progression curves, and configuration sets.
- **CSV** — Localization keys, narrative text, tutorial tips, and UI strings.
- **PNG/FBX** — UI atlases, concept art references, 3D models, rigs, and animation clips.

## Directory Map
- `Assets/HexRegions` — Hex-grid region data, tile prefabs, biome settings, and prop bundles.
- `Assets/Combat` — Ability assets, VFX profiles, animation references, and status effect definitions.
- `Assets/Encounters` — JSON encounter files, branching graphs, rewards, and condition sets.
- `Assets/Dungeons` — Procedural generation rules, room templates, biome modifiers, and boss room setups.
- `Assets/UI` — UI prefabs, layouts, fonts, and icon atlases.
- `Assets/Characters` — Hero/enemy models, rigs, textures, skinning profiles.
- `Scripts/Core` — Bootstrap scene logic, service locators, save/load entry points.
- `Scripts/Systems` — Gameplay system implementations for combat, exploration, progression.
- `Scripts/ContentRuntime` — JSON loaders, validators, schema contracts, and runtime DTOs.
- `Scripts/ToolsRuntime` — Editor hooks and shared utilities consumed by in-editor tools.
- `Tools/EventEditor` — Source code and UI layouts for Event Editor v2, including exporter logic.
- `Tools/DungeonGenerator` — Procedural tooling for designers to author and preview dungeon seeds.
- `Tools/BuildPipeline` — Local developer helpers for tagging builds and generating patch notes.
- `BuildPipeline/ci_config` — CI/CD configuration templates and environment files.
- `BuildPipeline/scripts` — Build and packaging scripts, versioning helpers, and distribution notes.

## Schema Notes
- Encounters should reference heroes/enemies by **stable IDs**, not names.
- Loot tables define rewards as **weighted entries**; drops reference currency/item IDs defined in progression data.
- Dungeon JSON stores **seed data** and **rule sets** separately to allow deterministic replays.
- Localization CSV files must include **language code columns** and fall back to English.

## Authoring Conventions
- Keep JSON human-readable: 2-space indent, sorted keys where possible.
- Store ScriptableObjects under folders that mirror runtime namespaces for easy lookup.
- Every new data schema requires a short README adjacent to the folder describing fields and ownership.
