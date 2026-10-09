# Re-review after a push

You reviewed a PR, the author pushed fixes, and you want to know if they're right without going through everything again.

1. Open the PR. The review's summary says how many **new iterations** were pushed since the review (on GitHub, each new commit counts as one).
2. Click **Review new changes**.
   The agent reviews only what changed since its review. Your decisions carry over: kept stays kept, dismissed stays dismissed. Findings the push fixed are marked **resolved**, and new ones are added.
3. Go through the new findings and post as usual.

**Full re-review** instead starts again from scratch, as if there had been no review.

## When the history was rewritten

If the author rebased or force-pushed, the summary says the PR's commits changed. **Review new changes** still reviews what changed in the code. If the commit the review read is gone, it does a full review instead.

## On your own PR

After pushing fixes from [fix mode](../fix-mode.md), **Re-review the changes** in the fix window does the same, by the agent that reviewed the PR. It uses the fix session's model and effort when that's the agent that fixed it.

## Not automatic

[Automatic reviews](../notifications.md#automatic-reviews) review new PRs as they arrive, not later pushes. After a push, start the re-review yourself.
