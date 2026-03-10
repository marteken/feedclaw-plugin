# FeedClaw Plugin for Claude

Publish content to X (Twitter) and email newsletters directly from Claude — without leaving your workflow.

## What it does

- **Draft** content for review in your FeedClaw inbox
- **Publish** immediately to X or email
- **Schedule** posts for a specific time
- **Review & approve** pending content from your inbox

## Installation

```bash
# Add the plugin to Claude Code
claude plugin install feedclaw@marteken/feedclaw-plugin
```

## First use

Run `/feedclaw:connect` to link your FeedClaw account. You'll be prompted to visit feedclaw.io/activate and enter a code — takes under a minute.

## Slash commands

| Command | What it does |
|---------|-------------|
| `/feedclaw:connect` | Link your FeedClaw account |
| `/feedclaw:publish` | Publish content immediately |
| `/feedclaw:draft` | Send content to inbox for review |
| `/feedclaw:schedule` | Schedule content for a future time |
| `/feedclaw:inbox` | View and approve pending content |

## Requirements

- A FeedClaw account at [feedclaw.io](https://www.feedclaw.io)
- At least one brand configured with X or email connected

## Get FeedClaw

Sign up at [feedclaw.io](https://www.feedclaw.io) — free to start.
