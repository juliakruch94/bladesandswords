# Dungeon Generator

## Purpose
Procedurally creates roguelite dungeons with biome-aware layouts, pacing rules, and boss encounters.

## Pipeline
1. **Seed & Parameters**: accepts region/biome tags, difficulty, and player progression tier.
2. **Layout Graph**: generates room/corridor graph with gating rules (keys, shrines, elite rooms).
3. **Room Dressing**: assigns room templates, props, interactables, and encounter hooks.
4. **Validation Pass**: checks pathing, loot pacing, and ensures boss accessibility.
5. **Export**: produces JSON manifest consumed by Content Runtime loaders.

## Data Contracts
- **Biome Profile**: room templates, prop pools, enemy pools, ambient settings.
- **Generation Ruleset**: pacing curves, gate frequency, dead-end rates.
- **Dungeon Manifest JSON**: node graph, connections, triggers, boss data.

## Interfaces & Ownership
- Public API: `IDungeonGenerator`, `IDungeonValidationService` in `Scripts/Systems/DungeonGenerator`.
- Consumes Content System pools and Progression tiers to scale enemies/loot.
- Outputs manifests stored under `Assets/Dungeons` for runtime loading.

## Testing Notes
- Property-based tests for connectivity and gating constraints.
- Performance budget: generation under 2s for large maps on target hardware.
- Deterministic output when provided identical seeds and rule sets.
