# OpenClaw Command Cheatsheet

A concise reference for the OpenClaw CLI commands that we use frequently to manage the gateway, sessions, and integrations. Copy/paste these into your terminal when you need to restart services, inspect status, send messages, or run audits.

## Common Commands
| Purpose | Command | Notes |
| --- | --- | --- |
| Restart the OpenClaw gateway (reboots agent + web UI) | `openclaw gateway restart` | Use when the gateway hangs, after configuration changes, or before a deployment. |
| Inspect gateway status and active sessions | `openclaw status` | Shows whether the gateway is online, what channels are connected, and a list of recent sessions. |
| Open the terminal TUI chat interface | `openclaw tui` | Launches a console-based chat session; good for quick interactions without browser access. |
| Run a deep security audit | `openclaw security audit --deep` | Performs configuration + policy checks; the builtin `doctor` helper automatically applies trivial fixes. |
| Send a manual message to a channel (example: Telegram) | `openclaw message send --channel telegram --target @username --message "Halo"` | Replace `@username` and the message text as needed; works for Telegram, Slack, Signal, etc. |

## Pro Tips
- For cron jobs, pair `openclaw gateway restart` with a delay to avoid overlapping warmups.
- The TUI (`openclaw tui`) keeps its own scrollback—press `Ctrl+D` to exit safely when you are done.
- Use `openclaw security audit --deep` after installing new plugins to make sure policies stay compliant.
- Message commands can also include attachments, quotes, or inline buttons via `--message-type` flags (refer to `openclaw message --help`).

## Reference
This repo serves as a living cheatsheet for Mas Nanda and the OpenClaw team. Add new commands here when they become part of your daily workflow.
