---
name: encoding-safe-edits
description: Use when editing files that contain non-ASCII text (umlauts, accents, emoji, translations), JSON, or files with mixed line endings - especially on Windows. Prevents silent UTF-8 corruption, stray BOMs and whole-file line-ending rewrites.
---

# Encoding-safe edits

Broken encoding is the worst kind of bug: the file still "works", the diff looks huge, and somewhere in sixteen languages an umlaut turned into garbage.

## Before editing

- **Check the encoding and line endings** of the file: UTF-8 with or without BOM? LF or CRLF? Keep exactly what you find.
- **Know your tool.** Some editing tools and shells re-encode files on save (e.g. Windows PowerShell 5 writes UTF-16 or a BOM by default; some string-replace tools mangle multi-byte characters in large JS/JSON files).

## Safe way to edit sensitive files

For translations, JSON and large JS files, edit through a small script that controls the encoding explicitly:

```python
from pathlib import Path

p = Path("js/lang/de.js")
s = p.read_text(encoding="utf-8")
old, new = "'title': 'Alt'", "'title': 'Neu'"
assert s.count(old) == 1, "pattern must match exactly once"
p.write_text(s.replace(old, new), encoding="utf-8", newline="")
```

- `newline=""` keeps the existing line endings untouched.
- The `assert` makes the edit fail loudly instead of silently replacing the wrong spot or nothing.
- Delete the throwaway script afterwards; it does not belong in the project.

## After editing

- Run a syntax check (`node --check`, `python -m json.tool`, `py_compile`).
- Look at `git diff --stat`: a one-line change must show as a few lines, not the whole file.
- Grep the file for replacement characters (`�`) or mojibake (`Ã¤`, `Ã¶`).

## Never

- Rewrite a whole translation file to change one string.
- Convert line endings as a side effect of a feature change.
- Write commit messages or config files with a BOM unless the format requires it.
