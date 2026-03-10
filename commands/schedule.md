---
description: Schedule content for a specific time via FeedClaw
argument-hint: "<content and time>"
---

# Schedule

Create and schedule content to publish at a future time.

## Steps

1. Call `get_brands` if brand is not known.
2. Parse the time from the user's message. Convert to ISO 8601 with timezone.
   - Default timezone: ask if not specified (common: America/Guayaquil UTC-5, America/New_York UTC-5/4)
3. Generate platform-specific content.
4. Call `create_draft` with `schedule_at` set to the ISO datetime.
5. Call `approve_post` to confirm scheduling.
6. Confirm: "✅ Scheduled for [human-readable datetime]."

## Time format examples

- "tomorrow at 9am Ecuador time" → `2026-03-11T09:00:00-05:00`
- "Friday at noon ET" → `2026-03-13T12:00:00-05:00`

## Rules

- Always confirm the exact scheduled time with the user before approving
- If the time is ambiguous, ask for clarification — one question only
