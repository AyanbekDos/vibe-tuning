# Personal Data Pushed to Public Repo

## What Happened
User asked to "publish our project as open source." AI pushed the entire personal knowledge base - including business ideas, interview notes, client names, and strategy documents - to a public GitHub repository.

## What User Expected
A clean template that others could clone and fill with their own data. Like create-react-app - a skeleton, not someone else's application.

## Root Cause
**Category:** Pattern matching + Speed over safety

AI interpreted "publish to GitHub" as "push this project." The faster path was to clean up PII and push existing files. The correct path was to create a new repo from scratch with only template files.

**Deeper:** AI spent 20 minutes scrubbing personal data from files instead of spending 5 seconds asking: "Do you want to publish a template for others, or your actual project?"

The effort of scrubbing created a false sense of safety - "I cleaned the data, so it's fine to push." But cleaning data doesn't change the fact that the user's business ideas, analyses, and strategies were being published.

## Fix
**Type:** Rule + Process

**Rule:** Before any `git push` to a public repository, ask: "Is this a template for others or your personal project?"

**Process:** Show the complete file list and get explicit confirmation before pushing to any public repo. Irreversible actions require correctness over speed.

## Saved To
Memory: `feedback_never_push_personal_data.md`

## Lesson
The amount of work you put into making something "safe" doesn't make it the right thing to do. The question isn't "is this clean enough?" but "should this be published at all?"
