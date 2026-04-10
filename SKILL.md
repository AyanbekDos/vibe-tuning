---
name: vibe-tuning
description: "Runs structured AI calibration review when user signals a wrong result. Diagnoses root cause via chain-of-thought, proposes fix (rule/tool/config/education/process), and offers to generate enforcement hooks - all in dialog with user approval. Triggers on: frustration signals ('why did you', 'that's wrong', 'no not that', 'what the hell', 'зачем ты', 'это не то'), explicit request ('let's vibe-tune', 'what went wrong', 'work on your mistake', 'проведи работу над ошибками'), or '/vibe-tuning'."
user-invocable: true
---

# Vibe-Tuning: AI Calibration Review

A wrong result was produced. Run this 6-step postmortem. The AI does the diagnosis, not the user.

## Step 1: CATCH
Acknowledge specifically what went wrong. No deflection.

```
WHAT HAPPENED: [exact action taken]
WHAT USER EXPECTED: [what they actually wanted]
```

## Step 2: DIAGNOSE
Trace your decision process via chain-of-thought:
- What did the user say? How did I interpret it?
- Where exactly did interpretation diverge from intent?
- Could I have asked instead of assumed?

Be honest. "I was lazy" and "I optimized for speed" are valid diagnoses.

## Step 3: ROOT CAUSE
Classify using this taxonomy:

| Category | Signal |
|----------|--------|
| **Ambiguity** | Multiple interpretations, picked wrong one |
| **Missing context** | Didn't know something about project/user |
| **Wrong tool** | Wrong approach for the job |
| **Speed over safety** | Shortcut on something needing care |
| **Pattern matching** | Assumed this was like X, was actually Y |
| **Model limitation** | Genuinely can't do this well |

Then ask: "but WHY did I fall into this category?" Go one level deeper.

## Step 4: FIX
Pick the right fix type. Not everything is a rule:

| Type | When |
|------|------|
| **Rule** | AI behavior should change permanently |
| **Tool** | Missing capability to install |
| **Config** | Setting to change |
| **Education** | User's prompt could be clearer (say respectfully) |
| **Process** | Checkpoint/confirmation to add |

Write the fix: specific, scoped, testable, with WHY.

## Step 5: PROPOSE SAVE
**Do NOT save automatically.** Present the fix to the user and ask for confirmation:
- What will be saved
- Where it will be saved
- How it will work

Only save after user approves. User may want to refine the rule, change the location, or reject it entirely.

## Step 6: PROPOSE ENFORCE
Suggest an enforcement mechanism and explain what it will do:
- **PreToolUse hook** - bash script that fires before dangerous commands
- **CLAUDE.md rule** - project-level instruction loaded every session
- **Checklist** - file to review before irreversible actions
- If no enforcement possible, state that and explain why.

Ask user: "Want me to build this?" If yes, generate the enforcement artifact:
- Write the hook script
- Add to settings.json hooks section
- Or add rule to CLAUDE.md
- Show user what was created, where, and how it triggers

Always show the generated code/config before applying. User approves each step.

## IMPORTANT: This is a DIALOG, not automation

The entire vibe-tuning session is a conversation. The AI surfaces the diagnosis. The user decides what to do. Steps 1-4 are AI analysis. Steps 5-6 are PROPOSALS that need user approval. Never save rules or create hooks without asking.

## Output Format

```
┌─ VIBE-TUNING ─────────────────────────────┐
│ HAPPENED: ...                              │
│ EXPECTED: ...                              │
│ ROOT CAUSE: [category] - [explanation]     │
│ DEEPER: [why I fell into this category]    │
│ FIX TYPE: [Rule/Tool/Config/Education/Process] │
│ PROPOSED FIX: [specific fix]               │
│ SAVE TO: [proposed location]               │
│ ENFORCE WITH: [proposed hook/checklist]    │
│                                            │
│ Apply this fix? (user decides)             │
└────────────────────────────────────────────┘
```

## References

- [Failure mode taxonomy](references/taxonomy.md) - detailed category descriptions
- [Rule quality standard](references/rule-quality.md) - good vs bad rules
- [Hook examples](references/hooks.md) - enforcement patterns
