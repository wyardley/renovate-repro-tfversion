# renovate-repro-tfversion
Minimal repro for renovate config help

## Current Behavior

When a GitHub actions config has, e.g., `1.9` or `1.10`, Renovate will propose
updating to `1.11.0` vs `1.11`

## Expected Behavior

I would like a way to configure renovate to preserve the versioning already
present for these updates. For example, if the version is `1.9` and `1.10.3` is
the latest, I'd like to be able to update to `1.10`. With Terraform providers
and modules, I think this behavior is already supported via the `hashicorp`
version type.
