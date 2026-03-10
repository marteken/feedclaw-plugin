---
description: Create a content draft in FeedClaw inbox for review
argument-hint: "<content type and topic>"
---

# Draft

Send content to the FeedClaw inbox for human review before publishing.

## Trigger

User says: "draft", "generate", "write", "create content", "prepare a post"

## Steps

1. Call `get_brands` to retrieve available brands. If multiple, ask which one.
2. Identify channel(s) from context.
3. Generate platform-specific content for each channel separately.
4. For each channel, call `create_draft` — one call per channel.
5. Confirm: "✅ Draft in your inbox at feedclaw.io/inbox"

## When to batch

If user asks for "this week's content" or a batch:
- Default: 4–5 X posts + 1 email draft
- Each X post covers a different angle: insight, story, hot take, question, data point
- Never repeat the same hook style twice
- Call create_draft separately for each item

## Rules

- Action verb (post, publish, send) → use /publish instead
- Creation verb (draft, write, generate, create) → use this command
- X and email always get different copy — never duplicate
