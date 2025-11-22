# Scripts
Entry point for runtime and editor-facing C# scripts. Systems are isolated by responsibility and remain package-friendly for Unity. Add assembly definitions per folder when bringing the project into Unity.

- `Core/` — Bootstrappers, service locators, save/load gateways.
- `Systems/` — Gameplay logic for combat, exploration, progression.
- `ContentRuntime/` — JSON loaders, validators, DTOs.
- `ToolsRuntime/` — Shared utilities consumed by in-editor tools.
