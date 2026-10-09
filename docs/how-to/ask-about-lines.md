# Ask about some lines of the diff

"What does this regex match?" "Is this lock needed?" "Why would this be null?" Ask an agent about the code right where you're reading it.

1. In the diff, select the lines. For one line, just put the cursor on it.
2. Right-click → **Ask AI about these lines**. A box opens under the lines.
   Already writing a comment there? Its **Ask** button (**Ask Claude**, say) sends your text as a question instead.
3. Pick the agent in the box. It starts with the agent of the review you have open.
4. Write your question and ask. It goes with the file, the line numbers and the code.

The answer shows on that agent's **Ask** tab.

- An agent that reviewed the PR answers in its review session: it remembers what it read.
- An agent marked **new** starts a questions session: it reads the PR's checkout to answer, read-only. Later questions continue it.

Answers come from the PR's current code, even if it changed since the review.

See [Asking the agent](../ask.md) for questions about findings, threads and the whole PR.
