# GPT Engineer

[![skills.sh](https://skills.sh/b/SYMBaiEX/gpt-orchestration)](https://skills.sh/SYMBaiEX/gpt-orchestration)

An open [Agent Skills](https://agentskills.io/) family for running a real GPT engineer: research the
codebase, route work across GPT-5.6 Sol, Terra, and Luna, implement confirmed findings, integrate the
result, verify it independently, and persist through goal-closing cycles.

## Skills

- [`gpt-engineer`](skills/gpt-engineer/) — primary end-to-end engineer with model-routed Codex agents,
  optional safety hooks, research, implementation, integration, verification, and goal persistence.
- [`gpt-orchestration`](skills/gpt-orchestration/) — research, build every confirmed finding, integrate, and verify.
- [`gpt-orchestration-build`](skills/gpt-orchestration-build/) — consume an existing audit or finding list and carry every item to a disposition.
- [`gpt-orchestration-auto`](skills/gpt-orchestration-auto/) — run a persistent `/goal`-style research → build → verify → gap-scan loop.

## Install

```bash
npx skills add SYMBaiEX/gpt-orchestration --skill gpt-engineer -g -y
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
Use $gpt-engineer to own this engineering outcome from research through verified implementation.

Use $gpt-orchestration to research this repository, implement every confirmed finding,
and independently verify the integrated result.

Use $gpt-orchestration-build to implement every finding in this audit and prove each disposition.

Use $gpt-orchestration-auto to pursue this engineering goal autonomously until it is verified complete.
```

`gpt-engineer` includes optional project-local Codex profiles for `gpt-5.6` (Sol),
`gpt-5.6-terra`, and `gpt-5.6-luna`. After installing the skill, configure a repository only when
you intend to add `.codex/agents` and hooks:

```bash
python3 /path/to/gpt-engineer/scripts/bootstrap_codex.py /path/to/repository
python3 /path/to/gpt-engineer/scripts/bootstrap_codex.py --check /path/to/repository
```

The bootstrap merges hooks without overwriting conflicts. On other runtimes, the skills detect
whether model routing exists and degrade to behavioral profiles without making false model claims.

## License

MIT
