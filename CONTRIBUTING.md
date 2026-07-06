<!--
SPDX-FileCopyrightText: The metio Authors
SPDX-License-Identifier: 0BSD
-->

# Contributor Guide

Thank you for improving metio's projects! Without a healthy community, any open
source project is doomed.

## Issue management

Each project tracks its work in its own GitHub issue tracker. Search the open
issues before filing a new one, and include enough detail — versions, steps, and
expected versus actual behavior — to reproduce the problem.

## Branching model

The `main` branch always holds the latest public stable release. Branch from it
for your change and open a pull request back against it.

## Development environment

Projects define their entire toolchain in a **[nix](https://nixos.org) flake**
(`flake.nix` + `flake.lock`), so CI and your machine run byte-identical tool
versions — a gate that is green locally is green in CI by construction, and no
host toolchain is required. Install Nix (with flakes enabled), then run any
gate through the dev shell:

```shell
nix develop --command <gate>   # e.g. nix develop --command go test ./...
```

or run `nix develop` to drop into a shell with every tool on `PATH` (it prints
the available commands on entry). The flake is the single source of tool
versions; Renovate keeps `flake.lock` current. On Windows, work inside
[WSL2](https://learn.microsoft.com/windows/wsl/) — Nix runs on Linux and macOS.
A project that does not yet ship a `flake.nix` documents its own setup in its
`README`.

## Pull requests

- Keep each pull request focused on a single change.
- Write [Conventional Commits](https://www.conventionalcommits.org); the
  changelog and the calendar-versioned release are generated from them.
- Every file carries an SPDX license header (or an entry in `REUSE.toml`); the
  REUSE check enforces it.
- The `Verify` check must be green before a pull request can merge.

## Code of conduct

Participation is governed by our [Code of Conduct](CODE_OF_CONDUCT.md).
