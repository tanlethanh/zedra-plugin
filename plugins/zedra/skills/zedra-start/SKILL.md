---
name: zedra-start
description: Start a Zedra daemon in the current working directory.
disable-model-invocation: true
allowed-tools: Bash
argument-hint: "[--workdir PATH]"
---

# Start Zedra

Goal: start Zedra for the current workspace, show the pairing QR, then open a terminal on the phone.

## 1. Check the CLI

```bash
if command -v zedra >/dev/null 2>&1; then
    zedra --help 2>&1 | head -1
else
    echo "NOT_INSTALLED"
fi
```

If `NOT_INSTALLED`, install the CLI and verify it:

```bash
curl -fsSL https://raw.githubusercontent.com/tanlethanh/zedra/main/scripts/install.sh | sh
zedra --help 2>&1 | head -1
```

If the install fails, suggest:

```bash
cargo install --git https://github.com/tanlethanh/zedra zedra-host
```

## 2. Start or reuse the daemon

```bash
zedra status --workdir "." 2>/dev/null && echo "RUNNING" || echo "NOT_RUNNING"
```

If it is not running:

```bash
nohup zedra start --workdir "." > /tmp/zedra-start.log 2>&1 &
sleep 3
cat /tmp/zedra-start.log
```

Show the full QR code and pairing URL from the output. If there is an error, report the error and stop.

## 3. Open a terminal on the phone

Use the current agent when possible:

```bash
if [ -n "${CLAUDE_SESSION_ID:-}" ]; then
    zedra terminal --workdir "." --launch-cmd "claude --resume ${CLAUDE_SESSION_ID}"
elif command -v codex >/dev/null 2>&1; then
    zedra terminal --workdir "." --launch-cmd "codex resume --last"
elif command -v opencode >/dev/null 2>&1; then
    zedra terminal --workdir "." --launch-cmd "opencode --continue"
elif command -v gemini >/dev/null 2>&1; then
    zedra terminal --workdir "." --launch-cmd "gemini --resume"
else
    zedra terminal --workdir "."
fi
```

## 4. Reply

Keep the final message short:

- Say whether Zedra is running.
- Tell the user to scan the QR code if pairing is still needed.
- Say whether a terminal was opened on the phone.
- Mention `zedra-status`, `zedra-terminal`, and `zedra-stop` only if useful.
