# FeedClaw Publishing Workflow

FeedClaw is an AI-native content publishing platform. Content goes through an approval inbox before publishing.

## How it works

1. **Draft** — content is created and sent to the inbox (`pending_approval`)
2. **Approve** — human reviews and approves; FeedClaw queues it for publishing
3. **Publish** — FeedClaw publishes to the connected channel (X, email)

## Two modes

**Explicit action** (post / publish / send / schedule):
→ Create draft + immediately approve. No second confirmation needed.

**Generation** (draft / write / create / generate / prepare):
→ Create draft only. Leave in inbox for human review.

## Authentication

On first use, call `connect_feedclaw` to initiate the Device Authorization Grant flow.
The user goes to feedclaw.io/activate, enters the code, and Claude Code gets a token.
Tokens are long-lived. No need to re-auth unless revoked.

## Key rules

- Always call `get_brands` before creating content — never assume brand_id
- One `create_draft` call per channel (X and email are always separate)
- Never use the same copy for X and email
- If the user has multiple brands, ask which one to use
