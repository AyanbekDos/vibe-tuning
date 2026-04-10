# Failure Mode Taxonomy

## Ambiguity
AI interpreted user's words differently than intended. Multiple valid interpretations existed.
- Signal: "That's not what I meant"
- Typical fix: Education (teach clearer prompting) or Rule (ask when ambiguous)
- Example: "publish to GitHub" interpreted as "push project" vs "create template"

## Missing Context
AI didn't know something about the project, user, or domain.
- Signal: "You should have known that"
- Typical fix: Rule (check X before doing Y) or Config (add to CLAUDE.md)
- Example: Didn't know public repos need English README

## Wrong Tool
Used the wrong approach, tool, or method for the job.
- Signal: "Why didn't you use X instead?"
- Typical fix: Tool (install better tool) or Rule (use X for Y tasks)
- Example: Used grep when semantic search was needed

## Speed over Safety
Took a shortcut on an action that required careful execution. The most common systemic cause.
- Signal: Same fix-type pattern across multiple incidents
- Typical fix: Process (add confirmation step) or Hook (enforce checklist)
- Example: Edited existing config instead of creating new file because it was "faster"

## Pattern Matching
Assumed current situation was like a previous one, but it wasn't.
- Signal: "This is completely different from that"
- Typical fix: Rule (ask when situation seems familiar but might differ)
- Example: Applied another AI's advice without filtering through own judgment

## Model Limitation
AI genuinely cannot do this task well with current capabilities.
- Signal: Repeated failures despite correct rules and context
- Typical fix: Workaround (different approach, human-in-loop, different tool)
- Example: Complex visual design tasks, real-time data analysis
