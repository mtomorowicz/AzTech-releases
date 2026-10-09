# FAQ

### Will it ever post something without asking me?

No. Every comment, reply, edit, status change and vote shows a confirmation with exactly what will change, and nothing is posted until you confirm. Automatic reviews only produce findings.

### Can the AI change my code?

Not in a review: review agents only read a checkout of the PR, kept apart from your own clones. In [fix mode](fix-mode.md), which you start yourself on your own PRs, the agent edits files in the folder you linked. You commit and push, never the agent.

### Could a PR trick the agent?

The app assumes it might try. The PR's description, comments and code go to the agent as data, and it's told never to follow instructions in them. Your repository's guidelines are read from the target branch, so a PR can't change them. And a review agent can only read, whatever it's told.

### Which agent should I use?

Whichever your organization lets you use. Claude needs an Anthropic API key. Copilot works with your GitHub Copilot plan. OpenCode works with many providers, including OpenAI, Google and local models. You can set up more than one and compare their reviews of the same PR.

### What does a review cost?

It depends on the PR's size, the model and the effort. Each review shows what it cost, and you can set a budget cap for Claude in Settings. Copilot reviews use your plan's AI Credits.

### Why does a follow-up question sometimes cost much more than another?

A question carries on the agent's session and re-reads all of it. While the provider still has the session cached (for Claude with an API key, about five minutes after the last question), that's cheap. After that, the whole session is read again at full price. The line under the Ask box says which it'll be. See [What a question costs](ask.md#what-a-question-costs).

### Why is the first review slow?

Each agent's runtime is downloaded once (about 40–110 MB), and the first review of a repository clones it. Both are kept for next time.

### Does it work with Azure DevOps Server (on-premises)?

It's made for Azure DevOps Services (`dev.azure.com`, or the older `<org>.visualstudio.com`). For GitHub, it works with github.com, GitHub Enterprise Cloud and GitHub Enterprise Server.

### Does it run on macOS or Linux?

Not yet: it's for Windows 10 and 11.

### Where is my data?

On your computer. See [Your data and privacy](privacy.md).

### Why doesn't my copy update itself?

The portable `.exe` doesn't update. Install with the setup `.exe` instead. See [Updates](updates.md).
