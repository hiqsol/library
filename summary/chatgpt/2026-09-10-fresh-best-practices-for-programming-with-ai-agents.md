---
title: Fresh Best Practices for Programming with AI Agents --- 2026
author: chatgpt
channel: AI
url: https://github.com/sol/prj/hiqsol/library/blob/main/ai_coding_agents_best_practices_2026_en.md
---

# Fresh Best Practices for Programming with AI Agents --- 2026

[article](../../articles/chatgpt/2026-09-10-fresh-best-practices-for-programming-with-ai-agents.md)

As of September 2026, effective coding-agent workflows have moved beyond prompt engineering. The main unit of optimization is now the **agent harness**: environment, context, tools, rules, feedback loops, and verification.

> **The key question in 2026 is: what environment lets an agent find the right context, do the work, observe its own mistakes, and prove that the result is correct?**

## 1. Define Tasks as Engineering Contracts

A weak request is simply `Implement automatic SSL renewal.` A better task resembles a GitHub issue with clear goal, constraints, and acceptance criteria. The key elements are goal, constraints, acceptance criteria, invariants, and verification — not a long "magic prompt."

## 2. For Complex Changes: Plan → Execute

Before implementing, explore the codebase, identify relevant components, produce an implementation plan, and only then modify code. Avoid over-planning — strong models benefit from architectural intent, invariants, and success criteria more than instructions for every class and method. A useful plan describes: what changes → affected components → preserved invariants → verification.

## 3. Keep `AGENTS.md`, `CLAUDE.md`, and Repository Rules Short

Persistent instructions are useful but should not become a project encyclopedia. Include information the agent cannot reliably infer, needs across many tasks, or repeatedly gets wrong. A strong rule: "Do not predict every possible agent mistake. Turn actual recurring mistakes into repository rules."

## 4. Prefer Retrieval Over Context Dumping

Avoid manually stuffing dozens of files into the context window. Give the agent repository navigation, grep, semantic search, and similar retrieval tools. Let the agent discover the rest — excessive context can degrade reasoning by adding irrelevant or competing signals.

## 5. Reset Contaminated Context

Do not keep one conversation alive indefinitely. Start fresh when a logical unit is complete, the task changes, the agent repeats mistakes, an early bad assumption contaminates later work, or too much irrelevant history has accumulated. Use structured handoffs with STATUS, Current failure, and Next sections.

## 6. The Verification Loop Matters More Than the First Patch

A strong workflow is: inspect → edit → build/run → inspect failure → edit → test → repeat. The agent needs an executable development environment with ruff, mypy/pyright, unit and integration tests, Docker Compose, application logs, database inspection, API calls, and benchmarks. The ability to observe the consequences of its own changes turns a code generator into a useful coding agent.

## 7. Use Tests as an External Oracle

Externally defined acceptance tests describe the required behavior and must be made to pass without weakening them. This is stronger than "implement the feature and write tests" because the implementation agent does not control both the code and the definition of success. This is particularly useful for security, concurrency, billing, permissions, database migrations, deployments, certificates, and DNS management.

## 8. Use Multiple Agents Only for Truly Parallel Work

Multi-agent systems are practical but not automatically better. Good parallel tasks include implementation, test creation, security review, performance investigation, documentation, and independent debugging hypotheses. A poor pattern is sending several agents after the same root cause. Parallel-agent systems need task ownership or locking to prevent duplicate and conflicting work. For a small local change: one strong agent is usually better than several competing over the same problem.

## 9. Isolate Parallel Agents

A good architecture uses git worktrees or separate clones, separate branches, containers/sandboxes, task ownership, and CI as the integration gate. Avoid multiple autonomous agents mutating the same working tree.

## 10. MCP: Prefer a Few High-Value Tools

A coding agent increasingly works beyond the repository with integrations to GitHub, issue trackers, Sentry, PostgreSQL, browser, and internal tooling. Dozens of MCP servers create tool-selection ambiguity, token overhead, a larger attack surface, and more complicated permissions. Start with two or three integrations that directly support the workflow, and add more only when they demonstrate clear value.

## 11. Agent-Friendly CLI Often Beats More Documentation

Expose stable commands rather than making the agent compose fragile chains of docker, curl, jq, psql, systemctl, and similar commands. Agent-friendly tooling is becoming an engineering asset just like human-friendly tooling.

## 12. Prefer Sandboxing to Endless Confirmation Dialogs

Repeated permission prompts create approval fatigue. A stronger boundary uses sandbox/container execution, access only to the required repository, network deny-by-default or allowlists, read-only production access, short-lived credentials, and human approval for deploys, production database mutations, secrets, and destructive operations. An unrestricted host shell should not be the default for autonomous agents.

## 13. Treat Agent Configuration as Software Supply Chain

Treat .cursor/, .claude/, AGENTS.md, skills, hooks, and MCP configuration with similar care to dependencies, Dockerfiles, and CI configuration. Review third-party skills, pin versions where practical, minimize permissions, do not blindly execute unknown hooks, and version-control agent configuration.

## 14. Do Not Use the Most Expensive Model for Everything

Route tasks according to difficulty: rename/boilerplate and simple unit tests use fast models; unfamiliar codebase, architecture, concurrency bugs, security reviews, and migration/deployment logic use frontier models. Model routing matters even more with parallel agents — frontier inference is usually wasteful for mechanical work.

## 15. Simplify the Harness When Models Improve

Every planner, verifier, memory layer, or specialized prompt usually compensates for a model weakness. When a new model generation arrives: rerun evals, remove unnecessary scaffolding, keep measurable improvements. Do not endlessly accumulate orchestration layers designed around old model limitations.

## 16. Use Best-of-N for Difficult Reasoning

For architecture or difficult debugging, several independent plans can outperform one long trajectory. Generate independent plans or hypotheses, compare them, then implement the best one. This works well for architecture, debugging hypotheses, algorithms, API design, and query optimization.

## 17. If the Trajectory Is Broken, Restart

A bad workflow: bad assumption → bad patch → corrective prompt → patch over patch → new inconsistency. Often the better workflow is: revert → improve spec → fresh context → restart. This can be cheaper and produce cleaner code than a long repair loop built on a flawed initial direction.

## 18. Design an Agent-Friendly Repository

A good repository should provide: one-command setup, one-command test, deterministic tests, local reproducibility, clear module boundaries, searchable code, machine-readable errors, fixtures/seed data, observability, and architecture constraints. For a hosting panel, reproducible test environments are especially useful — an agent should be able to safely create a domain, user, database, or certificate; modify web-server configuration; test DNS/TLS behavior; and then destroy the environment. If a new senior developer struggles to run and verify the repository, a coding agent will usually struggle too.

## 19. `Tests Passed` Does Not Mean Production-Ready

Green tests are only one signal. Critical code may also require static analysis, security checks, architecture review, runtime validation, performance checks where relevant, and independent/human review. Agent-generated PRs can pass tests while still introducing maintainability, security, or architectural problems. Verification should be layered.

## 20. The Human Role Shifts Toward Intent and Verification

A modern workflow: HUMAN → intent/architecture → planner → builder → tests/runtime → evaluator → diff → HUMAN. Humans remain especially important for product judgment, architecture, invariants, security boundaries, acceptance criteria, unusual trade-offs, and final evaluation of plausible but incorrect results.

# Sources

1. OpenAI --- [Harness engineering: leveraging Codex in an agent-first world](https://openai.com/index/harness-engineering/), 2026.
2. Anthropic --- [Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps), 2026.
3. Cursor --- [Best practices for coding with agents](https://cursor.com/blog/agent-best-practices), 2026.
4. OpenAI --- [How OpenAI uses Codex](https://openai.com/business/guides-and-resources/how-openai-uses-codex/), 2026.
5. Anthropic --- [Building a C compiler with a team of parallel Claudes](https://www.anthropic.com/engineering/building-c-compiler), 2026.
6. OpenAI --- [Open-source Codex orchestration: Symphony](https://openai.com/index/open-source-codex-orchestration-symphony/), 2026.
7. OpenAI --- [Running Codex safely](https://openai.com/index/running-codex-safely/), 2026.
8. Cursor --- [MCP for coding agents](https://cursor.com/guides/coding-agent-mcp), 2026.
9. Cursor --- [Model routing](https://cursor.com/guides/model-routing), 2026.
10. GitHub --- [Best practices for Copilot coding agent](https://docs.github.com/en/copilot/using-github-copilot/using-copilot-coding-agent-to-work-on-tasks/best-practices-for-using-copilot-to-work-on-tasks).
11. Anthropic --- [Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents), 2026.
12. Kapner et al. --- [Scanning the Harness: An Empirical Study of Supply-Chain Defects in AI Coding-Agent Configurations](https://arxiv.org/abs/2609.07360), 2026.
13. [Empirical study of agentic pull requests](https://arxiv.org/abs/2601.16839), 2026.