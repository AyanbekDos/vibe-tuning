# Wrong Language for Global Audience

## What Happened
User asked to publish an open source repo on GitHub. AI wrote the README in Russian.

## What User Expected
English. GitHub's audience is global. A Russian README cuts reach by 95%.

## Root Cause
**Category:** Missing context

The user communicates in Russian. The local wiki is in Russian. AI defaulted to the user's language instead of the audience's language.

**Deeper:** AI didn't distinguish between "language I talk to the user in" and "language the deliverable should be in." These are two different things. Private communication = user's language. Public content = audience's language.

## Fix
**Type:** Rule

**Rule:** Public content (GitHub, Reddit, HN, Twitter) is always in English. Russian only for private communication (Telegram, local wiki, TikTok for RU audience).

## Saved To
Memory: `feedback_public_content_english.md`

## Lesson
The language of the conversation is not the language of the deliverable. Always ask: who is the audience?
