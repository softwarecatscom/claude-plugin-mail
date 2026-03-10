---
name: loop
description: Start a /loop 1m polling cycle for LAN email
---

# Start Mail Polling Loop

Start a 1-minute polling cycle that checks ~/Mail/new for incoming LAN email
and displays new messages. Stays silent when the inbox is empty.

**Announce at start:** "Starting mail polling loop (1m interval)."

## Setup

Use `/loop 1m` to schedule this prompt as a recurring cron job:

```
check mail — run: mlist ~/Mail/new | if read -r f; then echo "New mail:"; for m in ~/Mail/new/*; do mshow "$m"; done; else true; fi
```

## When the loop fires

Each minute, the scheduled prompt runs. The agent should:

1. Check `~/Mail/new` for unread messages using mblaze
2. If new messages exist:
   - Display each message with `mshow`
   - Summarize the sender, subject, and key content for the user
   - Ask if the user wants to reply (suggest `/mail:send`)
3. If no new messages: produce no output (stay quiet to avoid noise)

## Reference

Full protocol details: `~/.claude/mail/PROTOCOL.md`

## Stopping

Tell the user the CronDelete job ID so they can stop with `/mail:stop`.
