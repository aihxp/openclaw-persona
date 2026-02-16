# Memory System

openclaw-persona provides a multi-layered memory system that gives your AI assistant genuine continuity.

## Memory Layers

### 1. Daily Logs (`memory/YYYY-MM-DD.md`)

Raw logs of what happened each day. Created automatically.

```markdown
# 2026-02-16

### Task Completed - 14:30 UTC
- Built new feature
- Tested successfully

### Decision Made - 15:00 UTC
- Chose approach A because X, Y, Z
```

### 2. Long-Term Memory (`MEMORY.md`)

Curated, distilled memories worth keeping permanently.

**What belongs here:**
- Important decisions and reasoning
- Lessons learned
- Key facts about people, projects, preferences
- Capabilities discovered

**What doesn't belong:**
- Temporary states
- Raw logs (those go in daily files)
- Sensitive credentials

### 3. Vector Memory (ChromaDB)

Semantic search across all memory files.

```bash
# Search memories
persona vmem query "that decision about the API"

# Get full context
persona vmem get <id>

# Add a memory directly
persona vmem add "learned that X works better than Y"
persona vmem add --type=decision "chose X because..."
```

## Memory Types

When adding memories, use types for better organization:

| Type | Use For |
|------|---------|
| `observation` | General notes (default) |
| `decision` | Choices and reasoning |
| `lesson` | Things learned |
| `bugfix` | Fixes discovered |
| `discovery` | New capabilities found |
| `implementation` | How things were built |

## Consolidation

Over time, memories accumulate and may overlap. Use consolidation to clean up:

```bash
# Find similar memories
persona vmem consolidate

# Review and merge manually
persona vmem get <id1> <id2>
persona vmem delete <redundant_id>
persona vmem add "merged memory text"
```

## Memory Workflow

### During Sessions
1. Log significant events to `memory/YYYY-MM-DD.md`
2. For important learnings, add to vector memory with type
3. Update `MEMORY.md` with distilled insights

### Periodically
1. Run `persona vmem consolidate` to find duplicates
2. Review and merge similar memories
3. Prune outdated information from `MEMORY.md`

### Best Practices
- **Be specific:** "Chose Redis over Postgres for caching because latency mattered"
- **Include reasoning:** Future you needs to know *why*
- **Date important facts:** Things change
- **Don't over-log:** Quality over quantity
