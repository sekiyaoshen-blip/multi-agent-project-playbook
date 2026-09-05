# Codex Native Capability Notes

Reviewed 2026-09-05. Maintainer context only, not runtime startup instructions.
Feature availability varies by client, account, rollout, and callable tools.

## What Changed

The official [changelog](https://learn.chatgpt.com/docs/changelog) documents:

- March: worktree handoff, fork/navigation improvements, and task-history search.
- May: goal mode availability, native local/worktree task coordination, and
  broader conversation/branch search.
- June: local/remote task handoff, app `/init`, browser developer tools, and
  improved task recovery.
- July: Codex in the ChatGPT desktop app, clearer task/subagent activity, and
  multi-folder projects. Git/instruction discovery uses the primary folder.
- August: further history, reconnect, and context-compaction improvements.

These changes justify preferring native task search, result inspection, waits,
and handoff over duplicate status files, manual context packets, and polling.
This is an engineering simplification, not a claim that all delivery and
concurrency failures are solved. Memory/history helps recovery; it does not
replace current code, ownership, or project decisions.

## Prompting Implications

The [GPT-6 Astra guidance](https://developers.openai.com/api/docs/guides/latest-model?model=gpt-6-astra)
notes sensitivity to skills/instructions, early stopping, under-delegation in
some settings, and excessive testing. Our response is shorter instructions,
clear outcomes, useful independent delegation, and a concrete stopping rule.
This does not select a model or add per-model behavior branches.

API asynchronous-tool and mid-turn steering features require harness support;
they are not evidence that a desktop task has those exact API capabilities.

## Global And Project Instructions

Use the supported [AGENTS.md layers](https://learn.chatgpt.com/docs/agent-configuration/agents-md):
global preferences in `$CODEX_HOME/AGENTS.md` (normally `~/.codex/AGENTS.md`),
project collaboration in the project's `AGENTS.md`, detailed references on demand.
Native subagents have their own
[configuration and lifecycle](https://learn.chatgpt.com/docs/agent-configuration/subagents);
they are not interchangeable with long-lived user-visible module tasks.

Do not duplicate the same long preference block across global instructions,
the skill, and every project. Installing this skill does not authorize changing
personal settings or removing existing project-specific release requirements.
