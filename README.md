# AzTech PRADOr

A dark-mode Windows app for reviewing Azure DevOps pull requests with Claude or GitHub Copilot.

- **Your PRs at a glance:** the ones waiting on you or all active ones, with build status, votes and filters.
- **AI review:** Claude or Copilot reviews a local checkout of the PR, read-only, and you keep, edit or dismiss what it finds.
- **Comments:** reply, resolve and post from the app. Nothing is written to Azure DevOps until you confirm exactly what will be posted.
- **Notifications:** for review requests, new PRs in repos you watch, and replies to your comments.

This repository hosts the releases only.

## Install

1. Download **`AzTech-PRADOr-Setup-<version>.exe`** from the [latest release](https://github.com/mtomorowicz/AzTech-releases/releases/latest).
2. Run it. It installs for your Windows user only, with no admin rights needed.

The installer isn't code-signed, so Windows may say "Windows protected your PC". Choose **More info → Run anyway**.

## Requirements

- Windows 10 or 11 (x64)
- [git](https://git-scm.com/downloads) on your PATH
- [Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli), signed in with `az login`. The app reaches Azure DevOps through your `az` sign-in and stores no tokens of its own.
- For reviews, one or both of:
  - an Anthropic API key (Claude)
  - a GitHub account with Copilot (sign in with the Copilot CLI or `gh`, or use a fine-grained token)

## Updates

The app updates itself from this repository. It checks shortly after it starts and every 6 hours; the update button in the title bar checks right away. A new version downloads in the background and is checked against its SHA-512 before it installs. Then click **Restart to update**, or it installs when you quit.

## Your data

The app keeps its data on your machine: settings and reviews in `%APPDATA%\AzTech`, repository checkouts in `%LOCALAPPDATA%\AzTech`. API keys and tokens are encrypted with Windows' DPAPI. A review sends the PR's code to Anthropic or GitHub, whichever agent you pick, and nowhere else.

To uninstall, open Windows **Settings → Apps → Installed apps → AzTech PRADOr**. Your data folders stay; delete them if you want a clean slate.

## License

[MIT](LICENSE)
