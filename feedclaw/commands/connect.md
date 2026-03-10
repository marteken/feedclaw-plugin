---
description: Connect your FeedClaw account to Claude
argument-hint: ""
---

# Connect FeedClaw

Link your FeedClaw workspace so Claude can publish content on your behalf.

## Step 1 — Add the connector (Cowork / Claude.ai users)

If the FeedClaw tools are not yet available, guide the user:

> "First, add FeedClaw as a connector:
> 1. Go to **Claude Settings → Connectors**
> 2. Click **Add connector**
> 3. Enter the URL: `https://www.feedclaw.io/api/mcp`
> 4. Click Save, then come back here and try again."

Wait for the user to confirm before proceeding.

## Step 2 — Authenticate via Device Grant

Once the connector is added and tools are available:

1. Call `connect_feedclaw` — it returns a `user_code` and a `device_code`.
2. Show the user:

> "Go to **[feedclaw.io/activate](https://www.feedclaw.io/activate)** and enter the code: **`{user_code}`**
>
> I'll wait while you do this — just let me know when you're done, or I'll check automatically."

3. Poll `check_connection` with the `device_code` every 5 seconds (up to 5 minutes).
4. On success, confirm: "✅ FeedClaw connected! You can now publish content."

## Notes

- If the code expires (5 minutes), call `connect_feedclaw` again for a fresh code.
- Once connected, no need to re-authenticate unless the user revokes the token from feedclaw.io.
- Claude Code (CLI) users: the connector is added automatically via `.mcp.json` — skip Step 1.
