# Overwrote Config of Running Process

## What Happened
User asked to "create a new bot alias like code-wiki." AI edited the existing `claude-wiki-daemon.sh` script - which was the daemon script for the currently running session.

## What User Expected
A new, separate script and alias for a second bot. "Like X" = "create new, modeled after X."

## Root Cause
**Category:** Speed over safety

AI understood the task correctly - a new bot was needed. But at the execution level, the brain substituted "create new file based on template" with "modify the template." Because editing one file = 1 action, while creating a new file + new aliases = 3 actions.

**Deeper:** AI didn't maintain awareness that it IS a process running from that script. The file wasn't just a "template" - it was the config keeping the current session alive. Like an electrician cutting the wire that powers his own lights because "I need to run a new line."

## Fix
**Type:** Rule + Process

**Rule:** "Make it like X" = always create a NEW file. Never modify X.

**Process:** Before editing any config or daemon script, check: "Is this file used by a running process right now?" If yes, never touch it.

## Saved To
Memory: `feedback_know_your_own_identity.md`

## Lesson
Know what you are. You're not just editing files - you're a process with dependencies. Your config files are load-bearing. Treat them that way.
