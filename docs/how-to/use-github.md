# Review GitHub pull requests

1. Install the [GitHub CLI](https://cli.github.com/) and sign in: `gh auth login`.
   For GitHub Enterprise, sign in to your host (`gh auth login --hostname <host>`) and set the host in Settings → GitHub.
2. In the title bar, switch from Azure DevOps to **GitHub**.
3. Pick an organization, or your own account. The menu next to the switch changes it later.

Everything else works as on Azure DevOps: the list, filters, reviews, questions, comments and fix mode. A few things follow GitHub's ways:

- **Needs me** is PRs asking for your review, plus the ones you've reviewed.
- **Votes** are GitHub reviews: **Approve**, or **Request changes**. GitHub needs a comment with a request for changes, so the app adds one ("Requesting changes: see my comments on the diff."), and the confirmation shows it. GitHub doesn't let you review your own PR, so you can't vote on it.
- **Builds** are GitHub's checks, with the required ones marked. Click one for its first failures.
- **Posting a review's findings** creates one GitHub review with a comment on each line.
- **Threads** are resolved or unresolved.

The title bar remembers where you were on each, so you can switch back and forth.

To review GitHub PRs with Copilot, see [Set up an agent](../getting-started.md#set-up-an-agent): Copilot works on Azure DevOps PRs too.
