# Cocogitto Pre-Commit

[Pre-Commit](https://pre-commit.com/) hooks for
[Cocogitto](https://github.com/cocogitto/cocogitto), the [conventional
commits](https://www.conventionalcommits.org/) toolbox.

## Using cocogitto-pre-commit hooks with pre-commit

Add this to your `.pre-commit-config.yaml`. Please note that using the
`cocogitto-verify` hook requires the `commit-msg` hook stage to be installed.

*Note: these hooks require the `cog` tool to be available in your `PATH`.*

```yaml
---
default_install_hook_types: [pre-commit, pre-push, commit-msg]
default_stages: [pre-commit, pre-push]
repos:
  - repo: https://gitlab.com/alexander-bauer/cocogitto-pre-commit
    rev: v0.1.0
    hooks:
      - id: cocogitto-check
      - id: cocogitto-verify
```
## Hooks available

### `cocogitto-check`

Check the validity of all ancestor commit messages using `cog check`.

- Override the stages it runs on by supplying `stages: [pre-commit, pre-push]`.
  (These are stages it runs on by default.)
- To check only commits since a specific ref, supply arguments to the command
  like `args: ["5f59c71ba83e44c8a8044d2c39abf3e919d200ae..HEAD"]`.

### `cocogitto-verify`

Verify a newly-written commit message before it is committed using `cog verify`.

*Note: this hook can only run in the `commit-msg` stage, which is not installed
by default. To install `commit-msg` when running `pre-commit install`, add the
following top-level directives to your `.pre-commit-config.yaml`:*

```yaml
default_install_hook_types: [pre-commit, pre-push, commit-msg]
default_stages: [pre-commit, pre-push]
```
