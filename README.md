# Munder Difflin

### Agent harness to run an office of your clones

Free, open source and performant — a multi-agent harness that works with the subscriptions you already pay for, on their hourly limits. It turns the terminal coding CLI you already run into a clone of you, one that keeps working while you're away and coordinates a whole office of agents on your own machine.

Wraps Claude Code, Antigravity (Gemini), OpenAI Codex, xAI Grok, Kimi Code, Gemini CLI, Qwen, OpenCode, Crush, pi.dev, GitHub Copilot CLI, and Cursor — with bring-your-own keys and local LLMs. Agents that message, route, and remember, coordinated by your clone (Michael) and visualized as avatars at work on a shared office floor.

**Electron · React · TypeScript · Pixi.js · xterm.js · node-pty**

<p align="center">
  <a href="#theme-preview">Theme Preview</a>
  ·
  <a href="#supported-agents">Supported Agents</a>
  ·
  <a href="#what-it-is">What It Is</a>
  ·
  <a href="#features">Features</a>
  ·
  <a href="#getting-started">Getting Started</a>
  ·
  <a href="#architecture">Architecture</a>
</p>

---

> ### Note
>
> **The world's best agents. The world's worst paper company.**
>
> Munder Difflin takes the terminal-agent CLIs you already run — `claude`, `agy`, `codex`, `grok`, `kimi`, `qwen`, `opencode`, `crush`, `pi`, and `copilot` — and turns them into a self-coordinating team.
>
> Each agent gets long-term memory, a mailbox, and a desk on a 2D office floor — while your clone (Michael) routes work between them and you watch everything happen.
>
> **He's the boss of the floor. You're still the boss of him.**

---

# 🎨 Theme Preview

This fork adds a set of visual themes to the Munder Difflin interface while keeping the underlying multi-agent workflow intact.

<p align="center">
  <sub>Five visual styles. One office.</sub>
</p>

### Original

<p align="center">
  <img src="./docs/default1.png" width="100%" alt="Original Munder Difflin theme">
</p>

<p align="center">
  <sub><b>Original</b> — The classic Munder Difflin visual style.</sub>
</p>

---

### Obsidian

<p align="center">
  <img src="./docs/obsidian.png" width="100%" alt="Obsidian Munder Difflin theme">
</p>

<p align="center">
  <sub><b>Obsidian</b> — Deep grayscale with a darker, subdued interface.</sub>
</p>

---

### Ember

<p align="center">
  <img src="./docs/ember.png" width="100%" alt="Ember Munder Difflin theme">
</p>

<p align="center">
  <sub><b>Ember</b> — Dark graphite with bright orange accents.</sub>
</p>

---

### Violet

<p align="center">
  <img src="./docs/violet.png" width="100%" alt="Violet Munder Difflin theme">
</p>

<p align="center">
  <sub><b>Violet</b> — Purple and magenta-focused styling.</sub>
</p>

---

### Arctic

<p align="center">
  <img src="./docs/arctic.png" width="100%" alt="Arctic Munder Difflin theme">
</p>

<p align="center">
  <sub><b>Arctic</b> — Bright white and cool-gray styling.</sub>
</p>

---

## Themes

| Theme        | Style                                           |
| ------------ | ----------------------------------------------- |
| **Original** | The classic Munder Difflin appearance           |
| **Obsidian** | Deep grayscale with a darker, subdued interface |
| **Ember**    | Dark graphite with bright orange accents        |
| **Violet**   | Purple and magenta-focused styling              |
| **Arctic**   | Bright white and cool-gray styling              |

---

## Theme Patch

The color customization is also included as a standalone patch:

```text
munder-difflin-color-themes.patch
```

The patch is located at the root of this repository.

### Verify the patch

```bash
git apply --check munder-difflin-color-themes.patch
```

### Apply the patch

```bash
git apply munder-difflin-color-themes.patch
```

---

# Munder Difflin

Free, open source and performant — a multi-agent harness that works with the subscriptions you already pay for, on their hourly limits.

It turns the terminal coding CLI you already run into a clone of you, one that keeps working while you're away and coordinates a whole office of agents on your own machine.

Wraps Claude Code, Antigravity (Gemini), OpenAI Codex, xAI Grok, Kimi Code, Gemini CLI, Qwen, OpenCode, Crush, pi.dev, GitHub Copilot CLI, and Cursor — with bring-your-own keys and local LLMs.

Agents message, route, and remember, coordinated by your clone (Michael) and visualized as avatars at work on a shared office floor.

**Electron · React · TypeScript · Pixi.js · xterm.js · node-pty**

---

## Contents

* [Theme Preview](#-theme-preview)
* [Themes](#themes)
* [Theme Patch](#theme-patch)
* [Supported Agents](#supported-agents)
* [What It Is](#what-it-is)
* [How It Works](#how-it-works)
* [Features](#features)
* [Getting Started](#getting-started)
* [Architecture](#architecture)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [Telemetry](#telemetry)
* [License](#license)
* [Acknowledgements](#acknowledgements)

---

## Supported agents

Bring the CLI you already pay for.

Every supported agent runs as a real process in its own terminal, using its existing subscription and hourly limits. If it runs in a terminal, it can run here.

`Claude Code` · `Codex · GPT` · `Grok · xAI` · `Kimi Code` · `Gemini CLI` · `Antigravity · Gemini` · `Qwen` · `OpenCode` · `Crush · Charm` · `Pi` · `GitHub Copilot` · `Cursor` · `+ any custom command`

Plus bring your own keys and local models through Ollama, LM Studio or vLLM.

---

## What it is

Munder Difflin is a desktop app that wraps real terminal-agent CLIs as fully-capable agents, wires them into a hive mind, and puts your clone in charge — Michael, the one agent you talk to in order to get things done.

Under the hood it provides a persistent memory and coordination layer so agents can retain context and collaborate across sessions.

### Every terminal is an agent

Each `claude`, `agy`, `codex`, `grok`, `kimi`, `qwen`, `opencode`, `crush`, `pi`, `copilot`, or custom session runs as a real process in a pseudo-terminal (`node-pty`), rendered with xterm.js.

### Every agent is an avatar

Sessions appear as characters on a Pixi.js office floor. They walk to stations as they work, while envelopes move between desks when agents communicate.

### The hive coordinates them

Agents read their memory and drain a mailbox while the router moves messages between inboxes.

The GOD agent adjudicates, assigns work, and escalates items that need you.

### Memory survives the session

A markdown-first memory layer with semantic recall lets agents carry learned context across sessions.

---

## How it works

```text
             you ── talk to ──►  ┌─────────────┐
                                  │  GOD agent  │  orchestrator / supervisor
                                  │ (Michael's  │  roster · routing · adjudication
                                  │   office)   │  blackboard · task ledger
                                  └──────┬──────┘
                                         │ assigns · routes · escalates
               ┌─────────────────────────┼─────────────────────────┐
               ▼                         ▼                         ▼
         ┌───────────┐            ┌───────────┐            ┌───────────┐
         │  agent A  │  message   │  agent B  │  message   │  agent C  │
         │ provider  │ ─────────► │ provider  │ ─────────► │ provider  │
         │  + memory │            │  + memory │            │  + memory │
         └───────────┘            └───────────┘            └───────────┘
               └──────── shared hive: memory · mailbox · blackboard · log ───────┘
```

1. You spawn agents — each is a normal terminal process (`claude`, `agy`, `codex`, or custom) with its own working directory, identity, and provider-specific lifecycle.

2. Agents collaborate through the hive — a local git repo of plain files. They write to their own `outbox/`; the harness's router delivers messages into recipients' `inbox/`. No agent ever touches git, using a single-committer design to avoid `index.lock` corruption.

3. The GOD agent runs the floor — it reads requests, resolves routine ones itself, and escalates critical items such as spending, destructive operations, or scope changes into an approvals queue.

4. Everything is visible — watch avatars move, envelopes fly, and the live terminal stream. You can type back into any session, browse its files, and read its git history.

See `HIVE.md` for the full multi-agent design, `SPEC.md` for the terminal/event plane, and `DESIGN.md` for the visual system.

---

# Features

## Talk to one agent, not twelve

Michael is your clone and the main agent you brief.

He assigns work, routes traffic, and escalates the few things that actually need you.

## Hire an agent in a few clicks

Pick the CLI, model, and autonomy level, give the agent a desk, and start working.

Import a ready-made role from the Agent Gallery if you would rather not start from scratch.

## Memory that survives the session

Every agent keeps markdown memory that is mined into a shared, searchable memory layer.

Close the app, come back later, and the agents can still retain what they learned.

## Autonomy with a leash

Set how far each agent may go on its own.

Spend, scope, and destructive operations can come back to you, while a circuit breaker can steer, constrain, and stop agents that loop or run away.

## Watch the whole floor work

Agents walk to stations while they work and envelopes fly desk-to-desk when they communicate.

Click any desk to read that terminal live and type straight back into it.

## Set up once

The onboarding wizard checks what you already have and offers to install missing prerequisites instead of sending you through a maze of documentation.

---

## The Floor

* Every terminal is a real agent.
* Every agent is an avatar.
* A GOD orchestrator coordinates the floor.
* Optional per-agent git worktrees provide isolation.
* The office visually reflects real agent activity.

---

## Memory & Coordination

* Per-agent memory.
* Atomic-file mailboxes.
* Shared blackboard.
* Append-only event log.
* Single-committer git.
* Semantic recall.
* Enterprise Knowledge Graph.

---

## Control & Safety

* Human approval gates.
* Circuit breaker.
* Per-agent token budgets.
* Cost tracking.
* Telemetry.
* Tool activity visibility.

---

## Command Center

* Kanban tasks with dependencies.
* Scheduled missions.
* Heartbeat.
* Fleet monitoring.
* Memory search.
* Activity log.
* CI watcher.
* Skills browser.
* Built-in Monaco IDE.
* Git history and diffs.

---

## Getting Work In and Out

* Slack and webhooks.
* Shareable hires.
* Agent Gallery.
* BYOK keys.
* Local LLMs.
* One-click updates.
* English, Simplified Chinese and Arabic.
* Right-to-left Arabic layout.
* Prerequisites management.

---

## Getting started

### Download the app

Most people want the packaged application.

Signed and notarized macOS builds, plus Windows and Linux builds, are available from the upstream project's releases.

Install it, open it, and the onboarding wizard takes you the rest of the way.

You still need at least one agent CLI on your machine, and the app can install missing ones through:

```text
Settings → Prerequisites
```

### Build from source

Everything below is intended for contributors and people who want to run an unreleased build.

### Prerequisites

* macOS, Windows, or Linux.
* Node.js 18+ and npm.
* A C/C++ toolchain for `node-pty`'s native addon.
* At least one supported agent CLI on your `PATH`.
* Optional API keys and local LLMs.
* Optional semantic memory index.

### macOS

```bash
xcode-select --install
```

### Supported CLI commands

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

## Install & run

Clone this fork:

```bash
git clone https://github.com/Jacuzzik/munder-difflin.git
cd munder-difflin
```

Install dependencies:

```bash
npm install
```

Start the development build:

```bash
npm run dev
```

On first launch you'll go through the onboarding wizard and then land on the floor.

Use **Add agent** to spawn your first session.

---

## Other scripts

### Build

```bash
npm run build
```

### Preview

```bash
npm run preview
```

### Typecheck

```bash
npm run typecheck
```

### Fix `node-pty` after an Electron upgrade

```bash
npm install
```

---

## Architecture

Two data planes feed one renderer:

```text
Terminal Plane
    │
    ├── PTYs
    ├── filesystem
    └── git
         │
         ▼
   Typed Bridge
         │
         ▼
     Renderer
         ▲
         │
    Typed Bridge
         │
         ▼
 Event Plane
    │
    ├── hive
    ├── hook server
    └── router
```

The terminal plane owns PTYs, filesystem access, and git.

The event plane runs the hive, hook server, and router.

The renderer communicates with both through a typed bridge.

See:

```text
docs/ARCHITECTURE.md
HIVE.md
SPEC.md
DESIGN.md
```

for the detailed architecture, multi-agent design, terminal/event plane, and visual system.

---

## Roadmap

### Shipped through v0.4.6

* Simplified Chinese and Arabic interface.
* Right-to-left support.
* Self-hosted fonts.
* Multiple agent engines.
* BYOK keys and local LLMs.
* Voice orchestration.
* Hive memory.
* Mailboxes.
* Blackboard.
* Event log.
* Command Center.
* Kanban.
* Scheduled missions.
* Built-in Monaco IDE.
* Git tooling.
* Integrations registry.
* Secret broker.
* Slack workers.
* Shareable hires.
* Agent Gallery.
* Observability.
* Circuit breaker.
* Durable persistence.
* Session resume.
* Multi-window floors.
* One-click updates.
* Skills browser.
* Prerequisites checking.
* Cost reporting.
* Semantic memory.

See `CHANGELOG.md` for the complete history.

### Next up

* More chat integrations.
* More agent engines and integration templates.
* Fuller avatar coverage driven by real hook events.
* Durable layout and command history.

---

## Contributing

Contributions are welcome.

Start with:

```text
CONTRIBUTING.md
```

The basic development flow is:

```bash
npm install
npm run dev
npm run typecheck
```

Keep the type checker green and derive new UI from the project's design tokens.

### Good areas for contributions

* Real hook events.
* Add-agent flow.
* Configuration UI.
* Cross-platform improvements.
* Agent integrations.
* Office interactions.
* Theme improvements.

Every pull request should include before-and-after evidence for UI changes.

---

## Telemetry

Official builds send a small set of anonymous usage events.

The complete event list, anonymity guarantees, and opt-out methods are documented in:

```text
TELEMETRY.md
```

Forks and source builds may have different telemetry behavior depending on their configuration.

---

# License

## Source Code

The source code is licensed under the MIT License.

See:

```text
LICENSE
```

for the complete license.

## Asset Licensing

The bundled pixel art tilesets and maps are:

**Modern Interiors - RPG Tileset [16X16] by LimeZu**

They are used under the applicable Complete Version licence.

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
* **electron-vite** — Electron tooling.
* **CodeMirror** — editor functionality.
* **Remotion** — landing-page animation.
* **The Office (US)** — inspiration for Munder Difflin.

---

<p align="center">
  <sub>
    A themed fork of Munder Difflin by <b>Jacuzzik</b>.
  </sub>
  <br>
  <sub>
    Built on the original Munder Difflin project.
  </sub>
</p>
