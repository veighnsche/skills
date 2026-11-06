# Skills

Reusable agent skills maintained by [veighnsche](https://github.com/veighnsche).

## Available skills

| Skill | When it applies |
| --- | --- |
| [overengineering-interrupt](skills/overengineering-interrupt/SKILL.md) | Implementation is underway and an agent is about to add optional work beyond the request and observed evidence. It excludes task startup, ordinary implementation choices, and required checks. |

## Install in Codex

Ask Codex:

```text
$skill-installer install https://github.com/veighnsche/skills/tree/main/skills/overengineering-interrupt
```

Private repository access requires GitHub authentication on the installing machine. The installer refuses to overwrite an existing skill; when updating, ask Codex to compare the installed copy with this repository and apply the intended changes.

## Repository layout

```text
plugin.json
skills/
  overengineering-interrupt/
    SKILL.md
```

Each skill lives in `skills/<skill-name>/SKILL.md`, with YAML `name` and `description` fields followed by its instructions. Add scripts, references, or assets only when the workflow needs them. The root manifest also packages the collection as a portable skills-only plugin.

Edit the version in this repository first, then distribute it to the machines that need it. Existing installations are independent copies and do not update automatically.

## Format references

- [Agent Skills specification](https://agentskills.io/specification)
- [Build skills for ChatGPT and Codex](https://learn.chatgpt.com/docs/build-skills)
- [Package a plugin](https://developers.openai.com/plugins/build/plugins)
