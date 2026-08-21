# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository state

This repository currently contains no application source code, build tooling, dependency
manifest, or test suite. The tracked files are:

- `README.md` and `readme.md` — two separate, case-differing placeholder files, each holding
  auto-generated "Unique Commit" stub content (a random string and a date). They are not
  documentation of a real project.
- Git history consists entirely of auto-generated "Auto commit for 115691 - N" commits.

There are no commands to build, lint, or test anything, because no such tooling exists in the
repo. Do not assume a framework, language, or project layout that isn't actually present —
check the current file listing (`git ls-files`) before making claims about structure.

## Working in this repository

If you are asked to add real functionality here, treat it as greenfield work: there is no
existing architecture, conventions, or module layout to conform to. Establish and document
whatever structure the new work needs, and update this file to reflect it once real code
exists.
