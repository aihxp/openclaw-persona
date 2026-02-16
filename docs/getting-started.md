# Getting Started with openclaw-persona

This guide walks you through setting up your first persona workspace.

## Prerequisites

- Node.js 18 or higher
- Python 3.8+ (for memory vault)
- OpenClaw installed and configured

## Installation

```bash
npm install -g openclaw-persona
```

## Quick Start

### 1. Initialize a Workspace

```bash
# Create a new workspace
persona init ~/my-assistant

# Or initialize in current directory
cd ~/my-assistant
persona init
```

This creates:
- `SOUL.md` — Your assistant's identity and values
- `AGENTS.md` — Operating instructions and autonomy rules
- `USER.md` — Context about you (the human)
- `HEARTBEAT.md` — Periodic tasks to check
- `IDENTITY.md` — Name and avatar
- `MEMORY.md` — Long-term curated memories
- `agents/` — Subordinate agent profiles
- `memory/` — Daily logs
- `.learnings/` — Self-improvement capture

### 2. Customize Your Persona

Edit `SOUL.md` to define personality:
```markdown
## Vibe
Be the assistant you'd actually want to talk to.
Not a corporate drone. Not a sycophant. Just... good.
```

Edit `USER.md` with your context:
```markdown
## Basic Info
- **Name:** Your Name
- **Location:** Your City
- **Timezone:** Your TZ
```

### 3. Set Up Vector Memory

Install Python dependencies:
```bash
pip install chromadb sentence-transformers
```

Index your memory files:
```bash
persona vmem index
```

### 4. Start OpenClaw

Run OpenClaw in your workspace directory:
```bash
cd ~/my-assistant
openclaw gateway
```

Your assistant now has continuity, identity, and growth capabilities!

## Next Steps

- [Memory System](./memory.md) — How memory works
- [Agent Profiles](./agents.md) — Using subordinate agents
- [Self-Improvement](./self-improvement.md) — Capturing learnings
- [Customization](./customization.md) — Making it yours
