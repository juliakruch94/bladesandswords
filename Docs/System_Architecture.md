# System Architecture

## Overview
Runes & Swords follows a modular Unity architecture that isolates gameplay systems behind explicit interfaces and shared data contracts. Each system ships as a package-friendly folder inside `Scripts`, with ScriptableObject configuration assets in `Assets` and runtime JSON consumed through loaders in `Scripts/ContentRuntime`.

## Subsystems (Detailed Docs)
- **Exploration System** — Hex-grid traversal, fog-of-war updates, region discovery, and encounter triggering. See `Docs/Subsystems/Exploration_System.md`.
- **Combat System** — Turn-based loop with initiative queue, ability resolution pipeline, and status effect management. See `Docs/Subsystems/Combat_System.md`.
- **Progression System** — XP curves, talent trees, glyph upgrades, equipment tiers, and unlock conditions. See `Docs/Subsystems/Progression_System.md`.
- **Content System** — Encounter graphs, dialogue scripting, loot tables, region metadata, and boss setups. See `Docs/Subsystems/Content_System.md`.
- **Dungeon Generator** — Procedural ruleset for roguelite dungeons, biome selectors, room templates, and boss/key placements. See `Docs/Subsystems/Dungeon_Generator.md`.
- **Event Editor v2** — In-editor tool for building branching encounters that export JSON payloads consumed at runtime. See `Docs/Subsystems/Event_Editor_v2.md`.
- **Build Pipeline** — Nightly and milestone build automation with version tagging and changelog generation. See `Docs/Subsystems/Build_Pipeline.md`.

## Data Flow
1. **Authored data** lives in `Assets/` (ScriptableObjects) and `Assets/Encounters` (JSON).
2. **Content loaders** in `Scripts/ContentRuntime` deserialize JSON, validate schemas, and emit runtime models.
3. **Systems** in `Scripts/Systems` consume runtime models via interfaces; systems are registered through bootstrap code in `Scripts/Core`.
4. **ToolsRuntime** components expose editor hooks to keep runtime paths aligned with the Event Editor output.

## Communication Patterns
- Use **C# interfaces** for cross-system calls to avoid direct component coupling.
- Prefer **event channels** (UnityEvents or custom signals) for one-to-many notifications (e.g., combat turn changes, encounter outcomes).
- Keep **ScriptableObject references** one-directional: systems read configuration; they never mutate authored data at runtime.
- **Scene composition** uses a minimal bootstrap scene that loads additive content scenes per region/dungeon to keep memory stable.

## Ownership and Branching
- Core system changes require updates to docs in `/Docs` and notifications in build notes under `BuildPipeline/scripts`.
- Feature work branches from `main` into subsystem branches (e.g., `feature/combat-initiative`, `feature/event-editor-ui`).
- Tools and runtime code share interfaces so that the Event Editor can be developed independently of runtime releases.
