---
name: send
description: Send LAN email to a peer agent. Use when the user says "send mail", "email z490", "reply to", or wants to send a message to another host.
---

# Send Mail

Send an email to a peer on the LAN.

## Arguments

- `to` — recipient address (e.g., `z490` or `christo@z490.lionsden.gbr`)
- `subject` — email subject line

If `to` is just a hostname (e.g., `z490`), expand to `christo@<host>.lionsden.gbr`.

## Steps

1. If no arguments provided, ask the user for recipient and subject.

2. Ask the user for the message body (or use context from the conversation).

3. Send:
   ```bash
   echo "<body>" | mail -s "<subject>" christo@<host>.lionsden.gbr
   ```

4. Confirm delivery.

## Reference

Known hosts are listed in `~/.claude/mail/PROTOCOL.md`.
