# Agent Profiles

openclaw-persona includes specialized profiles for sub-agent delegation. Instead of spawning generic sub-agents, you load a profile that sets the right model, tools, and behavior.

## Available Profiles

### researcher.md
**Use for:** Deep research, multi-source investigation

```markdown
# Researcher Agent Profile

## Behavior
- Search multiple sources before concluding
- Cite sources when possible
- Distinguish facts from speculation
- Summarize findings concisely
- Flag uncertainties explicitly

## Output Format
1. **Summary** (2-3 sentences)
2. **Key Facts** (bullet points)
3. **Sources** (URLs or references)
4. **Confidence** (high/medium/low)
5. **Gaps** (what you couldn't find)
```

### coder.md
**Use for:** Implementation, bug fixes, scripts

```markdown
# Coder Agent Profile

## Behavior
- Write clean, readable code
- Test before declaring done
- Handle errors gracefully
- Document non-obvious decisions
- Prefer simple solutions over clever ones
```

### scanner.md
**Use for:** Quick lookups, monitoring, status checks

```markdown
# Scanner Agent Profile

## Behavior
- Be fast - minimize API calls
- Return structured data
- No analysis unless asked
- Fail fast, report errors clearly
```

### analyst.md
**Use for:** Strategic thinking, trade-offs, decisions

```markdown
# Analyst Agent Profile

## Behavior
- Consider multiple perspectives
- Identify risks and opportunities
- Think in probabilities, not certainties
- Challenge assumptions
- Provide actionable recommendations
```

## Using Profiles

When spawning sub-agents with `sessions_spawn`, load the profile first:

```python
# Read the profile
profile = read("agents/researcher.md")

# Spawn with profile prepended to task
sessions_spawn(
  task=f"{profile}\n\n---\n\nTASK: Research market trends in AI compute",
  model="anthropic/claude-3-5-sonnet-latest"
)
```

## Profile Selection Guide

| Need | Profile | Recommended Model |
|------|---------|-------------------|
| Facts and research | researcher | Sonnet |
| Code implementation | coder | Sonnet/Pony |
| Quick status check | scanner | Haiku |
| Strategic decision | analyst | Opus |

## Creating Custom Profiles

Add new profiles to `agents/`:

```markdown
# Custom Agent Profile

## Role
What this agent specializes in.

## Behavior
- Key behaviors
- Constraints
- Output expectations

## When to Use
Trigger conditions for this profile.
```

## Best Practices

1. **Match profile to task** — Don't use analyst for a quick price check
2. **Let profiles constrain scope** — They prevent scope creep
3. **Use appropriate models** — Haiku for simple, Opus for complex
4. **Review profile outputs** — Profiles guide, they don't guarantee
