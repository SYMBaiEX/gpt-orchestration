# GPT Orchestration

[![skills.sh](https://skills.sh/b/SYMBaiEX/gpt-orchestration)](https://skills.sh/SYMBaiEX/gpt-orchestration)

An open [Agent Skills](https://agentskills.io/) family for coordinating native coding-agent fleets
safely. It gives one orchestrator repeatable workflows for research, implementation from findings,
autonomous goal completion, dirty-worktree preservation, bounded ownership, and independent verification.

## Skills

- [`gpt-orchestration`](skills/gpt-orchestration/) — research, build every confirmed finding, integrate, and verify.
- [`gpt-orchestration-build`](skills/gpt-orchestration-build/) — consume an existing audit or finding list and carry every item to a disposition.
- [`gpt-orchestration-auto`](skills/gpt-orchestration-auto/) — run a persistent `/goal`-style research → build → verify → gap-scan loop.

## Install

```bash
npx skills add SYMBaiEX/gpt-orchestration --skill gpt-orchestration -g -y
npx skills add SYMBaiEX/gpt-orchestration --skill gpt-orchestration-build -g -y
npx skills add SYMBaiEX/gpt-orchestration --skill gpt-orchestration-auto -g -y
```

Or select the target agent explicitly:

```bash
npx skills add SYMBaiEX/gpt-orchestration --skill gpt-orchestration --agent codex -g -y
```

The repository follows the open [Agent Skills specification](https://agentskills.io/specification)
and uses the `skills/<name>/SKILL.md` layout discovered by the
[skills CLI](https://www.skills.sh/docs/cli). Codex-specific presentation metadata lives beside
each skill in `agents/openai.yaml`.

## Use

Invoke the skill when a task benefits from multiple bounded specialists:

```text
Use $gpt-orchestration to research this repository, implement every confirmed finding,
and independently verify the integrated result.

Use $gpt-orchestration-build to implement every finding in this audit and prove each disposition.

Use $gpt-orchestration-auto to pursue this engineering goal autonomously until it is verified complete.
```

The skill treats Terra and Luna as behavioral profiles unless the active runtime exposes and confirms
real per-agent model selection. It never claims model routing that the runtime cannot prove.

## License

MIT
