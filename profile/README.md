# FastTrackStudio

Open-source Rust software for making music and running the work around it:
a DAW and live rig, a local-first personal operating system, the framework
they are built on, and studio routing.

The interfaces are [Dioxus](https://dioxuslabs.com), so one UI serves the
desktop app, the browser and the phone. Install steps are in each repo's
README.

## Studio

[![CI on main](https://github.com/FastTrackStudios/studio/actions/workflows/checks.yml/badge.svg?branch=main)](https://github.com/FastTrackStudios/studio/actions/workflows/checks.yml?query=branch%3Amain)

FastTrackStudio's audio and music software in one repository: Session (a
DAW), Signal (a live instrument rig), Patchbay (studio routing) and the FTS
effects as CLAP and VST3 plugins. Session and Signal run the same engine.

- **Session**: tracking, editing and mixing, setlists and songs, charts in
  the keyflow language, and the guide (click, count-in, spoken section cues).
- **Signal**: guitar, bass, keys, drums and sampled instruments, with tones
  and patches switched during a set. The rig runs headless; a laptop, phone,
  tablet or browser attaches to it as a remote.

Status: CalVer releases (`vYY.M.MICRO`) of the Studio app for macOS (Apple
silicon) and Linux (x86_64); iPhone and iPad in a TestFlight beta.
GPL-3.0-or-later.
**[FastTrackStudios/studio](https://github.com/FastTrackStudios/studio)** ·
[Releases](https://github.com/FastTrackStudios/studio/releases/latest)

## Task

[![CI on main](https://github.com/FastTrackStudios/task/actions/workflows/checks.yml/badge.svg?branch=main)](https://github.com/FastTrackStudios/task/actions/workflows/checks.yml?query=branch%3Amain)

A local-first personal operating system: a vault of markdown notes with
tasks, projects, goals, a calendar, files and agents on top.

- Work in orgs (a studio, a client, a personal org) and move between them;
  wikis, inbox, email, scheduling and more are features of the same vault.
- There is no central server: every install is a node holding your data, and
  your signed-in nodes find each other and sync directly.
- Run it as a desktop app, as an always-on headless `task-server`, or host
  orgs for a team with the web app (container images and a Helm chart).
- Agents work in it through its CLI and MCP server.

Status: CalVer releases with the desktop app for macOS (Apple silicon) and
Linux (x86_64), `task-server` binaries and the web app; installed apps
update themselves. MIT OR Apache-2.0.
**[FastTrackStudios/task](https://github.com/FastTrackStudios/task)** ·
[Releases](https://github.com/FastTrackStudios/task/releases/latest)

## Architect

[![checks on main](https://img.shields.io/github/check-runs/FastTrackStudios/architect/main?nameFilter=check&label=checks)](https://github.com/FastTrackStudios/architect/actions/workflows/checks.yml?query=branch%3Amain)

<!-- media: showcase-layout -->

A Rust framework for building local-first, multiplayer, collaborative apps.
Declare a data model and a service once; the derives write the wire types,
the vox, HTTP and iroh transports, the clients, the storage and the
migrations.

- Documents and sync, through an org server or peer to peer, with presence
  and collaborative text.
- Auth, permissions and orgs; settings declared once, by the app or by an
  extension.
- One Action List behind the keymap and input system, the ⌘K palette,
  menus, Luau scripting and an MCP server.
- Extensions added at run time (data, Luau, WASM, processes).
- The shell and the workspace: tabs in splits, docks, floats and pop-out
  windows.

Status: pre-1.0 SemVer (`v0.9.x`); APIs change in any release. Not on
crates.io: depend on a git tag. MIT OR Apache-2.0. Task, Studio and Patchbay
are built on it.
**[FastTrackStudios/architect](https://github.com/FastTrackStudios/architect)** ·
[Releases](https://github.com/FastTrackStudios/architect/releases/latest)

## Patchbay

[![CI on main](https://github.com/FastTrackStudios/patchbay/actions/workflows/checks.yml/badge.svg?branch=main)](https://github.com/FastTrackStudios/patchbay/actions/workflows/checks.yml?query=branch%3Amain)

Studio routing in one window: PipeWire, Core Audio, Dante and digital desks,
wired, mixed and recalled.

- Route PipeWire nodes and ports on Linux, or every app's audio on macOS,
  with loopback mixes into virtual devices.
- Drive a Dante network, an Antelope Galaxy 32 and a Yamaha TF from the same
  rail, and save scenes across all of them.
- Use it from the desktop app, a browser or phone remote, or the `patchbay`
  CLI built for agents (`--json`).

Status: its own repo since October 2026, first CalVer release `v26.10.0`,
built from source. The RPC endpoint has no authentication yet: keep it on
loopback or a trusted studio network. GPL-3.0-or-later.
**[FastTrackStudios/patchbay](https://github.com/FastTrackStudios/patchbay)**

## How they fit together

```text
                 architect
       ┌─────────────┼─────────────┐
       ▼             ▼             ▼
     task ───────▶ studio       patchbay
```

An arrow points from a repo to one that depends on it. Studio uses Task's
crates to keep songs and sessions in Task orgs; Task does not depend on
Studio. Patchbay depends on none of the others but Architect. Studio's
workspace also contains Patchbay (`apps/patchbay`), the tree the standalone
repo was split from.

## Also here

- [keyflow](https://github.com/FastTrackStudios/keyflow): a text format for musical charts, and the Engraver layout engine that renders them
- [editor](https://github.com/FastTrackStudios/editor): an embeddable Rust/Dioxus text and markdown editor
- [music-convention](https://github.com/FastTrackStudios/music-convention): a convention for naming, grouping, colouring and ordering tracks in a session
- [vendor](https://github.com/FastTrackStudios/vendor): third-party crates we patch
- [neural-amp-modeler-rs](https://github.com/FastTrackStudios/neural-amp-modeler-rs): safe Rust bindings to NeuralAmpModelerCore
- [nice-plug](https://github.com/FastTrackStudios/nice-plug): our plugin framework fork, with a Dioxus Native GUI backend

The old `FastTrackStudio` monorepo and the `signal`, `session` and `daw` repos
are archived; their audio code lives in Studio now.

Issues are open on every repo.
