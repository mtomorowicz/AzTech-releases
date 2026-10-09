<!-- Made from the user guide (docs/) with each release: a change made here is replaced by the next one. -->

# AzTech PRador

A dark-mode Windows app for reviewing pull requests on **Azure DevOps** and **GitHub**, with an AI reviewer at your side: **Claude**, **GitHub Copilot** or **OpenCode**.

![The main window: the PR list, a PR's diff, and Claude's review](docs/images/main-window.png)

- **Your PRs at a glance**: the ones waiting on you, or every active one, with build status, votes and filters.
- **AI reviews**: an agent reads a checkout of the PR, only reads, and finds what's worth your time. You keep, edit or dismiss each finding.
- **Ask about anything**: a finding, the whole PR, or a few lines of the diff.
- **Comments and votes** from the app. **Nothing is ever posted without your confirmation**: every write shows exactly what will change first.
- **Fix mode** for your own PRs: an agent fixes what the review found in your checkout, and you commit and push when you're happy.
- **Notifications** for review requests, new PRs in repos you watch, and replies to your comments.

This repository has the app's releases (the installers, and what's new in each) and its [user guide](docs/README.md).

## Install

1. Download **`AzTech-PRador-Setup-<version>.exe`** from the [latest release](https://github.com/mtomorowicz/AzTech-releases/releases/latest).
2. Run it and follow the steps. Installing **only for me** needs no admin rights.

The installer isn't code-signed, so Windows may say "Windows protected your PC". Choose **More info → Run anyway**.

The app [updates itself](docs/updates.md) from then on.

## Requirements

- **Windows 10 or 11** (x64).
- **[git](https://git-scm.com/downloads)** on your PATH: reviews read a local checkout of each PR.
- For **Azure DevOps**: the **[Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli)**, signed in with `az login`.
- For **GitHub**: the **[GitHub CLI](https://cli.github.com/)**, signed in with `gh auth login`.
- For reviews, at least one agent:
  - **Claude**: an Anthropic API key.
  - **GitHub Copilot**: a GitHub account with Copilot.
  - **OpenCode**: a provider connected in OpenCode (OpenAI, Google, Anthropic, a local model, and many more).

The app signs in through these tools. It stores no Azure DevOps password or token of its own.

## User guide

### Start here

1. [Getting started](docs/getting-started.md): install, sign in, set up an agent, run your first review.
2. [Your data and privacy](docs/privacy.md): what stays on your machine, and what goes where.

### Using the app

- [Pull requests](docs/pull-requests.md): the list, filters, builds, projects, the diff, Azure DevOps and GitHub.
- [Reviews](docs/reviews.md): running a review, the findings, posting and votes.
- [Asking the agent](docs/ask.md): questions about a finding, the PR, a thread or some lines.
- [Comments](docs/comments.md): threads, replies, and commenting on code.
- [Fix mode](docs/fix-mode.md): an agent fixing your own PR in your checkout.
- [Notifications](docs/notifications.md): the bell, Windows notifications, watched repos, the tray.
- [Keyboard](docs/keyboard.md): shortcuts and the command palette.
- [Updates](docs/updates.md): how the app updates itself, and what's new.

### How to

- [Re-review after a push](docs/how-to/re-review-after-a-push.md)
- [Ask about some lines of the diff](docs/how-to/ask-about-lines.md)
- [Fix your own PR](docs/how-to/fix-your-own-pr.md)
- [Tell reviews what to look for](docs/how-to/focus-areas.md)
- [Get notified about new PRs in a repo](docs/how-to/watch-a-repo.md)
- [Review GitHub pull requests](docs/how-to/use-github.md)

### When something's wrong

- [Troubleshooting](docs/troubleshooting.md)
- [FAQ](docs/faq.md)

## License

[MIT](LICENSE)
