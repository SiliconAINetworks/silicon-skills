---
name: git-discipline
description: Use whenever the agent works in a git repository. Commit after every logical step, never push or rewrite history without explicit permission, and avoid the traps that silently corrupt commits (BOM in messages, line-ending churn, binary folders).
---

# Git discipline

Git is the user's safety net. An agent's job is to make the net stronger, never to cut holes in it.

## Always

- **Commit after every logical step**, without asking. Small commits are cheap; a lost afternoon is not.
- **Write messages that say what and why**, in the language of the project.
- **Stage files explicitly** (`git add path/to/file`), never blindly add whole directories.
- **Check `git status` before and after** so you know exactly what went in.

## Never without explicit permission

- `git push` to any remote.
- `git reset --hard`, `git revert`, `git checkout -- .`, `git clean`, rebase, amend on shared history – anything that rolls back or rewrites.
- Deleting branches or tags.

If something went wrong, stop and report it. Do not "fix" it by rolling back on your own.

## Traps that cost real time

- **BOM in commit messages.** Some shells (e.g. Windows PowerShell `Set-Content -Encoding UTF8`) write a byte-order mark. It ends up as an invisible character at the start of the commit message. Write the message file as UTF-8 *without* BOM, then `git commit -F message.txt`.
- **Quotes and parentheses in `-m`.** Shell quoting breaks messages. Use `-F` with a file.
- **Line endings.** If the repo freezes line endings (`* -text` in `.gitattributes`), check whether a file is LF or CRLF before editing and keep it that way. Converting a whole file turns a 3-line fix into a 6000-line diff that hides the real change.
- **Generated or binary folders.** Rendered frames, builds, caches, dumps: put them in `.gitignore` first. One careless `git add` keeps megabytes in history forever.
- **Secrets.** `.env`, keys, database dumps and config files with credentials never get committed. Scan before the first push of a new repo.

## Output

After committing, report the short hash and the one-line summary so the user can find the step later.
