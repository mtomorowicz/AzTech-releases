# Troubleshooting

## Signing in

**"Azure CLI is not signed in"**
Run `az login` in a terminal, then retry. If your organization is in another tenant than your default one, the message shows the command with the tenant (`az login --tenant …`). You can also set the tenant in Settings → Azure DevOps.

**"GitHub CLI is not signed in"**
Run `gh auth login` in a terminal (for GitHub Enterprise, with `--hostname` and your host), then retry.

**The PR list is empty**
- Check the project in the title bar, and the **Needs me** / **All active** tab.
- Check the filters: when they hide every PR, the list says how many and offers **Clear filters**.
- On GitHub, check the organization in the title bar.

## Agents

**"…no key is stored. Add one in Settings."**
In Settings → Claude, choose **API key**, paste your Anthropic key and click **Save key**, then **Save changes**.

**Copilot: the check fails, or a model is missing**
**Check Copilot** in Settings says why. With **GitHub sign-in**, sign in with the Copilot CLI or `gh auth login`. With a **GitHub token**, it needs to be a fine-grained token with the Copilot Requests permission, saved with **Save token**. The models listed are the ones your Copilot plan offers.

**OpenCode: no models**
Connect a provider in OpenCode first: `opencode auth login`, then **Check OpenCode** in Settings.

**The first review is slow**
Each agent's runtime is downloaded once (about 40–110 MB): Claude's with its first review, Copilot's and OpenCode's when you check them in Settings or open their tab. The first review of a repository clones it. Both are kept for next time.

**A review failed**
The review says why, with **Try again**. Its **Activity** tab shows what the agent did up to then. If it stopped at your **budget cap**, raise the cap in Settings.

**A question cost more than the last one**
The agent's session wasn't cached any more, so it was read again in full. See [What a question costs](ask.md#what-a-question-costs).

## Notifications

**No Windows notifications**
- Check Settings → Notifications: each kind has its own switch.
- **Send test notification** there. If it doesn't show, check Windows Settings → System → Notifications (is AzTech PRador allowed?) and Do not disturb.
- The app needs to be running: in the tray counts. Turn on **Keep AzTech PRador running in the system tray when the window is closed**, near the bottom of Settings.

If the background checks are failing, Settings → Notifications says so, with **Open log**.

## Fix mode

**Fix… isn't there**
It's only on PRs you created.

**"The folder is on …: check out … first", "The branch is behind the PR: pull first" or "The folder doesn't have the PR's latest commit"**
Switch your clone to the PR's branch and pull, in your usual git tool, then press <kbd>F5</kbd> in the fix window to check again.

**"The branch and the PR have gone different ways (a force-push?)"**
Your branch and the PR's have different commits. Sort it out in git (say, reset your branch to the PR's, keeping a copy of any work of yours), then press <kbd>F5</kbd>.

**"This folder is a clone of …, not of …"**
Link the clone of the PR's repository: **Change…** next to the folder.

**"This folder has an .opencode folder"**
OpenCode would run the plugins in that folder outside fix mode's checks, so it can't fix there. Fix with Claude or Copilot instead.

## Disk space

The clones and PR checkouts are kept for the next review. **Local repo cache**, near the bottom of Settings, shows how much space they take: **Clean up now** removes the ones no longer needed, and **Clear everything** removes them all (they come back on the next review).

## Still stuck

Settings → Notifications → **Open log** opens the folder with the app's log. It helps to say what you were doing and when.
