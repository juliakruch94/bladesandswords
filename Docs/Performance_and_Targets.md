# Performance and Targets

## Platform Focus
- **Primary:** Windows PC (Steam)
- **Secondary (post-release):** macOS, Steam Deck optimizations

## Performance Goals
- Frame rate: **60 FPS** target on mid-spec PC in combat and exploration.
- Load times: **< 5s** for small regions, **< 12s** for large dungeons.
- Memory usage: **≤ 2.5 GB** peak during complex combat scenarios.
- Ability resolution: **< 0.5s** per action.

## Measurement Guidelines
- Use Unity Profiler captures during **representative scenarios**: large dungeon traversal, boss fights with multiple VFX, and branching encounter resolution.
- Track **GC allocations** per turn and per exploration step; budget allocations to prevent spikes during AI-heavy turns.
- Maintain **LOD and pooling** budgets for props, enemies, and VFX; document overrides in `Assets/Combat` or `Assets/Dungeons`.

## Optimization Checklist
- Disable unused systems in additive scenes to reduce overhead when exploring vs. fighting.
- Ensure **addressable assets** are grouped by biome/region to minimize unnecessary loads.
- Cap **max active rooms/nodes** for procedural maps to keep memory stable; unload distant rooms aggressively.
- Pre-bake **navigation data** for static hex regions and cache pathfinding graphs.
- Use **burst/Jobs** for heavy simulation steps where appropriate; gate with platform checks.

## Reporting
- CI should surface **performance regressions** via profiler snapshots on nightly builds.
- Document any deviations from targets in milestone build notes under `BuildPipeline/scripts`.
