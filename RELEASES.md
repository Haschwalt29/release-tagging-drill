# Release Notes

These entries describe the tagged repository milestones. The available
deployment history does not confirm production deployment of these versions.

## v1.0.0 — 2026-06-06

Initial repository milestone.

### Added

- Added the placeholder checkout service and the assignment's baseline
  documentation.
- Added initial changelog, deployment-history, and incident-log records.

### Rollback target

No earlier known-good tagged version exists. The earlier production artifact
cannot be identified from this repository's deployment history; use the
organization's independently verified deployment record rather than guessing.

## v1.1.0 — 2026-06-06

Updated the historical deployment record examples.

### Added

- Updated the deployment-history examples used to demonstrate the existing
  traceability problems.

### Rollback target

`v1.0.0` — the preceding tagged repository milestone. Verify its deployment
status before using it as a production rollback.

## v1.1.1 — 2026-06-06

Refined the checkout-service placeholder startup output.

### Changed

- Renamed the placeholder's service constants and startup function, and
  clarified its startup messages.

### Rollback target

`v1.1.0` — the preceding tagged repository milestone. Verify it is the
last-known-good deployed version before redeploying.
