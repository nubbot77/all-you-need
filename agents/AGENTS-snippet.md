# all-you-need — generic agent snippet

For any agent that reads an instructions file (AGENTS.md, .cursor/rules, .windsurfrules, GEMINI.md, CONVENTIONS.md, etc.): paste the block below into that file, after cloning the repo:

```
git clone https://github.com/nubbot77/all-you-need ~/.all-you-need
```

---

## Spec-First Workflow (all-you-need)

When the user says "start workflow", "all you need", or begins a new project:

1. Read `~/.all-you-need/plugins/all-you-need/skills/all-you-need/SKILL.md` and follow it exactly.
2. Resolve `stages/...` and `templates/...` references relative to that SKILL.md's directory.
3. Where it says "AskUserQuestion", ask the user directly in chat and wait for the answer.
4. Where it mentions the `grill-with-docs` skill, use the fallback interview in `stages/01-prd.md`.
5. Only load the reference file for the CURRENT stage — never all stages at once.
