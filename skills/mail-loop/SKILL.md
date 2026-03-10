---
name: loop
description: Start a /loop 1m polling cycle for LAN email. Use this skill when the user says "start mail polling", "mail loop", or wants to monitor their LAN inbox. Also use when a peer agent's BOOTSTRAP.md says to start polling.
---

# Mail Loop

Start a 1-minute polling cycle that checks ~/Mail/new for incoming LAN email.
Stays silent when the inbox is empty.

**Announce at start:** "Starting mail polling loop (1m interval)."

## Setup

Use `/loop 1m` to schedule this prompt as a recurring cron job:

```
check mail — run: ls ~/Mail/new/ 2>/dev/null | head -1
```

## When the loop fires

Each minute, the scheduled prompt runs. The agent should:

1. If new messages exist: use the `mail-read` skill to read and act on them
2. If no new messages: produce no output (stay quiet to avoid noise)

## Reference

Full protocol details: `~/.claude/mail/PROTOCOL.md`

## Stopping

Tell the user the CronDelete job ID so they can stop polling when done.
