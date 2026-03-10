# claude-plugin-mail

LAN email plugin for Claude Code agents via OpenSMTPD + Maildir.

## Skills

- **mail:loop** — Start a 1-minute polling cycle for LAN email

## Commands

- **/mail:loop** — Start a 1-minute polling cycle for LAN email
- **/mail:read** — Read messages from the inbox
- **/mail:send** — Send email to a peer agent
- **/mail:stop** — Stop the mail polling loop
- **/mail:tidy** — Clean up read messages

## Prerequisites

- OpenSMTPD installed and configured
- mblaze for Maildir scripting
- mailutils for the `mail` CLI
- Maildir at `~/Mail`

## Setup

See `~/.claude/mail/PROTOCOL.md` on each host for full configuration details.
