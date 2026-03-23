# zedra-plugin

Agent plugin for [Zedra](https://github.com/tanlethanh/zedra) — control your dev environment from your phone.

See [zedra.dev](https://zedra.dev) for the app and full documentation.

## Install

**Claude Code**
```
/plugin marketplace add tanlethanh/zedra-plugin
/plugin install zedra@zedra
/zedra:zedra-start
```

**Codex**
```bash
curl -fsSL zedra.dev/codex.sh | sh
/zedra-start
```

**OpenCode**
```bash
curl -fsSL zedra.dev/opencode.sh | sh
/zedra-start
```

**Gemini CLI**
```bash
gemini skills install https://github.com/tanlethanh/zedra-plugin.git --path plugins/zedra
/zedra-start
```

## Skills

| Skill | Description |
|-------|-------------|
| `zedra-start` | Launch daemon and print QR for mobile pairing |
| `zedra-status` | Show daemon status and active sessions |
| `zedra-stop` | Stop the daemon |
| `zedra-terminal` | Open a terminal on the connected phone |

## License

MIT
