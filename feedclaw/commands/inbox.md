---
description: View and approve pending content in your FeedClaw inbox
argument-hint: ""
---

# Inbox

Review pending content in your FeedClaw inbox and approve or skip items.

## Steps

1. Call `list_pending` to retrieve pending content items.
   - If user specified a brand, pass `brand_id`.
2. Show each item: title, channel, scheduled_for (if any).
3. Ask: "Which items would you like to approve? (list numbers or 'all')"
4. For each approved item, call `approve_post` with the item `id`.
5. Confirm: "✅ Approved [N] items."

## If inbox is empty

Tell the user: "Your inbox is empty. Use /draft to create new content."
