# Your data and privacy

## What stays on your machine

Everything the app keeps is on your computer:

- settings, reviews, your questions and notifications in `%APPDATA%\AzTech`;
- the clones and PR checkouts that reviews read, and the agents' runtimes, in `%LOCALAPPDATA%\AzTech`.

Your Anthropic API key and GitHub token are encrypted with Windows' own data protection for your user account. The app keeps no password or token for Azure DevOps: it asks the Azure CLI for a short-lived token, and holds it in memory only until it expires.

The agents' own tools keep their session history the way they normally do, in your user folder: Claude Code's and Copilot's, and OpenCode's history. That history holds what the agent read. The app deletes Copilot's and OpenCode's sessions of reviews it no longer keeps; Claude Code clears its own after 30 days.

The app has no account and no server of its own, and sends no analytics. The agents run on their makers' own tools (Claude Code, the Copilot CLI, OpenCode), which may report usage to their provider as they normally do.

## What goes where

- **Azure DevOps or GitHub**: to read the PRs, their comments and builds, and to clone the repositories. Writes (comments, replies, votes) happen only after you confirm each one.
- **The model provider you picked** (Anthropic for Claude, GitHub for Copilot, the provider you connected in OpenCode): the agent's prompt and what it reads from the PR's checkout to answer it. That's how a review works: the code it reviews goes to the model. Use a provider your organization allows for its code.
- **OpenCode Zen**, only if you turn on **Offer OpenCode Zen's free models** in Settings → OpenCode (it's off): those models work without signing in, but most may keep what they're sent to train on, so a review would share the PR's code. Leave it off for work code.
- **The package registry**, once per agent: the agent's runtime is downloaded the first time it's needed, and checked against the exact version the app expects.
- **The releases page on GitHub**: to check for updates and download them.

## What the agents can do

Review agents only read the PR's checkout: files, search, and read-only git commands. They can't change files, run other commands, or reach the web.

In [fix mode](fix-mode.md), the agent edits files in the folder you linked. Commands wait for your OK unless you turn on Auto mode. Committing, pushing, switching branches and web requests are blocked, though that check is best effort: see [Fix mode](fix-mode.md#tell-it-what-to-fix).

## Clearing it

The app cleans up on its own:

- a PR's checkout goes when the PR is completed or abandoned, or after 7 days unused;
- a repository's clone goes after 30 days unused;
- the saved reviews of a closed PR go once they're 90 days old.

**Local repo cache**, near the bottom of Settings, shows how much space the clones and checkouts take. **Clear everything** deletes them all now; they come back on the next review.

Uninstalling the app (Windows Settings → Apps) removes the app. To remove its data as well, delete the two `AzTech` folders above.
