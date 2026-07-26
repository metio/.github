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
- Sign off every commit (see below).
- The `Verify` check must be green before a pull request can merge.

## Developer Certificate of Origin

Every commit carries a `Signed-off-by` trailer, which records your agreement to
the [Developer Certificate of Origin](https://developercertificate.org/). Add it
with the `--signoff` flag:

```shell
git commit --signoff
```

The `DCO` check verifies the trailer on every commit in a pull request, so a
missing sign-off blocks the merge. To fix the last commit, amend it with
`git commit --amend --signoff`; for a whole branch, use
`git rebase --signoff main`.

By signing off you certify that:

```text
(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.
```

## Code of conduct

Participation is governed by our [Code of Conduct](CODE_OF_CONDUCT.md).
