---
description: Connect your FeedClaw account to Claude
argument-hint: ""
---

# Connect FeedClaw

## Step 1 — Add the connector (one-time setup)

FeedClaw needs to be added as a custom connector first. Show the user this exact message:

> **One-time setup needed:**
> 1. [Click here to open the connector setup](https://claude.ai/settings/connectors?modal=add-custom-connector)
> 2. Fill in: **Name:** FeedClaw — **URL:** `https://www.feedclaw.io/api/mcp`
> 3. Click **Add**
> 4. Come back and let me know when done

Wait for the user to confirm before proceeding to Step 2.

## Step 2 — Authenticate

Once the connector is added:

1. Call `connect_feedclaw` — returns a `user_code` and `device_code`.
2. Show the user:
> Go to **[feedclaw.io/activate](https://www.feedclaw.io/activate)** and enter: **`{user_code}`**
3. Poll `check_connection` with the `device_code` every 5 seconds until approved.
4. Confirm: "✅ FeedClaw connected!"

## Notes

- Both steps are one-time only — never needed again unless the user revokes access.
- Claude Code CLI users skip Step 1 entirely (`.mcp.json` handles it automatically).
