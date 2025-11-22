# Milestones & Sample Issues

These milestone backlogs provide **fake-yet-plausible** issue placeholders you can paste into GitHub and attach to your existing Milestones/Projects. Each issue lists the recommended branch prefix, owner role, and acceptance hints to keep scope clear.

## Milestone: Demo (0.3.0)

- **Issue:** Combat initiative HUD prototype — display turn order with placeholder portraits and delay modifiers. (Branch: `feature/combat-initiative-ui`; Owner: Gameplay)
- **Issue:** Region discovery fog-of-war pass — reveal adjacent hexes, cache revealed state in save stub. (Branch: `feature/exploration-fog`; Owner: Gameplay)
- **Issue:** Event Editor export MVP — export single-node event JSON; validate against content schema stub. (Branch: `feature/tools-event-export`; Owner: Tools)
- **Issue:** Dungeon room stitching rules — connect pre-authored rooms with door markers and navmesh bake hook. (Branch: `feature/dungeon-stitching` ; Owner: Gameplay)
- **Issue:** CI nightly builder skeleton — add pipeline job that builds Windows player and archives artifacts. (Branch: `feature/ci-nightly-demo`; Owner: Build/DevOps)

## Milestone: Beta (0.6.0)

- **Issue:** Ability resolution logging — structured logs for combat actions (source, target, modifiers) written to JSON for replay. (Branch: `feature/combat-action-logs`; Owner: Gameplay)
- **Issue:** Talent tree progression save/load — persist unlocked talents and refund tokens on respec. (Branch: `feature/progression-talents-save`; Owner: Gameplay)
- **Issue:** Encounter condition editor UI — add branch conditions (flag checks, inventory checks) to Event Editor v2. (Branch: `feature/tools-conditions-ui`; Owner: Tools)
- **Issue:** Dungeon biome parameter packs — ScriptableObject sets for lighting, VFX, and spawn weights; toggle via debug dropdown. (Branch: `feature/dungeon-biomes` ; Owner: Gameplay)
- **Issue:** Build version stamping — inject semantic version and changelog excerpt into splash screen. (Branch: `feature/build-versioning`; Owner: Build/DevOps)

## Milestone: Early Access (0.9.0)

- **Issue:** Status effect stacking rules — configurable stacking modes with visual badges and tooltip deltas. (Branch: `feature/combat-status-stacks`; Owner: Gameplay)
- **Issue:** World map travel costs — movement AP costs per terrain type with hover previews and blocked node feedback. (Branch: `feature/exploration-travel-costs`; Owner: Gameplay)
- **Issue:** Dynamic loot tables — weightable loot pools per dungeon tier with seed-based determinism. (Branch: `feature/content-loot-pools`; Owner: Gameplay)
- **Issue:** Localization export/import — CSV roundtrip for UI strings and encounter text from Event Editor. (Branch: `feature/tools-localization`; Owner: Tools)
- **Issue:** Steam build/branch publish job — add CI step to push Early Access build to Steam beta branch after approvals. (Branch: `feature/build-steam-beta`; Owner: Build/DevOps)

## Milestone: Release (1.0.0)

- **Issue:** Boss encounter script pass — implement two boss ability timelines with telegraphs and enrage trigger. (Branch: `feature/combat-bosses`; Owner: Gameplay)
- **Issue:** Save system hardening — autosave slots, checksum, and corruption fallback for exploration/combat states. (Branch: `feature/platform-save-hardening`; Owner: Gameplay)
- **Issue:** Analytics events — emit core funnel events (start run, finish run, boss defeated) with offline queue. (Branch: `feature/platform-analytics`; Owner: Tools)
- **Issue:** Dungeon generator perf budget — profile generator and enforce frame budget with async slicing. (Branch: `feature/dungeon-perf-budget`; Owner: Gameplay)
- **Issue:** Release checklist automation — script that validates branch protection, tags, and changelog presence before GA. (Branch: `feature/build-release-checklist`; Owner: Build/DevOps)

## Milestone: Season 1 (Post-Launch)

- **Issue:** Seasonal event hub — add limited-time hub node with themed vendors and event hooks. (Branch: `content/season1-hub`; Owner: Content)
- **Issue:** New hero class: Rune Knight — baseline ability kit, progression tree, and placeholder animations. (Branch: `content/season1-rune-knight`; Owner: Content)
- **Issue:** Dungeon mutators — weekly rotating modifiers applied to dungeon seeds with UI badges. (Branch: `content/season1-mutators`; Owner: Content)
- **Issue:** Live ops dashboard — lightweight webview/editor window showing uptime, build versions, and feature flags. (Branch: `feature/tools-live-ops`; Owner: Tools)
- **Issue:** Crash telemetry pipeline — symbol upload and crash report forwarding to ELK stack. (Branch: `feature/build-crash-telemetry`; Owner: Build/DevOps)

---

**Usage tips**

- Create the issues with matching titles and attach them to the corresponding Milestone and Project columns.
- Use the suggested branch prefixes to align with the branching rules in `README.md`.
- Keep scope tight: each issue is designed to be completable within the milestone sprint window.
- Update subsystem docs in `Docs/Subsystems/` if any placeholder implementation details change.
