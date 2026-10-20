# Give reviews a skill

A **skill** is a folder with a `SKILL.md`: a name and a one-line description at the top, then instructions in Markdown. It's the format Claude Code, GitHub Copilot and OpenCode share, so a skill you have for any of them works here, and so does one you write yourself: a checklist for your framework, the way your team handles migrations, what to look for in a controller.

**Review skills…** (<kbd>Ctrl</kbd>+<kbd>K</kbd>, or Settings → **Skills…**) is the app's library of them. Reviews by Claude, Copilot and OpenCode alike get the ones that apply, in their prompt, after the repository's guidelines and your instructions.

## Add a skill

- **Add from a folder…**: pick the skill's folder (the one holding `SKILL.md`), or a folder of skills: each in a folder of its own, or under a `skills` folder, as a plugin keeps them.
- **From Claude Code…**: what Claude Code has on this computer: your own skills, those synced from your claude.ai account, and the skills of its installed plugins (a plugin not enabled in Claude Code counts too). Tick the ones you want. The box above the list filters it by name, description or plugin, and **Tick all shown** takes what's left; ticks are kept while you filter. The library's own list gets a filter box once it holds a few.

Either way the skill is **copied** into the library, with the text files next to it. Where it came from is left as it is, and changing it there changes nothing here until you add it again. Read a skill's text in the dialog before a review gets it: it goes into the agents' prompts as written.

## When a review gets it

Each skill is used one of three ways:

- **Every review**: its text goes into every review's prompt, whatever the PR changes.
- **When the PR changes files that match**: patterns, one per line. `*` is anything within a name, `**` anything across folders, `?` one character. A pattern without a `/` matches a file's name wherever the file is (`*.cs`, `appsettings*.json`); with one, the whole path from the repository's root (`src/Api/**`, `**/Migrations/*.cs`). A trailing `/` is that folder and everything in it. Case doesn't matter.
- **Not for now**: kept in the library, given to no review.

A review's log says which skills it got (**Skills: …**). The review keeps what it was told: changing or removing a skill later changes nothing for reviews already done, nor for their follow-up questions.

## What the agent does with it

A skill's instructions are guidance, added to the review's own rules; they can't relax them. Nothing in a skill is run: a review has no shell, so a skill that says to run a script or a tool is read, not executed. The other files a skill comes with aren't read by reviews yet.

Long skills are cut: a review takes up to 24,000 characters of each, and 60,000 of all its skills together (the log says when one was left out). A skill that goes into every review costs context on every review, so keep those few and short, and give the rest file patterns.
