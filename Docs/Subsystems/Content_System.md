# Content System

## Purpose
Supplies encounters, narrative beats, loot tables, and region metadata to runtime systems through validated data contracts.

## Responsibilities
- Validate and ingest **encounter JSON** and **dialogue scripts** authored by Event Editor v2.
- Provide **lookup services** for region data, enemy pools, boss definitions, and reward bundles.
- Manage **localization bindings** (CSV/JSON) and ensure string references resolve at runtime.
- Version schemas and run **lint checks** on content changes (pre-commit/CI).

## Data Contracts
- **Encounter JSON**: graph nodes, conditions, rewards, combat hooks, narrative lines.
- **Region Manifest**: biome tags, encounter tables, travel costs, ambient tracks.
- **Loot Table JSON**: weighted drops, rarity rules, currency bundles.
- **Localization Tables**: key/value per locale with fallback rules.

## Interfaces & Ownership
- Public API: `IContentService`, `IEncounterRepository`, `ILootTableService` in `Scripts/Systems/Content`.
- Consumed by Exploration (triggers), Combat (enemy definitions, rewards), and Dungeon Generator (biome rules).
- Tight coupling with Event Editor output; schema changes must be communicated to tools team.

## Testing Notes
- Schema validation tests using golden encounter files.
- Localization key coverage report in CI.
- Cross-check rewards against Progression constraints (currency caps, rarity rules).
