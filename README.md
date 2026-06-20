# Zoey4OpenCode 🧠🤖

> **Your Personal AI Companion System — Native to OpenCode**

[![Version](https://img.shields.io/badge/version-1.0.0-6366f1?style=flat-square)](https://github.com/)
[![OpenCode Plugin](https://img.shields.io/badge/OpenCode-Plugin-8b5cf6?style=flat-square)](https://opencode.ai)
[![License](https://img.shields.io/badge/license-MIT-a855f7?style=flat-square)](LICENSE)
[![Privacy](https://img.shields.io/badge/privacy-local-22c55e?style=flat-square)]()
[![Built with Bun](https://img.shields.io/badge/Bun-1.3%2B-0f172a?style=flat-square)](https://bun.sh)

---

## 🌟 What Is Zoey4OpenCode?

**Zoey4OpenCode** is a complete AI companion system that lives inside [OpenCode](https://opencode.ai). It gives you a **team of four specialized AI agents** — each with its own personality and expertise — plus a **persistent memory system** so nothing is ever forgotten.

Think of it as having four expert colleagues on call 24/7:
- A **researcher** who digs up information
- An **architect** who plans and designs
- An **operator** who handles deployments
- A **mentor** who reviews and teaches

Everything runs **locally on your machine**. Zero cloud, zero data leaks, zero subscriptions.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| **🤖 4 AI Companions** | Atlas (research), Architect (design), Operator (devops), Mentor (review) |
| **💾 Persistent Memory** | SQLite-backed — agents remember across sessions, days, weeks |
| **🔌 Native OpenCode Plugin** | Deep integration with OpenCode's agent, command, and skill systems |
| **🎮 3 Interaction Modes** | @mentions, slash commands, or direct tool calls |
| **🔒 100% Local & Private** | All data stays on your machine — no servers, no cloud, no tracking |
| **⚡ Blazing Fast** | Built with Bun + TypeScript, SQLite for instant storage |
| **🎨 Fully Customizable** | Custom instructions, companion configuration, skill customization |

---

## 🧑‍🤝‍🧑 Meet Your Companions

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│    🔬 Atlas           🏗️ Architect        ⚙️ Operator      │
│    Research &         System Design &     DevOps &          │
│    Analysis           Planning            Operations        │
│                                                             │
│    💡 Mentor                                               │
│    Code Review &                                            │
│    Best Practices                                           │
│                                                             │
│         All connected to a shared persistent memory         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 🔬 **Atlas** — Research & Analysis Companion
- **Role:** Gathers intelligence, reads docs, synthesizes findings
- **Best for:** Web research, documentation analysis, data synthesis
- **Temperature:** 0.3 (balanced, thorough)
- **Try saying:** *"@Atlas Research the best database for a real-time chat app"*

### 🏗️ **Architect** — System Design Companion
- **Role:** Designs architecture, plans features, reviews structure
- **Best for:** System design, feature planning, technical decisions
- **Temperature:** 0.2 (precise, structured)
- **Try saying:** *"@Architect Design the folder structure for a microservices app"*

### ⚙️ **Operator** — DevOps & Operations Companion
- **Role:** Manages infrastructure, deployment, CI/CD, automation
- **Best for:** Docker, cloud, pipelines, scripting
- **Temperature:** 0.1 (deterministic, exact)
- **Try saying:** *"@Operator Set up a Docker Compose for this project"*

### 💡 **Mentor** — Code Review & Teaching Companion
- **Role:** Reviews code, teaches patterns, enforces quality
- **Best for:** Code review, best practices, learning
- **Temperature:** 0.3 (supportive, clear)
- **Try saying:** *"@Mentor Review my authentication module for security issues"*

---

## 🚀 Quick Start (30 Seconds)

### Prerequisites
- [OpenCode](https://opencode.ai) installed
- [Bun](https://bun.sh) v1.0+ installed

### Installation

```bash
# 1. Go to the plugin directory
cd ~/.config/opencode/plugins/zoey4opencode

# 2. Install dependencies
bun install

# 3. Build the plugin
bun run build

# 4. Add to opencode.json
#    (Already done if you're reading this after setup)
```

### Verify It Works
```bash
# Restart OpenCode, then type:
/companion list        # → Shows 4 companions
@Atlas Hello!          # → Atlas responds
/memory stats          # → Shows memory statistics
```

---

## 🎮 How to Use

### Talk to Companions
```
@Atlas What's the latest React version?
@Architect How should I structure this API?
@Operator Deploy this to production safely
@Mentor Review my error handling
```

### Manage Memory
```
/memory save "Use SQLite for local storage" tags=decision,database
/memory recall "database decision"
/memory list
/memory stats
```

### Manage Companions
```
/companion list
/companion switch Atlas
/companion status
/companion configure Mentor "Focus on security"
```

---

## 📂 Project Structure

```
~/.config/opencode/
├── agent/companions/           ← Companion definitions (loaded automatically)
│   ├── atlas.md
│   ├── architect.md
│   ├── operator.md
│   └── mentor.md
├── plugins/zoey4opencode/      ← The plugin (TypeScript + Bun)
│   ├── src/
│   │   ├── index.ts            ← Plugin entry, tool registration
│   │   ├── memory-store.ts     ← SQLite memory system
│   │   └── companion-manager.ts ← Companion state management
│   ├── store/                  ← SQLite databases (auto-created)
│   │   ├── zoey-memory.db
│   │   └── zoey-companions.db
│   ├── dist/index.js           ← Compiled plugin
│   └── docs/                   ← 📚 You are here
├── skills/zoey-companions/     ← Auto-loading skill
├── commands/                   ← Slash commands
│   ├── companion.md
│   └── memory.md
└── opencode.json               ← Plugin registration
```

---

## 🔒 Privacy & Data

| Concern | Answer |
|---------|--------|
| Where is my data stored? | Locally in `~/.config/opencode/plugins/zoey4opencode/store/` |
| Is data sent anywhere? | **Never.** Zero network calls for memory/companion data |
| Can I back up? | Yes — copy the two `.db` files in `store/` |
| Can I delete everything? | Delete the `store/` folder — databases recreate fresh |
| Do you track usage? | No telemetry, no analytics, no logging |

---

## 🛠️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                    OpenCode                          │
│  ┌───────────────────────────────────────────────┐  │
│  │         Zoey4OpenCode Plugin (Plugin)          │  │
│  │  ┌──────────┐  ┌──────────┐  ┌─────────────┐ │  │
│  │  │ Memory   │  │Companion │  │ Integration  │ │  │
│  │  │ Tools    │  │ Tools    │  │ Hub         │ │  │
│  │  └────┬─────┘  └────┬─────┘  └──────┬──────┘ │  │
│  │       │              │               │         │  │
│  │  ┌────▼──────────────▼───────────────▼──────┐ │  │
│  │  │           SQLite Databases                │ │  │
│  │  │   zoey-memory.db  │  zoey-companions.db  │ │  │
│  │  └──────────────────────────────────────────┘ │  │
│  └───────────────────────────────────────────────┘  │
│                                                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────┐ │
│  │  Atlas   │  │Architect │  │ Operator │  │Mentor│ │
│  │ (Subagt) │  │(Subagt)  │  │ (Subagt) │  │(Subgt)││
│  └──────────┘  └──────────┘  └──────────┘  └──────┘ │
└─────────────────────────────────────────────────────┘
```

---

## 📚 Documentation

| Guide | Description |
|-------|-------------|
| [Mind Map](docs/zoey-mindmap.html) | Visual architecture overview — see how everything connects |
| [Non-Developer Guide](docs/zoey-nondev-guide.html) | Friendly guide for non-technical users |
| [User Guide](docs/zoey-user-guide.html) | Complete install, interact, and adjust reference |

---

## 🧪 Development

```bash
# Install dependencies
bun install

# Build the plugin
bun run build

# Watch mode (auto-rebuild on changes)
bun run watch

# Run smoke tests
bun run test-smoke.mjs
```

### Tech Stack
- **Runtime:** Bun 1.3+
- **Language:** TypeScript
- **Storage:** Bun:sqlite (embedded SQLite)
- **Plugin SDK:** @opencode-ai/plugin
- **Bundle Size:** ~465KB

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

- **Add a new companion** — Create a new agent definition in `agent/companions/`
- **Extend the memory system** — Add new query capabilities or integrations
- **Build integrations** — Connect GitHub, Slack, Notion via MCP servers
- **Improve docs** — Better guides, examples, and tutorials

---

## 📄 License

MIT — Free for personal and commercial use.

---

## 🙏 Acknowledgments

- Inspired by [Zoey OS](https://zoeyos.com) — "Your World. Your AI."
- Built for [OpenCode](https://opencode.ai) — the open-source AI coding tool
- Powered by [Bun](https://bun.sh) — fast JavaScript runtime

---

<div align="center">
  <strong>Zoey4OpenCode</strong> — Your AI companions, your data, your control.<br>
  <sub>Built with ❤️ for the OpenCode community</sub>
</div>
