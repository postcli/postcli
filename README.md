<div align="center">

# postcli

**Publishing tools for humans and AI agents.**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![GitHub Org](https://img.shields.io/badge/github-postcli-181717?logo=github)](https://github.com/postcli)
[![npm scope](https://img.shields.io/badge/npm-%40postcli-cb3837?logo=npm)](https://www.npmjs.com/org/postcli)

Write, publish, and manage content across platforms from your terminal or through AI agents.

</div>

---

## What is postcli?

postcli is a collection of open-source tools that connect writing platforms to the terminal and to AI. Each platform gets its own package with two interfaces:

- **CLI** for humans who live in the terminal
- **MCP Server** for AI agents (Claude, GPT, local LLMs) that need publishing skills

No browser. No copy-paste. No context switching. Just `postcli-substack notes publish "your thought here"` and it's live.

## Packages

| Package | Platform | Status | Install |
|---------|----------|--------|---------|
| [`@postcli/substack`](https://github.com/postcli/substack) | Substack | ![alpha](https://img.shields.io/badge/status-alpha-yellow) | `npm i -g @postcli/substack` |
| `@postcli/medium` | Medium | ![planned](https://img.shields.io/badge/status-planned-lightgrey) | - |
| `@postcli/linkedin` | LinkedIn | ![planned](https://img.shields.io/badge/status-planned-lightgrey) | - |
| `@postcli/devto` | Dev.to | ![planned](https://img.shields.io/badge/status-planned-lightgrey) | - |
| `@postcli/ghost` | Ghost | ![planned](https://img.shields.io/badge/status-planned-lightgrey) | - |
| `@postcli/hashnode` | Hashnode | ![planned](https://img.shields.io/badge/status-planned-lightgrey) | - |

## How it works

### For humans

```bash
# Authenticate once
postcli-substack auth login

# Manage your content
postcli-substack posts list
postcli-substack notes publish "Shipping a new feature today"
postcli-substack profile me
```

### For AI agents

Each package ships an MCP server that any compatible AI agent can use as a skill.

```json
{
  "mcpServers": {
    "substack": {
      "command": "npx",
      "args": ["@postcli/substack", "--mcp"]
    }
  }
}
```

The AI can then read your drafts, publish notes, check engagement, and manage your content autonomously.

## Architecture

```
                     ┌─────────────┐
                     │   You / AI  │
                     └──────┬──────┘
                            │
                 ┌──────────┴──────────┐
                 │                     │
            ┌────┴────┐         ┌─────┴─────┐
            │   CLI   │         │ MCP Server │
            │ (human) │         │ (AI agent) │
            └────┬────┘         └─────┬─────┘
                 │                     │
                 └──────────┬──────────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
        ┌─────┴─────┐ ┌────┴────┐ ┌─────┴─────┐
        │ Substack  │ │ Medium  │ │ LinkedIn  │
        │ @postcli/ │ │ @postcli│ │ @postcli/ │
        │ substack  │ │ /medium │ │ linkedin  │
        └───────────┘ └─────────┘ └───────────┘
```

## Roadmap

- [x] **@postcli/substack** - Read posts, publish notes, manage profile, comments, likes
- [x] Chrome cookie auto-grab for seamless auth
- [x] MCP Server with 12 tools for AI integration
- [ ] **@postcli/medium** - Posts, drafts, publications
- [ ] **@postcli/linkedin** - Articles, posts, engagement
- [ ] **@postcli/devto** - Articles, comments, tags
- [ ] **@postcli/ghost** - Posts, pages, members (self-hosted)
- [ ] **@postcli/hashnode** - Articles, series, newsletters
- [ ] `postcli` unified CLI - single command for all platforms
- [ ] Cross-posting - publish once, distribute everywhere
- [ ] Content scheduling
- [ ] Analytics aggregation across platforms

## Contributing

Contributions are welcome. Pick a platform, open an issue, or submit a PR.

Each package follows the same structure:

```
@postcli/<platform>/
├── src/
│   ├── client.ts          # Platform API wrapper
│   ├── cli/               # Commander-based CLI
│   │   ├── index.ts
│   │   └── commands/
│   └── mcp/               # MCP server
│       ├── index.ts
│       └── tools.ts
├── package.json
└── tsconfig.json
```

## License

AGPL-3.0. See [LICENSE](LICENSE) for details.

Individual packages may use different licenses. Check each package's LICENSE file.

---

<div align="center">

Built by [@andreahlert](https://github.com/andreahlert)

</div>
