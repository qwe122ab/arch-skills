# arch-skills

Claude Code skills for the Arch regulations (Lithuanian building regulations, served by the Arch MCP server).

## Skills

| Skill | Command | What it does |
|---|---|---|
| arch | `/arch <question>` (or `/regulations:arch`) | Answers a question using **only** the regulations in the Arch MCP server, with exact citations. No web search, no general knowledge. |
| arch-check | `/arch-check` with your document attached (or `/regulations:arch-check`) | Checks a whole document (design, explanatory note, specification …) against the stored regulations: every claim, plus required items the document leaves out. Reports ❌ / 🕳 / ⚠️ / ✅ / ➖ findings with exact citations. |

## Install (Claude Code)

```
/plugin marketplace add qwe122ab/arch-skills
/plugin install regulations@arch-skills
```

Update later with `/plugin marketplace update arch-skills`.

## Requirements

- The **Arch MCP server** connected in Claude, at `https://<host>/mcp/<Mcp:PathSecret>` (the Arch app's MCP
  endpoint). The skills use only its read-only tools: `list_regulations`, `search_regulations`,
  `search_requirements`, `read_regulation`, `follow_references`.
  - Claude Code: add it to `.mcp.json` as an `http` server named `arch`.
  - claude.ai: add it as a custom connector with the same URL.

## Claude chat (claude.ai)

Zip each skill folder (`plugins/regulations/skills/arch`, `plugins/regulations/skills/arch-check`) and upload it
in Settings → Capabilities → Skills.

## Checking a document

Attach the document (.docx, PDF or pasted text) in the chat and type `/arch-check`. The document stays in the chat; it
is not uploaded to the Arch app or the database. Claude:

1. lists the loaded regulations and works out the document's scope (building purpose, category, type of works, date);
2. lists every checkable claim in the document and compares it with the regulations (numeric limits are compared
   value by value);
3. lists the mandatory requirements of the applicable regulations (in force today; only those are loaded) and
   reports the ones the document leaves out;
4. reports findings with the exact clause and quote, plus assumptions, regulations referred to but not loaded, and
   what was not checked.
