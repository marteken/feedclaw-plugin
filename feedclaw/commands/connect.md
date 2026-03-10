---
description: Connect your FeedClaw account to Claude
argument-hint: ""
---

# Connect FeedClaw

Link your FeedClaw workspace so Claude can publish content on your behalf.

## Steps

1. Call `connect_feedclaw` tool — it returns a `user_code` and a `device_code`.
2. Show the user: "Go to **feedclaw.io/activate** and enter the code: `{user_code}`"
3. Wait for the user to confirm they've entered the code.
4. Call `check_connection` with the `device_code` every 5 seconds until you get a success response.
5. On success, confirm: "✅ FeedClaw connected. You can now publish content."

## Notes

- Tokens are stored securely by the MCP server.
- If the code expires (5 minutes), call `connect_feedclaw` again to get a new one.
- Once connected, no need to re-authenticate unless the user revokes the token.
