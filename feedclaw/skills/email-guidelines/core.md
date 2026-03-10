# Email Newsletter Guidelines

## Structure

- `title` field = subject line (also rendered as H1 headline in the email)
- `content` field = markdown body rendered to styled HTML by FeedClaw
- `image_url` field (optional) = hero or featured image — FeedClaw auto-detects orientation

## Image handling (FeedClaw auto-layout)

FeedClaw automatically places images based on orientation:
- **Landscape/horizontal** (wider than tall) → **hero image** full-width above the headline
- **Square** → **featured image** centered below headline
- **Portrait/vertical** (taller than wide) → **inline image** within body content

**NEVER embed images as markdown `![](url)` in the content body.** Always use the `image_url` field in metadata. Markdown image syntax breaks email rendering.

## Content format

```
title: "Your subject line here"
content: |
  Opening paragraph — hook the reader immediately.

  ## Section Heading
  Body content here. Keep paragraphs short (2-4 lines max).

  **Bold** for emphasis. [Links](https://url.com) are supported.

  ## Call to Action
  One clear, specific CTA at the end.

channels: ["email"]
image_url: "https://..." (optional)
```

## Subject line best practices

- Specific > vague: "3 mistakes killing your AV installs" > "Tips for integrators"
- Under 50 characters for mobile preview
- Avoid ALL CAPS, excessive punctuation, spam words ("FREE!!!", "Click now")
- Ask a question or make a bold claim

## Body best practices

- Ideal length: 300–600 words
- One main idea per email — don't combine multiple topics
- End with exactly ONE specific CTA (not "check us out" — be concrete)
- Short paragraphs, generous whitespace

## Deliverability rules (agent must follow)

- Each email goes to subscribers who opted in — write accordingly
- Avoid spam trigger words: "FREE", "LIMITED TIME", "ACT NOW", "GUARANTEED"
- Include the brand name in the first sentence
- Don't use URL shorteners (bit.ly, tinyurl) — use full URLs

## What FeedClaw adds automatically

- Unsubscribe link + one-click unsubscribe (CAN-SPAM compliant)
- Physical address in footer
- List-Unsubscribe headers (Google/Microsoft deliverability)
- Responsive layout, inline CSS, plain-text version
- Brand color accent in header

## Common mistakes to avoid

- Using the same text as the X post
- Embedding images as `![](url)` in content body
- Multiple competing CTAs — pick one
- Subject lines over 60 characters
