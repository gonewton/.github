# Newton

**Orchestrate AI agents to ship reliable software.**

Newton turns AI coding agents from unpredictable assistants into dependable contributors. Instead of one-shot prompts and hoping for the best, Newton runs them inside deterministic workflows with explicit goals, checkpoints, approvals, and verifiable completion.

## Why Newton

AI agents are powerful, but raw agent runs are hard to trust in real engineering work:

- Output drifts from the requested goal.
- There is no clear definition of "done".
- Failures are opaque and not resumable.
- Humans lose oversight of what the agent actually changed.

Newton solves this by treating agent work as a **workflow graph**: every step has inputs, outputs, success conditions, and recovery semantics. Agents become operators in that graph, side-by-side with shell commands, GitHub actions, and human approvals.

## What Newton Gives You

- **Deterministic workflows** authored in YAML, with linting, dry-run preview, and a visual graph.
- **Agent operators** for the major coding agents (Claude, Codex, Gemini, OpenCode, generic SDK agents) with uniform quota and error handling.
- **Goal gates and terminal tasks** that decide when a run is actually complete, not just "finished".
- **Checkpoints and resume** so long agent runs survive crashes, restarts, and human breaks.
- **Human-in-the-loop** approvals and multiple-choice decisions wired directly into the graph.
- **GitHub integration** for PR creation, review, and project board updates as first-class steps.
- **Artifacts and logs** captured per task, ready for audit, replay, or downstream tooling.
- **Sub-workflows** to compose large pipelines from small, reusable graphs.

## Use Cases

- **Agent-driven feature delivery.** Plan, implement, test, open a PR, and chase reviews, with humans gating the risky parts.
- **Batch coding tasks.** Queue many specs and have Newton drive an agent through each one with consistent setup, branching, and post-run hooks.
- **Release and operations runbooks.** Encode deploys, migrations, and incident playbooks as graphs instead of brittle scripts.
- **Evaluator / advisor loops.** Iterate on a solution with measurable scoring until a goal is met, instead of fixed-iteration prompting.
- **Multi-agent pipelines.** Combine specialized agents (planner, implementer, reviewer) under one orchestrator.

## How It Works

1. **Describe the work** in a workflow YAML: tasks, operators, dependencies, and completion rules.
2. **Run it** with `newton run`. Newton schedules tasks, invokes agents and tools, captures artifacts, and checkpoints progress.
3. **Stay in control.** Use `newton monitor` for a live terminal UI, answer approval prompts, inspect artifacts, and resume from any checkpoint.
4. **Verify completion.** Goal gates and terminal tasks decide success; failures get stable error codes you can act on.

## Install

macOS / Linux:

```bash
brew tap gonewton/cli
brew install newton
```

Windows:

```powershell
scoop bucket add gonewton https://github.com/gonewton/scoop-bucket
scoop install newton
```

Then bootstrap a workspace:

```bash
newton init .
newton run
```

## Learn More

- CLI reference and operator docs: [`gonewton/newton`](https://github.com/gonewton/newton)
- Workflow templates: [`gonewton/newton-templates`](https://github.com/gonewton/newton-templates)
- Homebrew tap: [`gonewton/homebrew-cli`](https://github.com/gonewton/homebrew-cli)
- Scoop bucket: [`gonewton/scoop-bucket`](https://github.com/gonewton/scoop-bucket)

## License

Newton is released under the **Apache License 2.0**. See each repository’s `LICENSE` file for the full text.

Contributions, issues, and workflow recipes are welcome.
