# Build Pipeline

## Purpose
Automates nightly and milestone builds, tagging, changelog generation, and artifact publication.

## Stages
1. **Validation**: lint, code formatting, schema checks, and play-mode/unit tests.
2. **Build**: platform-specific Unity builds, addressable content packing, version stamping.
3. **Packaging**: zip installers, Steam depot upload (stub), checksum generation.
4. **Publish**: notify QA/Slack, attach changelog, archive symbols for crash reporting.

## Branching & Triggers
- **Nightly**: runs from `main` at 02:00 UTC; artifacts tagged `nightly-<date>`.
- **Milestone**: manual trigger for Demo/Beta/EA/Release branches; require green validation stage.
- **Hotfix**: branch `hotfix/*` triggers slim pipeline (validation + platform build + publish).

## Inputs & Outputs
- Inputs: Unity version pin, addressable profiles, signing credentials (secure storage).
- Outputs: build artifacts per platform under `BuildPipeline/artifacts`, version metadata JSON, changelog entry.

## Testing Notes
- CI dry-run step for build scripts to catch path/config regressions.
- Smoke install test on target PC spec for milestone builds.
- Track build duration to guard against regressions.
