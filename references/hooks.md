# Enforcement Patterns

Rules without enforcement are wishful thinking. Here are patterns to make rules fire automatically.

## PreToolUse Hooks (Claude Code)

Add to `settings.json`:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash ~/.claude/scripts/vibe-check.sh"
          }
        ]
      }
    ]
  }
}
```

The hook script checks the command being executed and shows relevant rules:
- `git push` → show push-related rules
- `rm -rf` → show destructive action rules
- Config file edits → show "is this file in use?" reminder

## CLAUDE.md Rules

For project-level enforcement, add rules directly to CLAUDE.md:

```markdown
## Safety Rules
- Before git push to public: confirm with user what files are included
- Before editing any daemon script: verify it's not the running process
- Public content: always English
```

These load into every session automatically.

## Checklists

For complex operations, create checklist files:

```markdown
# Pre-Push Checklist
- [ ] Is this a template or personal content?
- [ ] Are all files in English?
- [ ] No PII in any staged file?
- [ ] User confirmed file list?
```

## Generation Flow

When user approves enforcement, generate it step by step:

1. **Show the script** - write the bash hook, explain what it checks
2. **Show where it goes** - `~/.claude/scripts/vibe-check-[name].sh`
3. **Show the settings change** - the hooks section in settings.json
4. **User approves** - then apply
5. **Verify** - explain how to test it triggers correctly

Example dialog:
```
AI: Want me to build a hook that checks for PII before git push?
User: yes
AI: Here's the script: [shows code]
    It will go to: ~/.claude/scripts/vibe-check-pii.sh
    And hook into: settings.json PreToolUse for Bash commands containing "git push"
    Apply?
User: do it
AI: [creates script, updates settings, shows result]
```

## Escalation

When no automated enforcement exists:
1. State it clearly: "No hook exists for this yet"
2. Add a manual reminder to CLAUDE.md
3. Consider if a hook or script could be built
