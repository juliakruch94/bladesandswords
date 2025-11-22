# Exploration System

## Purpose
Provides hex-grid traversal, fog-of-war management, and trigger handling for region discovery and encounter initiation.

## Runtime Flow
1. **Region Bootstrap** loads hex data from `Assets/HexRegions` and registers grid services in `Scripts/Core`.
2. **Input Adapter** translates player input into movement intents with pathing constraints (movement points, blocked tiles).
3. **Traversal Resolver** updates actor position, emits `OnNodeEntered` events, and updates fog-of-war masks.
4. **Trigger Dispatcher** consumes encounter trigger volumes and pushes payloads into the Content System for validation.
5. **State Sync** writes lightweight snapshots for save/load and updates UI via event channels.

## Key Data Contracts
- **HexRegion JSON** — tile layout, biome tags, interactable nodes, metadata for travel costs.
- **Encounter Trigger** — `{ nodeId, encounterId, conditions[] }` stored alongside region data.
- **FogOfWar Mask** — compressed bitmask (per region) persisted in the save slot.

## Interfaces & Ownership
- Public API: `IHexTraversalService`, `IFogService`, `IEncounterTriggerService` (lives in `Scripts/Systems/Exploration`).
- Consumes Content System lookups for encounters and region metadata.
- Emits events to UI and Combat System (when a combat encounter is accepted).

## Testing Notes
- Pathfinding regression tests on sample regions.
- Serialization tests for fog-of-war masks and trigger states.
- Play-mode tests to confirm traversal cost budgets and blocklist behavior.
