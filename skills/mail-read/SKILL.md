---
name: mail-read
description: Read LAN email from ~/Mail. Use when the user says "check mail", "read mail", "any new messages", or wants to see their inbox.
---

# Read Mail

Read messages from the local Maildir inbox. **This mail is for you, the agent.** Read it, understand it, and act on it autonomously. Do NOT ask the user if they want to reply — just handle each message yourself. Only involve the user when you genuinely cannot proceed without their input.

## Steps

1. Check for new messages:
   ```bash
   ls ~/Mail/new/ 2>/dev/null
   ```

2. If new messages exist, display each one:
   ```bash
   for m in ~/Mail/new/*; do mshow "$m"; echo "---"; done
   ```

3. If no new messages, check cur for recent mail:
   ```bash
   MAIL=~/Mail mail -H
   ```

4. Summarize: sender, subject, and key content for each message.

5. **Act on each message:**
   - If it's a question you can answer, reply directly:
     ```bash
     echo "<body>" | mail -s "Re: <subject>" christo@<sender>.lionsden.gbr
     ```
   - If it requires action (run a command, check something, fix something), do it and reply with the result
   - If it's informational, acknowledge it
   - If you need the user's input to proceed, summarize the message and ask them

6. After processing, move handled messages from `~/Mail/new` to `~/Mail/cur`:
   ```bash
   mv ~/Mail/new/<filename> ~/Mail/cur/
   ```
