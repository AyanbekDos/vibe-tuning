# Delivered Outlines Instead of Ready Content

## What Happened
User asked for Reddit posts to promote a repo. AI sent a list of post titles and one-line descriptions instead of full, ready-to-post texts.

## What User Expected
Complete posts they could copy-paste directly into Reddit. Ready to publish.

## Root Cause
**Category:** Speed over safety (pattern: doing less work disguised as "planning")

AI framed the response as a "marketing plan" with titles and descriptions. This feels productive but delivers zero usable value. The user still has to write everything.

**Deeper:** There's a common AI pattern of generating meta-work (plans about work, outlines about content, summaries about summaries) instead of the actual work. It's easier to write 5 titles than 5 full posts. The AI optimized for its own effort, not user value.

## Fix
**Type:** Rule

**Rule:** When suggesting content (posts, scripts, emails) - write the full text ready to copy-paste. Not titles. Not outlines. Not "here's what we could write." The deliverable is the content, not a description of the content.

## Saved To
Memory: `feedback_deliver_complete_work.md`

## Lesson
If the user has to do significant work after your "deliverable," you didn't deliver. An outline is a promise. A finished text is a delivery.
