# FeedClaw Publishing Workflow

FeedClaw is an AI-native content publishing platform. Content goes through an approval inbox before publishing.

## ⚠️ FIRST: Check if tools are available

Before doing anything, check whether the FeedClaw MCP tools (`get_brands`, `create_draft`, etc.) are available.

### If tools are NOT available (Cowork / Claude.ai)

Tell the user exactly this:

> "To use FeedClaw, you need to add it as a connector first:
> 1. Go to **Claude Settings → Connectors**
> 2. Click **Add connector**
> 3. Enter the URL: `https://www.feedclaw.io/api/mcp`
> 4. Save and come back here
>
> Once the connector is added, I'll walk you through signing in."

Do NOT attempt to call any tools until the user confirms the connector is added.

### If tools ARE available but unauthenticated

If any tool returns error code `-32001` or "Authentication required":
1. Call `connect_feedclaw` to start authentication
2. Show the user: "Visit **feedclaw.io/activate** and enter this code: `{user_code}`"
3. Poll `check_connection` every 5 seconds until approved
4. Confirm: "✅ FeedClaw connected. Let's continue."

### If tools ARE available and authenticated

Proceed directly with the user's request.

---

## How it works

1. **Draft** — content created and sent to inbox (`pending_approval`)
2. **Approve** — human reviews and approves; FeedClaw queues for publishing
3. **Publish** — FeedClaw publishes to connected channel (X, email)

## Two modes

**Explicit action** (post / publish / send / schedule):
→ Create draft + immediately approve. No second confirmation needed.

**Generation** (draft / write / create / generate / prepare):
→ Create draft only. Leave in inbox for human review.

## Key rules

- Always call `get_brands` before creating content — never assume brand_id
- One `create_draft` call per channel (X and email are always separate)
- Never use the same copy for X and email
- If the user has multiple brands, ask which one to use
