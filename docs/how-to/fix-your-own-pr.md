# Fix your own PR

A reviewer (or an agent) found things in your PR. Let an agent fix them in your clone, check its work, and push.

You need a clone of the repository on your machine, on the PR's branch, up to date, ideally with nothing uncommitted.

1. **Review it**, if it hasn't been: open the PR and **Start review**. Fix mode works without a review too, from the comments or whatever you ask.
2. Click **Fix…** in the PR's header. It's there on PRs you created.
3. **Link your checkout…**: pick your clone's folder. The app checks it's on the PR's branch, with its latest commit. You only link it once per repository.
4. Pick the agent, model and effort, and **Ask me** (commands wait for your OK). **Start fixing**.
5. Say what to fix: "Fix the findings from the Claude review", or "Do what Tom asked in the comments on config.ts".
6. Watch it work. When it wants to run a command (say, the tests), **Allow** or **Deny** it. Edits to files go ahead.
7. Open **Changes** and read the diff. Not right? Tell it what to change, in the same session.
8. **Commit…**: pick the files and check the message.
9. **Push…**: check the commits and files listed, and confirm.
10. **Re-review the changes** checks whether the findings are fixed.

The agent can't commit, push or switch branches: those are your buttons. See [Fix mode](../fix-mode.md) for everything it can and can't do.
