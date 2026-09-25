# Munder Difflin

### Agent harness to run an office of your clones

<p align="center">
  <img src="./docs/previews/default1.png" width="1100">
</p>

<p align="center">
  <strong>A customized Munder Difflin fork with additional visual themes.</strong><br>
  Same agent system. Same office simulation. Same core workflows.
</p>

<p align="center">
  <a href="#themes">Themes</a> ·
  <a href="#getting-started">Getting Started</a> ·
  <a href="#what-it-is">What It Is</a> ·
  <a href="#architecture">Architecture</a>
</p>

---

## ✦ Themes

This fork adds a collection of visual themes while keeping the underlying Munder Difflin experience intact.

### Theme Gallery

<table>
  <tr>
    <td align="center" width="33%">
      <img src="./docs/previews/default1.png" width="100%">
      <br>
      <sub><b>Original</b></sub>
    </td>
    <td align="center" width="33%">
      <img src="./docs/previews/obsidian.png" width="100%">
      <br>
      <sub><b>Obsidian</b></sub>
    </td>
    <td align="center" width="33%">
      <img src="./docs/previews/ember.png" width="100%">
      <br>
      <sub><b>Ember</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="33%">
      <img src="./docs/previews/violet.png" width="100%">
      <br>
      <sub><b>Violet</b></sub>
    </td>
    <td align="center" width="33%">
      <img src="./docs/previews/arctic.png" width="100%">
      <br>
      <sub><b>Arctic</b></sub>
    </td>
    <td></td>
  </tr>
</table>

> **Note:** Replace `obsidian.png`, `ember.png`, `violet.png`, and `arctic.png` with your actual preview filenames if they are different.

### Available Themes

| Theme        | Style                                                |
| ------------ | ---------------------------------------------------- |
| **Original** | The classic Munder Difflin appearance                |
| **Obsidian** | Deep grayscale, dark surfaces and subdued contrast   |
| **Ember**    | Graphite surfaces with neon orange accents           |
| **Violet**   | Purple and magenta focused interface                 |
| **Arctic**   | Bright white and cool-gray Apple-inspired appearance |

### Custom Theme Patch

The repository also contains the theme customization patch:

```text
munder-difflin-color-themes.patch
```

To apply the patch to another Munder Difflin checkout:

```bash
git apply munder-difflin-color-themes.patch
```

---

## About Munder Difflin

Free, open source and performant — a multi-agent harness that works with the subscriptions you already pay for, on their hourly limits. It turns the terminal coding CLI you already run into a clone of you, one that keeps working while you're away and coordinates a whole office of agents on your own machine.

Wraps Claude Code, Antigravity (Gemini), OpenAI Codex, xAI Grok, Kimi Code, Gemini CLI, Qwen, OpenCode, Crush, pi.dev, GitHub Copilot CLI, and Cursor — with bring-your-own keys and local LLMs.

Agents message, route, and remember, coordinated by your clone (Michael) and visualized as avatars at work on a shared office floor.

**Electron · React · TypeScript · Pixi.js · xterm.js · node-pty**

---

## Supported Agents

Bring the CLI you already pay for.

Every one of these runs as a real process in its own terminal, with your existing subscription and its hourly limits. If it runs in a terminal, it can run here.

`Claude Code` · `Codex · GPT` · `Grok · xAI` · `Kimi Code` · `Gemini CLI` · `Antigravity · Gemini` · `Qwen` · `OpenCode` · `Crush · Charm` · `Pi` · `GitHub Copilot` · `Cursor` · `+ any custom command`

Plus bring your own keys and local models through Ollama, LM Studio or vLLM.

---

## What It Is

Munder Difflin is a desktop app that wraps real terminal-agent CLIs as fully-capable agents, wires them into a hive mind, and puts your clone in charge — Michael, the one agent you talk to in order to get things done.

Under the hood it runs a memory layer so every agent can remember what it learns and recall it across sessions.

### Every terminal is an agent

Each `claude`, `agy`, `codex`, `grok`, `kimi`, `qwen`, `opencode`, `crush`, `pi`, `copilot`, or custom session runs as a real process in a pseudo-terminal (`node-pty`), rendered with xterm.js.

### Every agent is an avatar

Sessions appear as characters on a Pixi.js office floor. They walk to stations as they work, and messages can travel between desks.

### The hive coordinates them

Agents read their memory and drain a mailbox. The router moves messages between inboxes, while the GOD agent coordinates work and escalates when human input is required.

### Memory across sessions

A markdown-first memory layer with semantic recall allows agents to retain useful information across sessions.

### Prerequisites

A dedicated Settings page shows supporting tools such as:

* `uv`
* `git`
* Node.js
* MemPalace
* Agent CLIs

The application can also help identify missing dependencies.

---

## Status

The upstream project has shipped a broad set of features including multiple agent engines, local LLM support, voice orchestration, the hive, Command Center, IDE functionality, integrations, durable persistence, session resume, multi-window floors, Skills, prerequisites checking, cost reporting, semantic memory and automatic updates.

This fork focuses on additional visual customization while preserving the core Munder Difflin experience.

---

# Getting Started

## Download the App

Most people want the packaged application.

Signed and notarized macOS builds, along with Windows and Linux builds, are available from the project's releases.

You do not need Node.js, a toolchain, or this repository when using a packaged release.

You still need at least one supported agent CLI on your machine. Missing tools can be installed through the application's prerequisites/settings flow.

---

## Build From Source

Everything below is for contributors and people who want to run an unreleased build.

### Prerequisites

* macOS, Windows, or Linux.
* Node.js 18+ and npm.
* A C/C++ toolchain for `node-pty`'s native addon.
* At least one supported agent CLI on your `PATH`.
* Optional API keys and local LLMs.
* Optional semantic memory indexing.

On macOS, install the Xcode Command Line Tools with:

```bash
xcode-select --install
```

Supported agent CLIs include:

```text
claude
agy
codex
grok
kimi
gemini
qwen
opencode
crush
pi
copilot
cursor-agent
```

---

## Install & Run

```bash
git clone <YOUR_FORK_URL>
cd munder-difflin
npm install
npm run dev
```

On first launch you'll go through the onboarding wizard and then land on the office floor.

Use **Add agent** to spawn your first session.

---

## Other Scripts

### Production build

```bash
npm run build
```

### Preview production build

```bash
npm run preview
```

### Type checking

```bash
npm run typecheck
```

If `node-pty` fails to load after an Electron upgrade, run:

```bash
npm install
```

The postinstall process rebuilds `node-pty` against the current Electron ABI.

---

# Architecture

Two data planes feed one renderer:

* A **terminal plane** that owns PTYs, filesystem access and git.
* An **event plane** that runs the hive, hook server and router.

The renderer communicates with both through a typed bridge.

The detailed architecture documentation is maintained separately in the project's documentation.

Related documentation includes:

```text
docs/ARCHITECTURE.md
HIVE.md
SPEC.md
DESIGN.md
```

---

# Features

## Multi-Agent Office

Run multiple coding agents simultaneously and visualize them as characters working throughout the office.

## Real Terminal Sessions

Agents operate through real terminal processes instead of simulated chat interfaces.

## Agent Memory

Agents can maintain persistent memory and recall information across sessions.

## Hive Coordination

The office provides a coordination layer allowing agents to communicate and route work between each other.

## GOD Orchestrator

Michael acts as the central orchestrator and can coordinate work across the office.

## Multiple AI Engines

Use different supported agent engines depending on the task and configuration.

## Local Models

Bring local models through supported integrations such as:

* Ollama
* LM Studio
* vLLM

## Voice

Realtime Michael provides a voice channel for interacting with the orchestrator when configured.

## Command Center

Manage work through centralized views and workflows.

## Built-In IDE

The application includes an integrated development environment with git functionality.

## Integrations

Connect external tools and services through the integrations system.

## Skills

Agents can be configured with additional capabilities and skills.

## Session Persistence

Sessions can persist and resume rather than starting from scratch every time.

## Multi-Window Floors

Run multiple office/floor views when supported by the current build.

---

# Roadmap

The upstream project continues to evolve across agent engines, integrations, avatar behavior, persistence and command history.

Current areas of development include:

* More chat integrations.
* Additional agent engines and integration templates.
* Fuller avatar coverage driven by real hook events.
* Durable layout and command history.
* Continued improvements to the agent and office experience.

See the project's `CHANGELOG.md` for detailed historical changes.

---

# Contributing

Contributions are welcome.

Start with:

```text
CONTRIBUTING.md
```

The basic workflow is:

```bash
npm install
npm run dev
npm run typecheck
```

When changing the UI, follow the project's design-system documentation.

### UI contributions

Pull requests involving UI changes should include before-and-after evidence such as screenshots or recordings.

Good areas for contributions include:

* Agent creation flows.
* Configuration UI.
* Real hook events.
* Cross-platform improvements.
* Office interactions.
* Agent integrations.
* Theme improvements.

---

# Custom Themes

This fork's theme work is intentionally focused on presentation.

The goal is to allow the same Munder Difflin experience to be presented through different visual styles without turning each theme into a separate application.

### Original

The baseline Munder Difflin appearance.

### Obsidian

A darker grayscale interface focused on low-light use, subdued surfaces and minimal visual noise.

### Ember

A dark graphite interface with bright orange accents.

### Violet

A purple/magenta visual treatment.

### Arctic

A bright interface using white and cool-gray surfaces with a clean modern aesthetic.

---

# Telemetry

Official builds send a small set of anonymous usage events.

The project documents the event list, privacy guarantees and available opt-out mechanisms in:

```text
TELEMETRY.md
```

Forks and source builds can have different telemetry behavior depending on their configuration.

---

# License

## Source Code

The source code is licensed under the MIT License.

See:

```text
LICENSE
```

for the complete license text.

## Asset Licensing

The bundled pixel art tilesets and maps are from Modern Interiors - RPG Tileset [16X16] by LimeZu and are used under the applicable Complete Version licence.

Credit to LimeZu is required by that licence and must remain in place.

The Office cast is not LimeZu artwork. It is drawn procedurally in:

```text
src/renderer/src/assets/portraitArt.ts
```

See:

```text
src/renderer/src/assets/ATTRIBUTION.md
```

for attribution details.

The bundled pixel art is licensed separately from the source code.

See:

```text
LICENSE-ASSETS
```

for the applicable asset licensing information.

Munder Difflin is an affectionate parody and is not affiliated with NBC's *The Office* or Dunder Mifflin.

---

# Acknowledgements

* **LimeZu** — Modern Interiors pixel-art tilesets.
* **shahar061/the-office** — office tileset/map vendoring.
* **Pixi.js** — rendering.
* **xterm.js** — terminal rendering.
* **node-pty** — pseudo-terminal processes.
* **electron-vite** — Electron development tooling.
* **CodeMirror** — editor functionality.
* **Remotion** — animated landing-page content.
* **The Office (US)** — inspiration for Munder Difflin.

---

<p align="center">
  <sub>
    Munder Difflin — an office of your clones.
  </sub>
</p>
