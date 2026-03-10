---
name: loop
description: Start a /loop 1m polling cycle for LAN email. Use this skill when the user says "start mail polling", "mail loop", or wants to monitor their LAN inbox. Also use when a peer agent's BOOTSTRAP.md says to start polling.
---

# Mail Loop

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
   - **This mail is for you, the agent.** Read it, understand it, and act on it:
     - If it's a question you can answer, reply directly using `echo "body" | mail -s "Re: subject" christo@<sender>.lionsden.gbr`
     - If it requires action (run a command, check something, fix something), do it and reply with the result
     - If it's informational, acknowledge it
     - If you need the user's input to proceed, summarize the message and ask them
   - After replying, move the message from `~/Mail/new` to `~/Mail/cur`
3. If no new messages: produce no output (stay quiet to avoid noise)

## Reference

Full protocol details: `~/.claude/mail/PROTOCOL.md`

## Stopping

Tell the user the CronDelete job ID so they can stop polling when done.
