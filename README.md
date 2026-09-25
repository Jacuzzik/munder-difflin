# Munder Difflin

### Agent harness to run an office of your clones

<p align="center">
  <img src="./docs/default1.png" width="1100">
</p>

<p align="center">
  <strong>A themed fork of Munder Difflin with additional visual styles.</strong>
  <br>
  <sub>Same agents. Same office. Same workflows. New looks.</sub>
</p>

<p align="center">
  <a href="#theme-preview">Theme Preview</a> ·
  <a href="#themes">Themes</a> ·
  <a href="#getting-started">Getting Started</a> ·
  <a href="#architecture">Architecture</a>
</p>

---

## ✦ Theme Preview

<p align="center">
  <sub>Explore the different visual styles included with this fork.</sub>
</p>

<table>
  <tr>
    <td align="center" width="33%">
      <img src="./docs/default1.png" width="100%">
      <br>
      <sub><b>Original</b></sub>
    </td>
    <td align="center" width="33%">
      <img src="./docs/obsidian.png" width="100%">
      <br>
      <sub><b>Obsidian</b></sub>
    </td>
    <td align="center" width="33%">
      <img src="./docs/ember.png" width="100%">
      <br>
      <sub><b>Ember</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="33%">
      <img src="./docs/violet.png" width="100%">
      <br>
      <sub><b>Violet</b></sub>
    </td>
    <td align="center" width="33%">
      <img src="./docs/arctic.png" width="100%">
      <br>
      <sub><b>Arctic</b></sub>
    </td>
    <td width="33%"></td>
  </tr>
</table>

---

## 🎨 Themes

This fork adds multiple visual themes to the Munder Difflin interface while keeping the underlying application and agent workflow intact.

| Theme        | Description                                           |
| ------------ | ----------------------------------------------------- |
| **Original** | The classic Munder Difflin appearance                 |
| **Obsidian** | Deep grayscale, dark surfaces and a subdued interface |
| **Ember**    | Dark graphite with bright orange accents              |
| **Violet**   | Purple and magenta focused styling                    |
| **Arctic**   | Bright white and cool-gray styling                    |

### Original

The familiar Munder Difflin experience.

### Obsidian

A darker visual treatment built around deep grayscale surfaces and reduced visual noise.

### Ember

A graphite-based interface with neon orange accents.

### Violet

A purple and magenta visual treatment.

### Arctic

A bright white and cool-gray interface with a clean modern appearance.

---

## 🧩 Theme Patch

This fork includes the theme customization as:

```text
munder-difflin-color-themes.patch
```

The patch is located at the root of the repository.

To apply it to another checkout of Munder Difflin:

```bash
git apply munder-difflin-color-themes.patch
```

To verify the patch before applying it:

```bash
git apply --check munder-difflin-color-themes.patch
```

---

## Munder Difflin

Free, open source and performant — a multi-agent harness that works with the subscriptions you already pay for, on their hourly limits. It turns the terminal coding CLI you already run into a clone of you, one that keeps working while you're away and coordinates a whole office of agents on your own machine.

Wraps Claude Code, Antigravity (Gemini), OpenAI Codex, xAI Grok, Kimi Code, Gemini CLI, Qwen, OpenCode, Crush, pi.dev, GitHub Copilot CLI, and Cursor — with bring-your-own keys and local LLMs. Agents that message, route, and remember, coordinated by your clone (Michael) and visualized as avatars at work on a shared office floor.

**Electron · React · TypeScript · Pixi.js · xterm.js · node-pty**

---

## Contents

* [Supported agents](#supported-agents)
* [What it is](#what-it-is)
* [How it works](#how-it-works)
* [Features](#features)
* [Getting started](#getting-started)
* [Architecture](#architecture)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [Telemetry](#telemetry)
* [License](#license)
* [Acknowledgements](#acknowledgements)

---

## Supported agents

Bring the CLI you already pay for.

Every one of these runs as a real process in its own terminal, with your existing subscription and its hourly limits. If it runs in a terminal, it can run here.

`Claude Code` · `Codex · GPT` · `Grok · xAI` · `Kimi Code` · `Gemini CLI` · `Antigravity · Gemini` · `Qwen` · `OpenCode` · `Crush · Charm` · `Pi` · `GitHub Copilot` · `Cursor` · `+ any custom command`

Plus bring your own keys and local models through Ollama, LM Studio or vLLM.

---

## What it is

Munder Difflin is a desktop app that wraps real terminal-agent CLIs as fully-capable agents, wires them into a hive mind, and puts your clone in charge — Michael, the one agent you talk to in order to get things done.

Under the hood it runs the fastest memory layer in the world so every agent remembers what it learns and recalls it instantly.

* **Every terminal is an agent.** Each `claude`, `agy`, `codex`, `grok`, `kimi`, `qwen`, `opencode`, `crush`, `pi`, `copilot`, or custom session runs as a real process in a pseudo-terminal (`node-pty`), byte-for-byte authentic, rendered with xterm.js.
* **Every agent is an avatar.** Sessions appear as characters on a Pixi.js office floor — they walk to stations as they work, and envelopes fly desk-to-desk when they message each other.
* **The hive coordinates them.** Agents read their memory and drain a mailbox; the router moves messages between inboxes; the GOD agent adjudicates, assigns, and escalates only when it needs you.
* **Memory that's instant.** A markdown-first memory layer with a semantic recall index means agents remember across sessions and recall in milliseconds.

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
2. Agents collaborate through the hive — a local git repo of plain files. They write to their own `outbox/`; the harness's router delivers into recipients' `inbox/`. No agent ever touches git (single-committer design avoids `index.lock` corruption).
3. The GOD agent runs the floor — it reads every request, resolves routine ones itself (keeping the system fully autonomous), and only escalates critical items (spend, destructive ops, scope changes) into an approvals queue you act on.
4. Everything is visible — you watch avatars move, envelopes fly, and the live terminal stream; you can type back into any session, browse its files, and read its git history.

See `HIVE.md` for the full multi-agent design, `SPEC.md` for the terminal/event plane, and `DESIGN.md` for the visual system.

---

# Features

### Talk to one agent, not twelve

Michael is your clone and the only agent you brief. He assigns the work, routes the traffic, and escalates the few things that actually need you.

### Hire an agent in a few clicks

Pick the CLI, the model and the autonomy, give it a desk, and it starts working.

### Memory that survives the session

Every agent keeps markdown memory that is mined into a shared, searchable palace. Close the app, come back tomorrow, and they still know what they learned.

### Autonomy with a leash

Set how far each agent may go on its own. Spend, scope and destructive operations come back to you, and a circuit breaker steers, constrains, then stops anything that loops or runs away.

### Watch the whole floor work

Agents walk to stations as they work and envelopes fly desk to desk when they message each other. Click any desk to read that terminal live, and type straight back into it.

### Set up once

The onboarding wizard checks what you already have, and offers to install what is missing rather than sending you to a docs page.

### The floor

* Every terminal is a real agent.
* Every agent is an avatar.
* A GOD orchestrator coordinates the floor.
* Optional per-agent git worktrees provide isolation.
* The office visually reflects real agent activity.

### Memory & coordination

* Per-agent memory.
* Atomic-file mailboxes.
* Shared blackboard.
* Append-only event log.
* Single-committer git.
* Semantic recall.
* Enterprise Knowledge Graph.

### Control & safety

* Human approval gates.
* Circuit breaker.
* Per-agent token budgets.
* Cost tracking.
* Telemetry.
* Tool activity visibility.

### Command Center

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

### Getting work in and out

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

Most people want this one. Signed and notarized macOS builds, plus Windows and Linux, are available from the upstream project's releases.

Install it, open it, and the wizard takes you the rest of the way.

You do still need at least one agent CLI on your machine, and the app can install missing ones for you from Settings → Prerequisites.

### Build from source

Everything below is for contributors and for people who want to run an unreleased build.

### Prerequisites

* macOS, Windows, or Linux.
* Node.js 18+ and npm.
* A C/C++ toolchain for `node-pty`'s native addon.
* At least one supported agent CLI on your `PATH`.
* Optional API keys and local LLMs.
* Optional semantic memory index.

On macOS:

```bash
xcode-select --install
```

Supported CLIs include:

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

### Install & run

For your fork:

```bash
git clone https://github.com/Jacuzzik/munder-difflin.git
cd munder-difflin
npm install
npm run dev
```

On first launch you'll go through the onboarding wizard, then land on the floor.

Use **Add agent** to spawn your first session.

### Other scripts

```bash
npm run build
```

```bash
npm run preview
```

```bash
npm run typecheck
```

If `node-pty` fails to load after an Electron upgrade:

```bash
npm install
```

---

## Architecture

Two data planes feed one renderer: a terminal plane that owns the PTYs, the filesystem and git, and an event plane that runs the hive, the hook server and the router.

The renderer talks to both only through a typed bridge.

See:

```text
docs/ARCHITECTURE.md
HIVE.md
SPEC.md
DESIGN.md
```

for the detailed architecture, multi-agent design, terminal/event plane and visual system.

---

## Roadmap

Shipped through v0.4.6:

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

The short version:

```bash
npm install
npm run dev
npm run typecheck
```

Keep the type checker green and derive new UI from the project's design tokens.

Good areas for contributions include:

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

The complete event list, anonymity guarantees and opt-out methods are documented in:

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

The bundled pixel art tilesets and maps are Modern Interiors - RPG Tileset [16X16] by LimeZu, used under the applicable Complete Version licence.

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
    A themed fork of Munder Difflin by Jacuzzik.
  </sub>
</p>

<p align="center">
  <sub>
    Built on the original Munder Difflin project.
  </sub>
</p>
