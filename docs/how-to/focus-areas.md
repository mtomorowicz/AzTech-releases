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

## The team's rules: guidelines in the repository

If the repository has a `CLAUDE.md`, `AGENTS.md` or `.github/copilot-instructions.md`, every review reads it, from the PR's **target** branch. That's the place for rules the whole team shares.
