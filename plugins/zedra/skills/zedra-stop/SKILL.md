---
name: zedra-stop
description: Stop Zedra for the current workspace.
disable-model-invocation: true
allowed-tools: Bash
argument-hint: "[--workdir PATH]"
---

# Stop Zedra

Check the current daemon:

```bash
zedra status --workdir "." 2>&1
```

If no daemon is running, tell the user and stop.

Otherwise stop it:

```bash
zedra stop --workdir "."
```

Reply with whether the daemon stopped successfully.
