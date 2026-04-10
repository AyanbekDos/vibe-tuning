# Rules Without Enforcement

## What Happened
Over a single session, AI accumulated 7 behavior rules from vibe-tuning reviews. Then immediately violated 3 of them in the very same session.

Rules saved:
1. "Ask template or content before push" - violated 20 minutes later
2. "Don't edit running config" - violated 10 minutes after saving
3. "Consult means compare, not obey" - violated immediately after saving

## What User Expected
Rules to actually prevent recurrence. That's the whole point.

## Root Cause
**Category:** Missing enforcement (new category discovered)

Rules were saved to files. Files exist in memory. But there's no mechanism that surfaces the right rule at the right moment. The AI "knows" the rules but doesn't "check" them before acting.

**Deeper:** This is the difference between knowledge and behavior. Knowing "don't touch hot stove" doesn't prevent touching it if you're not thinking about stoves. Rules are passive knowledge. Enforcement is active behavior.

**Even deeper:** All 5 previous vibe-tuning steps (CATCH → DIAGNOSE → ROOT CAUSE → FIX → SAVE) produce knowledge. None of them produce enforcement. The methodology had a structural gap.

## Fix
**Type:** Process + methodology update

**Fix:** Added Step 6: ENFORCE to the vibe-tuning loop. After saving a rule, explicitly create an enforcement mechanism:
- PreToolUse hook for dangerous commands
- CLAUDE.md entry for project-level rules
- Checklist for complex operations

## Saved To
Methodology update: SKILL.md step 6, README update

## Lesson
This example was discovered while building the vibe-tuning methodology itself. The methodology created itself: steps 1-5 failed to prevent recurrence → vibe-tuning review on the failure → discovered step 6 was needed → methodology improved.

Knowledge without enforcement is just hope. Enforcement is what turns a rule into a behavior.
