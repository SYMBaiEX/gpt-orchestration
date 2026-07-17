# GPT Engineer

[![skills.sh](https://skills.sh/b/SYMBaiEX/gpt-orchestration)](https://skills.sh/SYMBaiEX/gpt-orchestration)

An open [Agent Skills](https://agentskills.io/) family for running a real delegated engineer: research
the codebase, route bounded work across provider-specific models, implement confirmed findings,
integrate the result, verify it independently, and persist through goal-closing cycles.

## Skills

- [`gpt-engineer`](skills/gpt-engineer/) — primary end-to-end engineer with model-routed Codex agents,
  optional safety hooks, research, implementation, integration, verification, and goal persistence.
- [`gpt-engineer-spark`](skills/gpt-engineer-spark/) — keep a capable lead in control while a
  model-pinned GPT-5.3-Codex-Spark fleet handles dependency-aware exploration, isolated candidate
  edits, and checks.
- [`gpt-orchestration`](skills/gpt-orchestration/) — research, build every confirmed finding, integrate, and verify.
- [`gpt-orchestration-build`](skills/gpt-orchestration-build/) — consume an existing audit or finding list and carry every item to a disposition.
- [`gpt-orchestration-auto`](skills/gpt-orchestration-auto/) — run a persistent `/goal`-style research → build → verify → gap-scan loop.

## Install

```bash
npx skills add https://github.com/SYMBaiEX/gpt-orchestration \
  --skill gpt-engineer --agent codex claude-code --global --yes

npx skills add https://github.com/SYMBaiEX/gpt-orchestration \
  --skill gpt-engineer-spark --agent codex --global --yes
```

The repository follows the open [Agent Skills specification](https://agentskills.io/specification)
and uses the `skills/<name>/SKILL.md` layout discovered by the
[skills CLI](https://www.skills.sh/docs/cli). Codex-specific presentation metadata lives beside
each skill in `agents/openai.yaml`.

## Use

Invoke the skill when a task benefits from multiple bounded specialists:

```text
Use $gpt-engineer to own this engineering outcome from research through verified implementation.

Use $gpt-engineer-spark to lead this build with a fleet of fast, model-pinned Spark agents.

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

For Spark, register its Codex-only profiles separately:

```bash
python3 ~/.agents/skills/gpt-engineer-spark/scripts/bootstrap.py --global
python3 ~/.agents/skills/gpt-engineer-spark/scripts/bootstrap.py --check --global
```

Spark CLI fallback writers operate on isolated candidate copies and return reviewable change bundles;
the capable main agent integrates them and owns the final repository checks.

## Dynamic workflows

GPT Engineer now selects the orchestration surface from the work: native Codex subagents for a few
shards, exact model-pinned runners when routing must be proven, dependency-derived Spark waves for
fast bounded work, and Claude Code saved workflows for repeatable high-fanout audits or migrations.
Cross-provider transitions remain with the capable outer lead; Claude workflows cannot select GPT
models. Writer delegates return candidate bundles and never silently mutate the source checkout.

Install the companion `claude-multi-agent` skill from `SYMBaiEX/skills` to add the saved
`gpt-engineer-dynamic` JavaScript workflow and its headless runner.

## License

MIT
