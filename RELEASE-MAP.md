# Release Map

The commits below are annotated repository release milestones selected from
the existing history. The source deployment records do not establish that any
of them were actually deployed, so the entries are not claims about what is
currently in production. Confirm and record a deployment against its exact
commit before using the map as a production inventory.

| Version (tag) | Commit (short hash) | Date | What Shipped |
| --- | --- | --- | --- |
| `v1.0.0` | `ff1fb9a` | 2026-06-06 | Initial assignment repository: checkout-service placeholder, project guidance, and baseline changelog/deployment/incident examples. Repository milestone; production deployment not verified. |
| `v1.1.0` | `28bd110` | 2026-06-06 | Updated the historical deployment record examples. Repository milestone; production deployment not verified. |
| `v1.1.1` | `82535d9` | 2026-06-06 | Refined the checkout-service placeholder's startup output and service constants. Repository milestone; production deployment not verified. |

## Traceable rollback demonstration

For this example, assume `v1.1.1` is the release under investigation and that
the operator has independently verified `v1.1.0` as the last known-good
deployment. The existing historical deployment records do not prove that
verification for these new tags; update the deployment record with the deployed
tag and commit before treating any version as production's current state.

```sh
git tag --sort=-v:refname        # the sortable release history
git checkout v1.1.0              # roll back to the last known-good tag, then redeploy
```

Each release tag now resolves to an explicit historical commit, and its
annotation and release notes describe the milestone, so the team can reproduce
the selected source state and explain why it was chosen. The original history
had no Git tags at all and only inconsistent labels in documents, making the
same rollback a guess rather than a verifiable commit selection.
