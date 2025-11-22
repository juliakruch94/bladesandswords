# Progression System

## Purpose
Manages player growth: XP curves, level rewards, talent trees, glyph upgrades, and equipment tiers.

## Responsibilities
- Compute **derived stats** for heroes by combining base sheets, gear, glyphs, and temporary buffs.
- Apply **unlock logic** for abilities/talents with dependency checks and class restrictions.
- Track **currencies** (gold, shards) and **account-level unlocks** for cosmetics or meta-progression.
- Emit **saveable deltas** for stat recalculation on load.

## Data Contracts
- **Hero Sheet SO**: base stats, class tags, talent tree identifiers.
- **Talent Tree JSON**: nodes, costs, prerequisites, granted abilities/modifiers.
- **Glyph/Equipment Definitions**: rarity, stat ranges, socket rules, upgrade steps.
- **Progress Snapshot**: hero level, XP, unlocked nodes, equipped items, account currencies.

## Interfaces & Events
- Public API: `IProgressionService`, `IStatAggregator`, `IInventoryService` in `Scripts/Systems/Progression`.
- Consumes loot and reward payloads from Combat and Content Systems.
- Provides final stat blocks to Combat and Exploration (movement budgets, resistances, checks).

## Testing Notes
- Unit tests for talent prerequisite resolution and XP curve boundaries.
- Serialization tests to ensure snapshot compatibility across versions.
- Balance sanity checks: simulate power curves and flag outliers.
