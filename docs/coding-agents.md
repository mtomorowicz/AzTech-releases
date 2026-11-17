# Coding agents

Let your own coding agent read what AzTech PRador knows: your queue, a pull request, its comment threads, and the findings of its reviews. Then "fix what the review found on this branch" works from **Claude Code**, **GitHub Copilot** (in a terminal, VS Code, Rider and the other JetBrains IDEs, or Visual Studio) or **OpenCode** without copying anything across.

It's off until you turn it on, and your agent writes nothing to Azure DevOps or GitHub through it.

## Turn it on

1. Open **Settings** → **Coding agents** (or <kbd>Ctrl</kbd>+<kbd>K</kbd> → "Coding agents…").
2. Tick **Let my coding agents use AzTech PRador**. It says **Listening**, with the address your agents call: this computer's own, on port 47811 unless you pick another.
3. Under **Clients**, pick the agent you use from the list and click **Add client**. Each gets a token of its own.
   - **Claude Code**
   - **Copilot CLI and VS Code**: the `copilot` command and Copilot Chat in VS Code read one list of MCP servers, so one client covers both.
   - **Copilot in JetBrains IDEs**: Rider, IntelliJ IDEA and the others share one list.
   - **Copilot in Visual Studio**
   - **OpenCode**
4. Connect it:
   - **Claude Code**: click **Add to Claude Code**. The app shows the command it will run, then runs Claude Code's own command for you, so it has an `aztech-prador` server in all your projects. The same command is shown under it, if you'd rather run it yourself.
   - **Copilot** (each of the three): click **Add to …**. The app shows what it will add, then writes an `aztech-prador` server into that Copilot's list of MCP servers, next to the servers already there; anything else in the file, comments included, stays as it was. It says which file under the button. The button is there once that Copilot has run on this computer; otherwise **Connect…** shows the settings and where they go, to add yourself.
   - **OpenCode**: **Connect…** shows a block to add to your `opencode.json` (or the project's), next to what's already there.

   The client then says **Set up**.
5. Start your agent again (in Claude Code, `/mcp` also does; in VS Code, reload the window; in an IDE, Copilot Chat's agent mode lists the tools), and ask it something. Where an agent shows its servers' names and icons (VS Code's tools picker, say), it's **AzTech PRador**, with the app's icon and its version.

## What it can do

| Tool | What it does |
|---|---|
| `list_pull_requests` | Your queue: the PRs that need you, the ones you created, or all active ones, each with its address and how its AzTech reviews stand. From the Azure DevOps project and the GitHub organization the app is set to, both, whichever one it's showing; it says which it read |
| `find_pull_request` | The pull request for the branch you're on, from the repository's remote URL: any repository of your Azure DevOps organization or on your GitHub, not only the project the app shows |
| `get_pull_request` | A pull request: votes, checks (a failed build with its first errors), work items, its commits, the files it changes, its description |
| `get_file_diff` | What a pull request changes in one file, as a diff, so your agent can read a change without a copy of the repository |
| `get_comment_threads` | Its comment threads, open ones or all, with every comment. On GitHub also what reviewers wrote with their reviews, and the conversation's comments, which GitHub doesn't mark open or resolved. Comments only automation bots wrote (test results, coverage) are left out, as in the **Comments** tab, unless your agent asks for them; the answer says how many |
| `get_review_findings` | The latest finished AzTech review by each agent: its summary and the findings still open, with their lines and suggested fixes. It says when a newer review is running or failed, and when the pull request has been pushed to since |
| `add_draft_comment` | A comment in **your drafts**: on lines of a changed file, on the whole pull request, or a reply to a thread. Asked for again (after a timeout, say), it isn't added twice |
| `list_drafts` | The drafts waiting on a pull request, yours too, each saying who wrote it and where it goes, so your agent doesn't answer a thread you've answered |
| `update_draft` | Changes or removes a draft that agent added. Yours, and other agents', it leaves alone |
| `mark_finding_fixed` | Marks a finding fixed in AzTech |
| `start_review` | Starts an AzTech review of what's pushed, only if you allowed that client to |

A long list of threads or findings, or a long diff, reaches your agent in parts: each answer says how many it has and how to ask for the rest, so a busy pull request is never too much for it to take.

Things to try:

- "What's waiting for my review in AzTech?"
- "Summarise what changed in this pull request."
- "Find the AzTech findings for this branch and fix them."
- "Draft replies to the open threads on my pull request as AzTech drafts."
- "Mark the findings you fixed as fixed in AzTech."

## What stays yours

- **A pull request by its address is that one.** Your agent names a pull request by its web address, and the app looks it up where the address says, in any project of your organization: never a repository of the same name in the project on screen. A draft on a pull request that isn't there is refused.
- **Nothing is posted.** A comment your agent drafts waits in your drafts (the Comments panel, and the header's **N drafts · Post…**), marked **from Claude Code** or whichever client wrote it. You read it, change or delete it, and post it from **Post…**, with its confirmation, as any draft. Your agent can change or take back only the drafts it added itself. The bell says when an agent added some.
- **Reviews only if you say so.** Tick **May start reviews** on a client to let it start one. A review it starts is like any other: read-only, it posts nothing, with the repository's skill profile if it has one, and it costs what any review costs (it counts in **Usage and spend** and towards your budget). Its log says which client started it. Coding agents can start 20 reviews a day between them, and have 3 running at once, however many your agent asks for in one go; closing the app doesn't start the day's count again. One asked to review what's new when nothing is starts nothing.
- **Marked fixed** says by whom ("Marked fixed by Claude Code"), and a re-review after you push still has the last word.
- **Recent calls** lists what each client did this session.
- **New token** gives a client a new token; the old one stops working at once. A client the app added to its agent gets the new token there too; otherwise connect it again. **Remove** (the bin) stops the token for good, and takes the `aztech-prador` server out of an agent the app added it to.
- **Remove from …** (under **Connect…**) takes the server out of the agent and keeps the client. In a Copilot's list only the `aztech-prador` server goes; the rest stays.
- Untick the switch and nothing listens any more.

## Your data

- **Only this computer.** The endpoint listens on this computer's own loopback address only, so nothing on the network can reach it; it refuses requests from web pages, and answers only a token you gave out. It's there while AzTech PRador runs, in the tray too.
- **What your agent reads goes to its own AI provider**, as if you'd pasted it into it: pull request text, the code it changes, comments and findings. Use an agent your organization allows for its code.
- **Text written by others** (titles, branch names, descriptions, comments, file names, build output) is marked as such, so your agent treats it as data rather than instructions. So are a review's findings: an AI wrote them after reading the pull request.
- **The token is in your agent's settings.** Treat it like a password: if it's been seen, give the client a new token.

## If it doesn't connect

- **AzTech PRador must be running.** In the tray counts.
- **"Port … is in use by another program"**: type another port and click **Use port …**. An agent the app added (it says **Set up**) is given the new address: start it again. Connect any other again, with the settings **Connect…** shows.
- **Your agent says the token is unknown**: it was replaced or the client removed. **Add to …** again, or run the new command.
- **The Add to … button is greyed out**: for Claude Code, its command isn't on this computer (or not on its PATH): run the command shown where it is installed. For a Copilot, it hasn't run on this computer yet: start it once (in an IDE, open Copilot Chat) and open **Connect…** again, or add the settings shown yourself.
- **"… isn't JSON the app can read, so it's left as it is"**: the Copilot's list of MCP servers has a mistake in it. Put it right (the message names the file), or add the settings shown yourself.
- **Your agent doesn't list the tools**: start it again after adding the server; Claude Code lists them with `/mcp`. Copilot shows them in agent mode.
