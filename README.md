# tunr plugin

> Screen context provider for [Claude Code](https://claude.ai/code) — a Claude Code plugin.

Observe what the user is looking at and search screen history via MCP tools.

## Commands

- `/tunr:subscribe <channels>` — Subscribe to channels (e.g. `/tunr:subscribe dev` or `/tunr:subscribe dev,research`)
- `/tunr:unsubscribe <channels>` — Unsubscribe from channels
- `/tunr:pause` — Pause all subscriptions (remembered for resume)
- `/tunr:resume` — Resume paused subscriptions

## Install

```
/plugin marketplace add moeki0/tunr-skill
/plugin install tunr@tunr
```

Requires [tunr](https://github.com/moeki0/tunr) to be installed and running:

```bash
brew install moeki0/tunr/tunr
tunr start
```

## License

MIT
