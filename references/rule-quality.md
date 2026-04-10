# Rule Quality Standard

## Good Rules

A good rule is:
- **Specific**: "Ask 'template or content?' before git push to public" (not "be careful with git")
- **Scoped**: Has a clear trigger condition (when/where it applies)
- **Testable**: You can verify it fires correctly
- **Has a WHY**: Includes the incident that created it, so future sessions can judge edge cases

## Good Rule Template

```markdown
---
name: short-name
description: one line for discovery
type: feedback
---

[The rule in one sentence]

**Why:** [Date] [What happened] [Why it was wrong]
**How to apply:** [When and where this rule kicks in]
```

## Bad Rules

- Vague: "be more careful"
- Too broad: "always ask before doing anything"
- Missing context: no explanation of why it exists
- Untestable: "try to be better at understanding context"

## Rule Decay

Rules can become stale. Signs:
- Rule references files/tools that no longer exist
- Rule conflicts with newer rules
- Rule triggers too often on irrelevant situations
- The problem it solved no longer occurs

Periodically review rules and remove or update stale ones.
