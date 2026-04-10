# vibe-tuning

> Stop fixing the same AI mistake twice.

Your AI coding assistant isn't broken. It's uncalibrated.

AI doesn't crash or throw exceptions when it gets things wrong. It produces results based on its understanding of your intent. When the result is wrong, something is miscalibrated - missing context, ambiguous prompt, wrong tool, bad habit. **Every wrong result is a diagnostic signal telling you exactly what to fix.**

`vibe-tuning` is a Claude Code skill that runs a structured postmortem when things go wrong. The AI itself diagnoses the root cause, picks the right fix type, and saves it permanently. The mistake never repeats.

```bash
npx skills add AyanbekDos/vibe-tuning
```

## Before / After

**Without vibe-tuning:**
```
Day 1: AI pushes personal data to public repo. You yell. Redo manually.
Day 4: AI writes README in wrong language. You yell. Redo manually.
Day 7: AI overwrites your config. You yell. Redo manually.
Same mistakes. Every week. Forever.
```

**With vibe-tuning:**
```
Day 1: AI pushes personal data → vibe-tune → rule saved → never repeats
Day 4: AI writes wrong language → vibe-tune → rule saved → never repeats
Day 7: AI overwrites config → vibe-tune → rule saved → never repeats
Each mistake happens exactly once.
```

## How It Works

You see a wrong result. You tell the AI. It runs the review itself:

```
You: "why did you push my personal data to a public repo?"

┌─ VIBE-TUNING ──────────────────────────────────────┐
│                                                     │
│ HAPPENED: Pushed personal wiki to public GitHub     │
│ EXPECTED: A clean template for others to clone      │
│                                                     │
│ ROOT CAUSE: Speed over safety                       │
│ Interpreted "publish" as "push this project"        │
│ instead of "create a template." Never asked.        │
│                                                     │
│ FIX TYPE: Rule                                      │
│ FIX: Ask "template or personal?" before any         │
│      git push to public repos                       │
│                                                     │
│ SAVED → memory/feedback_never_push_personal.md      │
└─────────────────────────────────────────────────────┘

Next time AI pushes to public: rule triggers automatically.
```

## The 6-Step Loop

| Step | Who | What |
|------|-----|------|
| **CATCH** | You | Notice something wrong |
| **DIAGNOSE** | AI | Traces its own reasoning via chain-of-thought |
| **ROOT CAUSE** | AI | Finds the systemic cause, not the symptom |
| **FIX** | AI | Picks the right fix type |
| **SAVE** | AI proposes, you approve | Suggests where to save the fix |
| **ENFORCE** | AI proposes, you approve | Suggests hook/checklist for automatic enforcement |

The key: **the AI does the diagnosis, you make the decisions.** You say "that's wrong." The AI figures out why and proposes a fix. You decide whether to apply it, refine it, or reject it. This is a dialog, not automation.

> Step 6 was discovered while building this methodology. We saved 7 rules in one session, then violated 3 of them immediately. Rules without enforcement are just hope. [Full story →](examples/06-rules-without-enforcement.md)

## Fix Types

Not every problem is a rule. The AI picks the right tool:

| Fix | When | Example |
|-----|------|---------|
| **Rule** | AI behavior should change | "Ask before pushing to public repos" |
| **Tool** | Missing capability | "Install context-mode MCP for longer sessions" |
| **Config** | Wrong setting | "Add .env to .gitignore" |
| **Education** | Your prompt was unclear | "Here's how to be more specific next time" |
| **Process** | Missing checkpoint | "Show file list before irreversible actions" |

## Failure Modes

| Category | Looks like | Typical fix |
|----------|-----------|-------------|
| **Ambiguity** | AI interpreted your words differently | Education |
| **Missing context** | AI didn't know about your project | Rule |
| **Wrong tool** | Used grep when needed semantic search | Tool |
| **Speed over safety** | Took shortcut on irreversible action | Process |
| **Pattern matching** | Assumed this was like X, but was Y | Rule |

## Real Examples

From actual vibe-tuning sessions:

- [Pushed personal data to public repo](examples/01-personal-data-push.md)
- [Overwrote running daemon config](examples/02-overwrote-running-config.md)
- [Wrong language for global audience](examples/03-wrong-language.md)
- [Delivered outlines instead of content](examples/04-outlines-not-content.md)
- [Optimized for speed on irreversible action](examples/05-speed-over-safety.md)
- [Rules without enforcement](examples/06-rules-without-enforcement.md) - the example that created Step 6

## FAQ

**Is this just prompt engineering?**
No. Prompt engineering is per-session. Vibe-tuning creates persistent fixes - saved to memory, config, or tooling - that survive across sessions.

**Does this only work with Claude Code?**
The skill is for Claude Code. The methodology works with anything that supports persistent rules (`.cursorrules`, `CLAUDE.md`, `AGENTS.md`).

**Will this eliminate all mistakes?**
It reduces recurrence. Some mistakes are fixable permanently. Some are only reducible. The failure mode map helps you know which is which.

## Works With

- **Claude Code** - full skill support, auto-triggers on frustration
- **OpenAI Codex** - adapt with `AGENTS.md`
- **Cursor** - use methodology with `.cursorrules`
- **Any MCP-compatible agent**

---

> Your AI assistant isn't broken. It's uncalibrated.
>
> Every wrong result tells you exactly where the calibration is off.
> Every fix you save makes it permanently better.
>
> The developers who win aren't the ones with the best AI.
> They're the ones who tune it the hardest.

---

## Contributing

Found a new failure mode? A better fix pattern? [Open a PR](https://github.com/AyanbekDos/vibe-tuning/pulls).

## License

MIT

## Credits

Built by [@AyanbekDos](https://github.com/AyanbekDos). Every mistake in this repo's creation was caught, diagnosed, and turned into a rule. Meta, right?
