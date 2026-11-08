# Silicon Skills

**Agent skills for people who ship. Graduated from the Donkey School.** 🎓

Nine working rules for Claude Code, Codex, Cursor and every other coding agent – forged in months of daily work between one developer and his AI on real products: a code-only art museum, an AI workbench, an email security app and a trading platform.

No theory, no vibe coding. Every rule exists because ignoring it once cost real hours.

---

## The complete kit: Skills + MCP

| | What it gives your agent | Install |
|---|---|---|
| **Silicon Skills** | *How* to work: measure before fixing, check the whole chain, deploy safely | `npx skills add SiliconAINetworks/silicon-skills` |
| **[Silicon Transfer MCP](https://github.com/SiliconAINetworks/mcp-server-ftp)** | The *tools* to deploy: FTP/FTPS/SFTP, checksum compare, backup, smart sync | see its README |

The skills work on their own. Together with the MCP, `safe-deploy` has its backup, checksum and sync steps built right in.

---

## The skills

| Skill | Teaches the agent to … |
|---|---|
| [`measure-dont-guess`](skills/measure-dont-guess/SKILL.md) | collect real evidence and find the root cause before touching code |
| [`bridge-check`](skills/bridge-check/SKILL.md) | trace trigger → transport → storage → reader → effect before saying "done" |
| [`meeting-first`](skills/meeting-first/SKILL.md) | separate talking from building: honest opinion, plan, wait for the go – then execute without nagging |
| [`git-discipline`](skills/git-discipline/SKILL.md) | commit every step, never push or roll back without permission, avoid BOM and line-ending traps |
| [`clean-separation`](skills/clean-separation/SKILL.md) | keep HTML, CSS and JS apart, bust caches, delete old code when adding new |
| [`honest-ui`](skills/honest-ui/SKILL.md) | ship no fake features, no invented numbers, no silent failures |
| [`safe-deploy`](skills/safe-deploy/SKILL.md) | deploy local-first: pull server state, stage, verify checksums, hand over sudo one command per block |
| [`read-before-claim`](skills/read-before-claim/SKILL.md) | read files and handover notes after every compaction instead of trusting memory |
| [`encoding-safe-edits`](skills/encoding-safe-edits/SKILL.md) | edit UTF-8, JSON and translation files without corrupting them |

## Install

**Any agent (skills.sh):**

```bash
npx skills add SiliconAINetworks/silicon-skills
```

Pick the skills you want – they are independent.

**Claude Code plugin marketplace:**

```
/plugin marketplace add SiliconAINetworks/silicon-skills
/plugin install silicon-skills@silicon-skills
```

**Manual:** copy any folder from `skills/` into `~/.claude/skills/` (or your agent's skills directory).

---

## Deutsch

**Agent-Skills für Leute, die liefern. Abschluss an der Esels-Schule.**

Neun Arbeitsregeln für Claude Code, Codex, Cursor und jeden anderen Coding-Agenten – entstanden in Monaten täglicher Zusammenarbeit zwischen einem Entwickler und seiner KI an echten Produkten. Jede Regel gibt es, weil ihr Fehlen einmal echte Stunden gekostet hat.

Die Skills sind auf Englisch, damit jeder Agent sie versteht. Sie funktionieren einzeln und ohne weitere Werkzeuge; zusammen mit dem [Silicon Transfer MCP](https://github.com/SiliconAINetworks/mcp-server-ftp) bekommt `safe-deploy` Backup, Prüfsummen-Vergleich und Smart-Sync direkt als Werkzeuge.

---

## Built by

**Silicon Networks** – Switzerland. The rules in this repo were forged while building:

- **[HALLE 42](https://siliconnetworks.ch/museum-42/entry.html)** – an art museum made entirely of live code. No images, no videos.
- **[AEONIX](https://aeonix888.com)** – an AI workbench where whole AI teams work together.
- **[AEGIS Shield](https://aegis888.com)** – email security with multi-AI analysis, Swiss made.
- **[siliconnetworks.ch](https://siliconnetworks.ch)** – web design you don't forget.

If these skills save you time, have a look at what we build.

## License

MIT – © 2026 Silicon Networks
