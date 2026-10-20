# Tell reviews what to look for

There are four ways to steer a review, from this one review to all of them.

## This review: the prompt

On a review's start screen, above **Start review** (or in the options of its **Using …** line), **Prompt** is for this review only: "Check the migration can be rolled back", "Is this safe to run twice?"

## Areas to look at hardest: focus

**Focus** picks areas such as security, performance, tests or style. Pick any number. **Save as default** makes them your **preferred focus**, used for new reviews and automatic ones. Settings has it too.

The pencil next to the focus chips (or <kbd>Ctrl</kbd>+<kbd>K</kbd> → "Review focus areas…") shows what each area tells the agent. You can:

- edit the built-in ones: their name, short description and instructions;
- hide the ones you don't use, or reset them;
- add your own, say a checklist for your framework.

A review keeps what it was told, even if you change the areas later.

## A repository's rules: your instructions

**Your instructions for** *(the repository)*, in the review options, are added to every review of that repository: "We use MediatR: flag DbContext used directly in controllers. Ignore generated *.g.cs files."

They're saved on your machine, for you.

## Take them to another computer, or share them

Settings → **Export…** (next to **Saved replies…**) saves your focus areas, your instructions for each repository and your saved replies to a file. Your accounts and keys are never in it. **Import…** reads such a file, say a teammate's, and says what it would change before it does: your focus areas replaced by the file's, instructions added (or replacing yours) for its repositories, and its saved replies you don't have yet added. Below that, it shows what the file says: each focus area, each repository's instructions and each saved reply, folded under its name. Click a name to read it before you import: what a focus area or instructions say goes into the agent's prompt for every review.

## The team's rules: guidelines in the repository

If the repository has a `CLAUDE.md`, `AGENTS.md` or `.github/copilot-instructions.md`, every review reads it, from the PR's **target** branch. That's the place for rules the whole team shares.

## Standing guidance: skills

A longer checklist, or guidance that only matters when certain files change (migrations, a public API, a framework), fits a **skill** better than a focus area: a SKILL.md folder in the app's library, given to every review or only to PRs that change files matching its patterns. See [Give reviews a skill](skills.md).
