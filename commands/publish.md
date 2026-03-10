---
description: Publish content immediately to X or email via FeedClaw
argument-hint: "<what to publish and where>"
---

# Publish

Publish content immediately to X (Twitter) or email newsletter via FeedClaw.

## Trigger

User says: "post this", "publish", "send this newsletter", "tweet this"

## Steps

1. Call `get_brands` to retrieve available brands. If multiple brands exist, ask which one to use.
2. Identify the channel from context: "X" / "tweet" → `["x"]`, "email" / "newsletter" → `["email"]`.
3. Generate platform-specific content (do NOT use the same text for X and email):
   - **X**: max 280 weighted chars, plain text, strong hook first line, no markdown
   - **Email**: subject line as `title`, markdown body as `content`, 300–600 words
4. Call `create_draft` with `title`, `content`, `brand_id`, `channels`.
5. Call `approve_post` with the returned `id`.
6. Confirm: "✅ Published to [channel]."

## Rules

- NEVER use the same copy for X and email — they are different formats
- X emoji count as 2 chars — count carefully before calling create_draft
- For email, do NOT embed image URLs as markdown `![](url)` in content
- One channel per create_draft call (separate calls for X and email)
