---
name: zedra-terminal
description: Open a new terminal on the connected phone.
disable-model-invocation: true
allowed-tools: Bash
argument-hint: "[--launch-cmd CMD]"
---

# Open Zedra Terminal

## 1. Check the daemon

```bash
zedra status --workdir "." 2>&1 || echo "NOT_RUNNING"
```

If `NOT_RUNNING`, tell the user to run the start skill first.

## 2. Open the terminal

If the user provided a launch command, use it:

```bash
zedra terminal --workdir "." --launch-cmd "$ARGUMENTS"
```

Otherwise resume the current agent when possible:

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

Reply with the command result and whether the terminal should now appear on the phone.
