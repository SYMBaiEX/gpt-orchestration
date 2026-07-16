# GPT Engineer

[![skills.sh](https://skills.sh/b/SYMBaiEX/gpt-orchestration)](https://skills.sh/SYMBaiEX/gpt-orchestration)

An open [Agent Skills](https://agentskills.io/) family for running a real delegated engineer: research
the codebase, route bounded work across provider-specific models, implement confirmed findings,
integrate the result, verify it independently, and persist through goal-closing cycles.

## Skills

- [`gpt-engineer`](skills/gpt-engineer/) — primary end-to-end engineer with model-routed Codex agents,
  optional safety hooks, research, implementation, integration, verification, and goal persistence.
- [`gpt-orchestration`](skills/gpt-orchestration/) — research, build every confirmed finding, integrate, and verify.
- [`gpt-orchestration-build`](skills/gpt-orchestration-build/) — consume an existing audit or finding list and carry every item to a disposition.
- [`gpt-orchestration-auto`](skills/gpt-orchestration-auto/) — run a persistent `/goal`-style research → build → verify → gap-scan loop.

## Install

```bash
npx skills add https://github.com/SYMBaiEX/gpt-orchestration \
  --skill gpt-engineer --agent codex claude-code --global --yes
```

The repository follows the open [Agent Skills specification](https://agentskills.io/specification)
and uses the `skills/<name>/SKILL.md` layout discovered by the
[skills CLI](https://www.skills.sh/docs/cli). Codex-specific presentation metadata lives beside
each skill in `agents/openai.yaml`.

## Use

Invoke the skill when a task benefits from multiple bounded specialists:

```text
Use $gpt-engineer to own this engineering outcome from research through verified implementation.

Use $gpt-orchestration to research this repository, implement every confirmed finding,
and independently verify the integrated result.

Use $gpt-orchestration-build to implement every finding in this audit and prove each disposition.

Use $gpt-orchestration-auto to pursue this engineering goal autonomously until it is verified complete.
```

skills.sh installs the workflow. Register the bundled user-level Codex and Claude model profiles once:

```bash
python3 ~/.agents/skills/gpt-engineer/scripts/bootstrap.py --global
python3 ~/.agents/skills/gpt-engineer/scripts/bootstrap.py --check --global
```

Restart Codex and Claude Code after registration. For repo-scoped profiles and conservative Codex hooks,
replace `--global` with `/path/to/repository`. The bootstrap refuses conflicts and does not edit provider
configuration. When a Codex surface cannot select a custom model natively, the skill includes a guarded
`codex exec` fallback that pins the requested model and fails closed on repository-scope violations.

## License

MIT
