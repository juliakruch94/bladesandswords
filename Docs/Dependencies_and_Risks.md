# Dependencies and Risks

## System Dependencies
- **Combat** depends on **Progression** and **Content System** for abilities, stats, and enemy definitions.
- **Exploration** depends on **HexRegions** and **Encounters** for region data and triggers.
- **Dungeon Generator** depends on **Content System** for biome templates, enemy pools, and boss definitions.
- **Event Editor v2** depends on **Content System** for schema definitions and exports consumed at runtime.
- **Build Pipeline** depends on **ToolsRuntime** for version tagging and build metadata.

## Risks and Mitigations
- **Dungeon generation complexity** may cause memory spikes
  - Use pooling, LOD, and cap maximum active rooms/nodes.
- **Event Editor v2 delays** could bottleneck content production
  - Ship an MVP early, iterate UI/UX later, and keep JSON schema stable.
- **Build pipeline failures** can slow QA and milestones
  - Nightly CI runs with notifications; keep build scripts versioned and documented.
- **Overuse of ScriptableObjects** without clear ownership can lead to hidden coupling
  - Establish ownership conventions and keep references one-directional.

## Ownership
- **Tech Lead / Architect** — Maintains architecture docs in `/Docs`.
- **Gameplay Programmers** — Own systems under `Scripts/Systems` and their tests.
- **Tools Engineer** — Owns `Tools/EventEditor`, `DungeonGenerator`, and build tooling.
- **Producers** — Track milestone risks and ensure CI/build health stays green.
