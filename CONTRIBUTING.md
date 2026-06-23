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

## Pull requests

- Keep each pull request focused on a single change.
- Write [Conventional Commits](https://www.conventionalcommits.org); the
  changelog and the calendar-versioned release are generated from them.
- Every file carries an SPDX license header (or an entry in `REUSE.toml`); the
  REUSE check enforces it.
- The `Verify` check must be green before a pull request can merge.

## Code of conduct

Participation is governed by our [Code of Conduct](CODE_OF_CONDUCT.md).
