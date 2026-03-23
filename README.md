# zedra-plugin

Agent plugin for [Zedra](https://github.com/tanlethanh/zedra) — control your dev environment from your phone.

See [zedra.dev](https://zedra.dev) for the app and full documentation.

## Install

**curl**
```bash
# Install Zedra CLI
curl -fsSL zedra.dev/install.sh | sh
# Start Zedra in working directory
zedra start
```

**Claude Code**
```bash
# Inside Claude Code session
/plugin marketplace add tanlethanh/zedra-plugin
/plugin install zedra@zedra
# Restart Claude Code session and start Zedra
/zedra:zedra-start
```

**Codex**
```bash
# Install CLI and setup Codex skill
curl -fsSL zedra.dev/codex.sh | sh
# then in Codex:
/zedra-start
```

**OpenCode**
```bash
# Install CLI and setup OpenCode skill
curl -fsSL zedra.dev/opencode.sh | sh
# then in OpenCode:
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
