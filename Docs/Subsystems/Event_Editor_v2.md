# Event Editor v2

## Purpose
Internal tool for authoring branching encounters, dialogue, and rewards, exporting JSON consumed by Content Runtime.

## Feature Highlights
- **Graph authoring UI** with node templates (dialogue, check, reward, combat hook).
- **Schema validation** against Content System contracts with inline errors.
- **Localization preview** with key resolution and fallback visualization.
- **Versioned exports** with GUIDs to keep references stable across edits.

## Data Flow
1. Designer creates/edits an encounter graph.
2. Tool validates against schemas from `Docs/` and `Scripts/ContentRuntime`.
3. Exporter writes JSON to `Assets/Encounters` and updates changelog notes in `Tools/EventEditor`.
4. CI lint step re-validates changed graphs before merge.

## Integration Points
- Exposes **export hooks** for build pipeline to package latest content.
- Shares **schemas** with runtime loaders; breaking changes require a version bump and migration notes.
- Emits **analytics events** for tool usage to monitor throughput (optional).

## Testing Notes
- Editor tests for graph serialization/deserialization parity.
- Schema regression suite run in CI when schemas change.
- Manual smoke tests for localization preview per release.
