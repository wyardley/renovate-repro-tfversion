# renovate-repro-tfversion
Minimal repro for renovate config help

## Current Behavior

The current behavior is correct, but I'm trying to figure out how to follow a
looser version strategy when bumping a `github-release` derived version in a
GHA config.

The Terraform configs are mostly to show how the versions show up when both are
getting updated at the same time. After reviewing the docs, Renovate's behavior
is correct in that it will propose updating a pinned `1.9` version to, e.g.,
`1.11` in `modules/pinnedversion/versions.tf`, and will also bump `~> 1.9.0` to
`~> 1.11.0`, but doesn't seem to touch `~> 1.9` since it doesn't need to.

## Expected Behavior

I would like a way to configure renovate to preserve the versioning already
present for these updates. For example, if the version is `1.9` and `1.10.3` is
the latest, I'd like to be able to update to `"~> 1.10"` or `1.10`. With
Terraform providers and modules, I think this behavior is already supported.

I briefly tried using a `packageRule` to set the versioning type to
`hashicorp`, but it didn't seem to change that, probably because there is
nothing before the version.
