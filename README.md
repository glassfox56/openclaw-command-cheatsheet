# OpenClaw Command Cheatsheet

A concise reference for the OpenClaw CLI commands that we use frequently to manage the gateway, sessions, and integrations. Copy/paste these into your terminal when you need to restart services, inspect status, send messages, or run audits.

## Common Commands
| Purpose | Command | Notes |
| --- | --- | --- |
| Restart the OpenClaw gateway (reboots agent + web UI) | `openclaw gateway restart` | Use when the gateway hangs, after configuration changes, or before a deployment. |
| Inspect gateway status and active sessions | `openclaw status` | Shows whether the gateway is online, what channels are connected, and a list of recent sessions. |
| Open the terminal TUI chat interface | `openclaw tui` | Launches a console-based chat session; good for quick interactions without browser access. |
| Run a deep security audit | `openclaw security audit --deep` | Performs configuration + policy checks; the builtin `doctor` helper automatically applies trivial fixes. |
| Re-run interactive model setup (like onboarding) | `openclaw configure --section model` | Launches the interactive wizard just for model/provider setup (Copilot, OpenAI, etc). |
| Add a new LLM model to the Gateway catalog | `openclaw model add --name gpt-5.1 --provider openai --endpoint https://api.openai.com/v1` | Registers a new model entry so agents can select it when launching tasks; you can also set `--default` or `--priority`. |
| Add a new channel (e.g., Slack workspace) | `openclaw channel add --type slack --workspace-id T12345 --token-file ~/.openclaw/credentials/slack-token.json` | Creates a new Slack channel connector; similar flags exist for Discord/Telegram; tokens stay out of Git by using file paths. |
| Send a manual message to a channel (example: Telegram) | `openclaw message send --channel telegram --target @username --message "Halo"` | Replace `@username` and the message text as needed; works for Telegram, Slack, Signal, etc. |

## Pro Tips
- For cron jobs, pair `openclaw gateway restart` with a delay to avoid overlapping warmups.
- The TUI (`openclaw tui`) keeps its own scrollback—press `Ctrl+D` to exit safely when you are done.
- Use `openclaw security audit --deep` after installing new plugins to make sure policies stay compliant.
- Message commands can also include attachments, quotes, or inline buttons via `--message-type` flags (refer to `openclaw message --help`).

## Reference
This repo serves as a living cheatsheet for Mas Nanda and the OpenClaw team. Add new commands here when they become part of your daily workflow.
