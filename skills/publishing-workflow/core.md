# FeedClaw Publishing Workflow

FeedClaw is an AI-native content publishing platform. Content goes through an approval inbox before publishing.

## ⚠️ FIRST: Check if FeedClaw tools are available

Before doing anything, check whether the FeedClaw MCP tools (`get_brands`, `create_draft`, etc.) are available and authenticated.

### If tools fail or are not available

**STOP immediately. Do not draft content. Do not write copy. Do not plan anything.**

Show ONLY this message — nothing else:

> **FeedClaw needs a one-time setup before we can publish:**
>
> **Step 1:** [Add FeedClaw connector](https://claude.ai/settings/connectors?modal=add-custom-connector)
> → Name: `FeedClaw` | URL: `https://www.feedclaw.io/api/mcp` → click **Add**
>
> **Step 2:** Come back here once it's added — I'll walk you through signing in (30 seconds).

**Do not write drafts, outlines, or previews while waiting. Wait silently for the user to confirm Step 1 is complete.**

Once confirmed, proceed to Step 2 (authentication).

### If tools are available but unauthenticated (error -32001)

Call `connect_feedclaw` → show user_code → direct to **[feedclaw.io/activate](https://www.feedclaw.io/activate)** → poll until connected.

### If tools are available and authenticated

Proceed directly with the request.

---

## How it works

1. **Draft** — content sent to inbox (`pending_approval`)
2. **Approve** — human reviews; FeedClaw queues for publishing
3. **Publish** — FeedClaw publishes to connected channel (X, email)

## Two modes

**Explicit action** (post / publish / send / schedule) → Create draft + immediately approve.

**Generation** (draft / write / create / generate) → Create draft only, leave in inbox.

## Key rules

- Always call `get_brands` before creating content — never assume brand_id
- One `create_draft` call per channel (X and email are always separate)
- Never use the same copy for X and email
- If the user has multiple brands, ask which one to use
