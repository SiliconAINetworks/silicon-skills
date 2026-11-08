---
name: measure-dont-guess
description: Use before fixing any bug, layout glitch, failing request or "it stopped working" report. Forces the agent to collect real evidence (logs, payloads, measurements) and find the root cause before touching code. Never patch on assumptions.
---

# Measure, don't guess

A fix built on a guess is a second bug waiting to happen. Before you change a single line, you prove where the problem is.

## The rule

1. **Reproduce first.** Write down the exact steps, input and environment that trigger the problem. If you cannot reproduce it, you are not ready to fix it.
2. **Collect real data.** Read the actual log lines, the actual request and response payloads, the actual values in the database or the DOM. Not what the code *should* produce – what it *did* produce.
3. **Measure from the outside in.** Start at the boundary the user sees and walk inward: page → container → component, or request → router → handler → database. The first layer where reality differs from expectation is where the bug lives.
4. **State the root cause in one sentence** before writing the fix: "X happens because Y, proven by Z."
5. **Fix that cause, and only that cause.** Then verify with the same measurement that showed the problem.

## Red flags – stop and measure

- You are about to write "probably", "should be", "maybe it's" in your reasoning.
- You changed something, it didn't help, and you are about to change something else.
- Two attempts failed. A third guess is not a plan; go back to step 2.
- The fix touches code far away from where the symptom appears, and you have no evidence connecting them.

## Field notes (real cases)

- **The page looked shifted to the left.** Four guesses at individual elements were wrong. Measuring widths outside-in in the browser console (body → wrapper → main) found it in one step: a flex `body` without an explicit width shrank to its content. Fix: `width: 100vw` on body.
- **"No mail for two days."** The filter was blamed. Running the real filter against the real messages showed every harmless mail scored 0 – the filter was innocent. The cause was spam correctly filtered plus a client that had stopped fetching.
- **"Deleted, but it's still there."** Over IMAP, Gmail folders are labels. Flag + expunge on INBOX only removes the label; the message lives on in "All Mail". Found by checking the server state after the action, not by re-reading the code.

## Output

When you report a fix, include: the evidence you collected, the one-sentence root cause, the change, and the measurement that proves it is gone.
