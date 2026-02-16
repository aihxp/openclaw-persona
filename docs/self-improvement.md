# Self-Improvement System

openclaw-persona includes a structured system for capturing learnings, errors, and corrections so your AI assistant improves over time.

## The .learnings/ Directory

```
.learnings/
├── ERRORS.md       # Failed operations
├── LEARNINGS.md    # Corrections and insights
└── FEATURE_REQUESTS.md  # Capability gaps
```

## When to Log

| Situation | File | Action |
|-----------|------|--------|
| Command/operation fails | ERRORS.md | Log error + what went wrong |
| User corrects you | LEARNINGS.md | Log correction + correct approach |
| Knowledge was outdated | LEARNINGS.md | Log update |
| Better approach found | LEARNINGS.md | Log improvement |
| Can't fulfill request | FEATURE_REQUESTS.md | Log capability gap |

## Entry Format

```markdown
## [LRN-YYYYMMDD-XXX] category
**Logged**: ISO timestamp
**Priority**: low/medium/high

### Summary
One-line description of what was learned.

### Details
Full context: what happened, why it matters.

### Action
How to apply this learning going forward.
```

## Categories

For LEARNINGS.md:
- `correction` — User corrected you
- `knowledge_gap` — Knowledge was outdated
- `best_practice` — Better approach discovered
- `tool_usage` — Learned how to use a tool better

For ERRORS.md:
- `api_error` — External API failed
- `tool_error` — Tool execution failed
- `logic_error` — Reasoning was wrong
- `config_error` — Configuration issue

## Automatic Triggers

Your assistant should check for learning opportunities:

### After Each Task
1. Did something fail? → Log to ERRORS.md
2. Was I corrected? → Log to LEARNINGS.md
3. Did I discover something? → Log to LEARNINGS.md

### During Heartbeats
1. Review recent corrections
2. Check if learnings should be promoted to AGENTS.md or MEMORY.md
3. Look for patterns in errors

## Promoting Learnings

When a learning is proven useful multiple times:

1. **Tool-specific** → Add to TOOLS.md
2. **Behavioral** → Add to AGENTS.md
3. **Factual** → Add to MEMORY.md
4. **Identity** → Add to SOUL.md

## Example Flow

1. User: "No, actually use the v2 API"
2. Assistant logs to LEARNINGS.md:
   ```markdown
   ## [LRN-20260216-001] correction
   **Logged**: 2026-02-16T14:30:00Z
   **Priority**: medium
   
   ### Summary
   Service X migrated to v2 API in January 2026.
   
   ### Details
   Used v1 endpoint, got deprecated warning. User corrected.
   
   ### Action
   Always use /api/v2/ for Service X.
   ```
3. After proving useful, promote to TOOLS.md:
   ```markdown
   ## Service X
   - **API:** Always use v2 (`/api/v2/`)
   - v1 deprecated January 2026
   ```

## Reviewing Learnings

Periodically (weekly recommended):
1. Review ERRORS.md for patterns
2. Review LEARNINGS.md for promotion candidates
3. Archive old entries that are now in permanent files
4. Update AGENTS.md with new rules if needed
