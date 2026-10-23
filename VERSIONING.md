# Release Versioning Convention

## Semantic versioning

Use `MAJOR.MINOR.PATCH` as `vMAJOR.MINOR.PATCH`:

- **MAJOR** increases for incompatible changes to the service's public behavior
  or interfaces. Example: `v1.4.2` -> `v2.0.0`.
- **MINOR** increases for backward-compatible functionality. Reset PATCH to
  zero. Example: `v1.4.2` -> `v1.5.0`.
- **PATCH** increases for backward-compatible fixes. Example:
  `v1.4.2` -> `v1.4.3`.

Each release tag identifies one immutable commit. Do not reuse or move a
published release tag.

## Tag naming

The exact release format is `vMAJOR.MINOR.PATCH`, with non-negative integers
and no leading zeroes (except the number zero itself). Example: `v1.5.0`.

## Annotated release tags

Production releases use annotated tags because they include a message and tag
metadata, creating a durable release record rather than only a pointer to a
commit. Create one with:

```sh
git tag -a v1.5.0 -m "Release 1.5.0: <concise summary>"
```

Push release tags with `git push origin --tags`. Release messages should state
the version and a meaningful summary.

## Pre-releases

Mark release candidates and betas by appending a hyphen and a dot-separated
pre-release identifier, for example `v1.5.0-rc.1` or `v1.5.0-beta.1`.
Increment the identifier for subsequent candidates. Pre-releases sort before
the corresponding final version: `v1.5.0-rc.1` < `v1.5.0-rc.2` <
`v1.5.0`. Do not treat a pre-release as a production release.
