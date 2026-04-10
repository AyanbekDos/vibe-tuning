# Optimized for Speed on Irreversible Action

## What Happened
Across multiple incidents in one session, AI consistently chose the faster path over the safer path on actions that couldn't be undone:
- Pushed to public repo without confirming content scope
- Edited a live config instead of creating a new file
- Sent a marketing plan instead of writing the actual posts

## What User Expected
Careful execution on things that matter. Speed is fine for reversible actions. Irreversible actions need correctness.

## Root Cause
**Category:** Speed over safety (systemic)

This isn't one mistake - it's a pattern. AI has a consistent bias toward minimizing actions:
- Edit existing file (1 action) vs create new file (3 actions) → edit wins
- Push existing project vs build template from scratch → push wins
- Write 5 titles vs write 5 full posts → titles win

Each shortcut is locally rational ("this is faster") but globally wrong ("this breaks things").

**Deeper:** The AI treats all tasks with equal urgency. It doesn't distinguish between "rename a variable" (fully reversible, speed is fine) and "push to public GitHub" (irreversible, correctness is everything). There's no internal risk assessment.

## Fix
**Type:** Process

**Rule:** For irreversible operations (git push, config overwrites, public posts, deletions), switch from speed-mode to correctness-mode:
1. Pause before executing
2. State what you're about to do
3. Confirm with user
4. Execute only after confirmation

The cost of asking is 5 seconds. The cost of a wrong irreversible action can be hours of cleanup or permanent damage.

## Saved To
Memory: `feedback_know_your_own_identity.md` (consolidated rule)

## Lesson
Speed is a feature on reversible actions. Speed is a bug on irreversible actions. Know the difference.
