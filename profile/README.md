# FastTrackStudio

Tools for people who make things — a live music rig, a personal operating
system, studio audio routing, and the framework all three are built on.

Everything here is Rust, local-first, and works offline. The UI is
[Dioxus](https://dioxuslabs.com), so the same code runs as a desktop app, in
the browser, on iOS, and inside an audio plugin.

## The four main repos

### [FastTrackStudio](https://github.com/FastTrackStudios/FastTrackStudio)

The audio/music product. **Signal** — the headless live-rig engine (plugin
chains, sampler, amp modeling, FX) with detachable GUIs that attach over the
network from a browser, a tablet, or the desktop. Around it: the DAW domain and
REAPER integration, session/setlist management, keyflow, engraving, and the
FastTrackStudio app itself.

### [Task](https://github.com/FastTrackStudios/task)

A local-first personal operating system. A vault of markdown notes with
structured overlays on top — tasks, projects, goals, a calendar, files, and
agents. Your data stays plain markdown on your disk; sync and collaboration are
opt-in.

### [Patchbay](https://github.com/FastTrackStudios/patchbay)

PipeWire routing for studios. See every node and every port on the machine,
wire them together, and keep the result — routing that survives a reboot,
a device reconnect, and a PipeWire restart.

### [Architect](https://github.com/FastTrackStudios/architect)

The application framework the others are built on: entities and typed RPC,
atoms and forms, auth and permissions, CRDT document sync, telemetry, and the
`architect-ui` component library. Facet-native, transport-agnostic, and
wasm-ready.

## How they fit together

```
        Architect          the framework — RPC, auth, sync, UI
       ↙         ↘
FastTrackStudio ⇄ Task     audio product  ⇄  personal OS
        ↑
     Patchbay              the audio routing underneath it all
```

FastTrackStudio and Task depend on each other on purpose: Task provides the
editor and knowledge-graph stack, FastTrackStudio provides the DAW, session and
song domains.

## Also here

- [vendor](https://github.com/FastTrackStudios/vendor) — third-party crates we patch
- [music-convention](https://github.com/FastTrackStudios/music-convention) — a convention for naming, grouping, colouring and ordering tracks in a session
- [neural-amp-modeler-rs](https://github.com/FastTrackStudios/neural-amp-modeler-rs) — safe Rust bindings to NeuralAmpModelerCore
- [nice-plug](https://github.com/FastTrackStudios/nice-plug) — our plugin framework fork, with a Dioxus Native GUI backend

---

Everything is open. Issues and discussions are welcome on any repo.
