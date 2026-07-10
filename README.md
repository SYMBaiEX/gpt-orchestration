# GPT Orchestration

[![skills.sh](https://skills.sh/b/SYMBaiEX/gpt-orchestration)](https://skills.sh/SYMBaiEX/gpt-orchestration)

An open [Agent Skill](https://agentskills.io/) for coordinating native coding-agent fleets safely.
It gives one orchestrator a repeatable workflow for repository-wide audits, parallel implementation,
dirty-worktree preservation, bounded file ownership, independent verification, and honest model routing.

## Install

```bash
npx skills add SYMBaiEX/gpt-orchestration -g -y
```

Or select the target agent explicitly:

```bash
npx skills add SYMBaiEX/gpt-orchestration --skill gpt-orchestration --agent codex -g -y
```

The repository follows the open [Agent Skills specification](https://agentskills.io/specification)
and is discoverable by the [skills CLI](https://www.skills.sh/docs/cli). The skill itself is in
[`SKILL.md`](SKILL.md); Codex-specific presentation metadata lives in [`agents/openai.yaml`](agents/openai.yaml).

## Use

Invoke the skill when a task benefits from multiple bounded specialists:

```text
Use $gpt-orchestration to audit this repository with parallel agents, implement confirmed fixes,
and independently verify the integrated result.
```

The skill treats Terra and Luna as behavioral profiles unless the active runtime exposes and confirms
real per-agent model selection. It never claims model routing that the runtime cannot prove.

## License

MIT
