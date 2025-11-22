# Combat System

## Purpose
Turn-based engine responsible for initiative, ability resolution, status effects, and combat outcomes.

## Pipelines
1. **Battle Bootstrap**: seeds combatants from Content System definitions, applies Progression stats, and registers turn controller.
2. **Initiative Loop**: maintains ordered queue; supports interrupts and delay mechanics.
3. **Ability Resolution**: deterministic pipeline (targeting → cost check → effect bundling → VFX hooks → result events).
4. **Status Engine**: stackable modifiers with lifecycle callbacks (on-apply, on-turn, on-expire), referenced by GUID.
5. **Outcome Handling**: victory/defeat triggers, loot/XP attribution, and save hooks.

## Data Contracts
- **Ability SO**: costs, targeting rules, effect blocks (damage, heal, apply-status, spawn).
- **Combatant Sheet**: derived stats after Progression buffs; includes resistances and AI behavior flags.
- **Status Definition**: ticking rules, stacking policy, dispel tags, and serialization ID.

## Interfaces & Events
- Public API: `ICombatService`, `IStatusService`, `ITurnController` under `Scripts/Systems/Combat`.
- Consumes Progression System for stats and Content System for enemy definitions.
- Emits combat log events, animation requests, and post-battle rewards to UI/Progression.

## Testing Notes
- Deterministic seed-based tests for initiative and ability resolution.
- Snapshot tests for status stacking and cleanse/expire behavior.
- Performance budget: < 0.5s per action on target hardware.
