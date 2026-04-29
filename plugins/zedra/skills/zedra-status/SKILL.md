---
name: zedra-status
description: Check whether Zedra is running and show connected sessions.
allowed-tools: Bash
argument-hint: "[--workdir PATH]"
---

# Zedra Status

Check the current workspace first:

```bash
zedra status --workdir "." 2>&1
```

Then list all running instances:

```bash
zedra list
```

Reply with:

- running or not running
- workspace path
- uptime and endpoint ID
- connected sessions and terminal count
