# Tag History Audit

## Scope and evidence

The requested `git tag`, `git log --oneline --decorate --all`, and
`git tag --sort=-v:refname` commands show that this checkout has **no Git tags**.
The names below are therefore not existing refs in this repository; they are
legacy labels cited in the repository's deployment history, incident log,
changelog, and old release notes. They cannot be resolved to commits with Git.

| Evidence | Problem and team impact | Rollback or traceability risk |
| --- | --- | --- |
| `release_2` — [docs/incident-log.md](docs/incident-log.md) says it was lightweight and points to an older unsupported commit; the incident record says rollback to it followed a 502 incident. | The name does not communicate a version or contents, and there is no release annotation or deployment record to establish its purpose. | It has already been associated with an unsafe rollback. Without an immutable release record, responders cannot confidently select or audit a safe target. |
| `latest-good` — [docs/deployment-history.md](docs/deployment-history.md) and [CHANGELOG.md](CHANGELOG.md) say production was deployed from it on 2026-05-04. | “Latest” and “good” are subjective labels, and neither specifies a version, commit, or what changed. | The label cannot establish which build was deployed or whether its target later moved; reproducing the deployment or rolling back to it is guesswork. |
| `v1.4.2` — [CHANGELOG.md](CHANGELOG.md) says production was assumed to be this version on 2026-04-10, while [docs/deployment-history.md](docs/deployment-history.md) only records an assumed staging promotion and says the production tag is undocumented. | A SemVer-looking label is not sufficient evidence that the matching release was actually deployed. | An operator could roll back to a version that was never verified in production, while the actual production commit remains unknown. |
| `stable-build` — [docs/deployment-history.md](docs/deployment-history.md) records a missing deployment record for it on 2026-03-15, and [docs/incident-log.md](docs/incident-log.md) cites it among inconsistent tags. | “Stable” is an unsupported status claim; the label carries no version or release contents. | The name does not identify a reproducible safe commit, undermining both rollback selection and audit review. |
| `patch-new` — [docs/release-notes-old.md](docs/release-notes-old.md) calls it a “new patch release.” | The name does not include the MAJOR.MINOR.PATCH number, and the notes do not identify a commit or the actual patch. | Teams cannot determine which fixes are included or tell whether this is the intended patch rollback target. |
| `v2-final-FINAL` — [docs/release-notes-old.md](docs/release-notes-old.md) describes it only as “production-ready? maybe”. | Repeated “final” wording is ambiguous, and the question mark signals that readiness was not established. | Multiple candidates may be mistaken for the approved release; missing commit and deployment evidence prevents a reliable audit or rollback. |
| `Unknown version` — [docs/deployment-history.md](docs/deployment-history.md) and [CHANGELOG.md](CHANGELOG.md) record production as unknown on 2026-03-31. | This is a deployment traceability failure rather than a usable tag name: no release identifier was recorded. | Responders cannot identify the live commit, compare it with a candidate rollback, or reproduce the production state. |

The audit baseline is consequently an empty Git tag namespace, not a corrupt set
of resolvable refs. The release tags added for this assignment establish
consistent repository milestones; they do not retroactively prove that those
milestones were deployed.
