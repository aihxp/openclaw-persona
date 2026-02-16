# Contributing to openclaw-persona

Thanks for your interest in contributing! 🦞

## Development Setup

```bash
# Clone the repo
git clone https://github.com/hxp-pxh/openclaw-persona.git
cd openclaw-persona

# Install dependencies
npm install

# Build
npm run build

# Run tests
npm test
```

## Project Structure

```
openclaw-persona/
├── src/
│   ├── cli/
│   │   ├── commands/     # CLI command implementations
│   │   └── index.ts      # CLI entry point
│   └── index.ts          # Library exports
├── templates/            # Workspace templates
├── agents/               # Agent profile templates
├── memory-vault/         # Python memory system
├── docs/                 # Documentation
└── tests/                # Test files
```

## Making Changes

### Templates
Edit files in `templates/` and `agents/`. These are copied to user workspaces on `persona init`.

### CLI Commands
Add new commands in `src/cli/commands/`. Register them in `src/cli/index.ts`.

### Memory Vault
The Python code in `memory-vault/vault.py` handles vector memory. Requires ChromaDB and sentence-transformers.

## Testing

```bash
# Run all tests
npm test

# Run specific test file
node --test tests/init.test.js
```

## Code Style

- TypeScript for CLI
- Python for memory vault
- Use ESM imports
- Keep functions focused and documented

## Pull Requests

1. Fork the repo
2. Create a feature branch
3. Make your changes
4. Run tests
5. Submit PR with clear description

## Questions?

Open an issue or reach out!
