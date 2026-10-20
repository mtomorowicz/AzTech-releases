# Give reviews a skill

A **skill** is a folder with a `SKILL.md`: a name and a one-line description at the top, then instructions in Markdown. It's the format Claude Code, GitHub Copilot and OpenCode share, so a skill you have for any of them works here, and so does one you write yourself: a checklist for your framework, the way your team handles migrations, what to look for in a controller.

**Review skills…** (<kbd>Ctrl</kbd>+<kbd>K</kbd>, or Settings → **Skills…**) is the app's library of them. Reviews by Claude, Copilot and OpenCode alike get the ones that apply: in their prompt, after the repository's guidelines and your instructions, or, for the ones you set to **when the agent asks**, as a line each and a tool the agent reads them with when the change calls for one.

## Add a skill

- **Add from a folder…**: pick the skill's folder (the one holding `SKILL.md`), or a folder of skills: each in a folder of its own, or under a `skills` folder, as a plugin keeps them.
- **From Claude Code…**: what Claude Code has on this computer: your own skills, those synced from your claude.ai account, and the skills of its installed plugins (a plugin not enabled in Claude Code counts too), grouped by plugin.
- **From a repository or marketplace…**: a repository of skills, a plugin, or a marketplace's catalog, fetched to pick from. Type it as `owner/repo` (on GitHub), an https link (a GitHub `/tree/<branch>` link works), or a folder on this computer; `#branch` at the end picks a branch or tag. The marketplaces Claude Code knows are listed below the box, read from its own copies: a plugin a marketplace keeps in another repository is fetched when you ask for its skills (**Show its skills**). A private GitHub repository works when the GitHub CLI is signed in to its host.

In each picker the skills are grouped by plugin, with a box per plugin to tick them all and a chevron to fold it (a catalog of many plugins starts folded; **Collapse all** and **Expand all** do them at once); the box above filters by name, description or plugin and shows what matches whatever is folded, **Tick all shown** takes what the filter leaves, and ticks are kept while you filter. **Add them as** says how reviews get what you add: **every review**, **when files match** (it asks for the patterns, and every skill you add gets them; change them per skill afterwards), **when the agent asks**, or **not for now**. Skills from Claude Code and from a folder of skills start as **when the agent asks**, so a plugin's twenty skills cost a line each, not their text; skills from a repository or a marketplace start as **not for now**, so nothing from a stranger goes into a review before you've read it. The library's own list is grouped by where skills came from, with a filter box once it holds a few.

Either way the skill is **copied** into the library, with the text files next to it. Where it came from is left as it is, and changing it there changes nothing here until you update: **Check for updates** at the bottom asks each repository where its branch is now (without fetching it) and compares each folder's file with your copy, then marks the skills that moved on; **Update all** reads them again in one go, one fetch per repository, and says which got new text. One skill at a time: **Read it again** (a folder) or **Fetch it again** (a repository, at the branch it was fetched from). Updating keeps how you use a skill. Read a skill's text in the dialog before a review gets it: it goes into the agents' prompts as written. A skill whose text holds hidden characters (zero-width or bidirectional ones, which can hide instructions from a reader) is shown as such and can't be added.

## When a review gets it

Each skill is used one of four ways:

- **Every review**: its text goes into every review's prompt, whatever the PR changes.
- **When the PR changes files that match**: patterns, one per line. `*` is anything within a name, `**` anything across folders, `?` one character. A pattern without a `/` matches a file's name wherever the file is (`*.cs`, `appsettings*.json`); with one, the whole path from the repository's root (`src/Api/**`, `**/Migrations/*.cs`). A trailing `/` is that folder and everything in it. Case doesn't matter.
- **When the agent asks**: the review's prompt has only the skill's name and what it's for, one line, and the agent has a tool that gives it the skill's text, or one of the files it comes with, when it judges the change touches what the skill is about. The setting for a plugin's many skills: a review of a controller doesn't carry the actor checklist, and the agent opens it when the PR changes an actor.
- **Not for now**: kept in the library, given to no review.

## For one review

A review's start screen (and the **Using …** options) shows the skills that apply to the PR, each in the review unless you click it off; **None this time** leaves them all out of this one review, and the last button opens the library. A few skills are a row of chips. More are a summary line and a line per source (a plugin, a folder), each with a box for the lot and a count; **Choose…** opens a dialog to pick them one by one, with a filter, **All of them** and **None this time**. That choice is for this PR's next review only: the library's settings stay as they are. The **Using …** line counts what the review gets ("1/3 skills", "no skills"), the ones for the agent to ask for included, and the finished review shows the skills it was given: **N on request** for those, and, marked with an eye, each one the agent read.

A review's log says which skills it got (**Skills: …**), which the agent could read (**Skills the agent can read when it needs them: …**) and which it read (**Read skill …**), which you left out, and which didn't fit. The review keeps what it was told: changing or removing a skill later changes nothing for reviews already done, nor for their follow-up questions.

## What the agent does with it

A skill's instructions are guidance, added to the review's own rules; they can't relax them. Nothing in a skill is run: a review has no shell, so a skill that says to run a script or a tool is read, not executed. The other text files a skill comes with (a reference, a longer checklist) are named to the agent with it, and it reads one with the same tool when it needs it, whether the skill is in the prompt or on request. The tool reads the library's copies only: nothing from the PR's checkout, and nothing outside the skill's folder.

Long skills are cut: a review takes up to 24,000 characters of each, and 60,000 of all its skills together (the log says when one was left out). A skill that goes into every review costs context on every review, so keep those few and short, give the rest file patterns, or leave them for the agent to ask for. Follow-up questions have the same list and the same tool.
