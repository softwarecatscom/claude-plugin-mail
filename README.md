# claude-plugin-mail

LAN email plugin for Claude Code agents via OpenSMTPD + Maildir.

## Skills

- **mail-loop** — Start a 1-minute polling cycle for LAN email

## Prerequisites

- OpenSMTPD installed and configured
- mblaze for Maildir scripting
- mailutils for the `mail` CLI
- Maildir at `~/Mail`

## Setup

See `~/.claude/mail/PROTOCOL.md` on each host for full configuration details.
