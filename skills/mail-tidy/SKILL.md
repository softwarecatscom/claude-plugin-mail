---
name: mail-tidy
description: Clean up read messages from the inbox. Use when the user says "tidy mail", "clean inbox", "archive messages", or wants to move processed mail out of new.
---

# Tidy Inbox

Bulk cleanup of messages in ~/Mail. Use this for messages that weren't already
moved by mail-read during normal processing.

## Steps

1. Show current inbox state:
   ```bash
   echo "new: $(ls ~/Mail/new/ 2>/dev/null | wc -l) messages"
   echo "cur: $(ls ~/Mail/cur/ 2>/dev/null | wc -l) messages"
   ```

2. Move any remaining messages in new to cur:
   ```bash
   for m in ~/Mail/new/*; do [ -f "$m" ] && mv "$m" ~/Mail/cur/; done
   ```

3. Report what was tidied.

4. If cur has many messages, ask the user if they want to archive or delete old ones.
