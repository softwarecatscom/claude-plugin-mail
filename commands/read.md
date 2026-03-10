---
name: read
description: Read LAN email from ~/Mail
---

# Read Mail

Read messages from the local Maildir inbox.

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

5. Ask the user if they want to reply to any message (suggest `/mail:send`).
