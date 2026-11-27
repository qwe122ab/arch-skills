# arch-skills

Claude Code skills for the Arch regulations database (Lithuanian building regulations in Supabase).

## Skills

| Skill | Command | What it does |
|---|---|---|
| search-regulations | `/regulations:search-regulations <question>` | Answers a question using **only** the regulations in Supabase, with exact citations. No web search, no general knowledge. |

## Install (Claude Code)

```
/plugin marketplace add qwe122ab/arch-skills
/plugin install regulations@arch-skills
```

Update later with `/plugin marketplace update arch-skills`.

## Requirements

- The **Supabase** connector (or Supabase MCP server) connected in Claude, with access to project
  `ruqbadvcdjjkidklrriv`. Read-only access is recommended.

## Claude chat (claude.ai)

Zip the `plugins/regulations/skills/search-regulations` folder and upload it in
Settings → Capabilities → Skills.
