# Fresh Best Practices for Programming with AI Agents --- 2026

As of September 2026, effective coding-agent workflows have moved beyond
prompt engineering. The main unit of optimization is now the **agent
harness**: environment, context, tools, rules, feedback loops, and
verification.

> **The key question in 2026 is: what environment lets an agent find the
> right context, do the work, observe its own mistakes, and prove that
> the result is correct?**

## 1. Define Tasks as Engineering Contracts

A weak request is simply `Implement automatic SSL renewal.` A better
task resembles a GitHub issue:

``` text
Goal:
Implement automatic Let's Encrypt certificate renewal.

Constraints:
- Keep the existing certificate API.
- Do not restart unrelated services.
- Renewal must be safe to retry.

Acceptance criteria:
- Add a regression/integration test for expiring certificates.
- Successful renewal reloads the affected web server.
- Failed renewal leaves the current certificate intact.
- Existing tests and static checks pass.

Before modifying code:
1. Trace the current certificate provisioning path.
2. Explain where renewal should integrate.
3. Propose the smallest architectural change.
```

The important elements are **goal, constraints, acceptance criteria,
invariants, and verification**, not a long "magic prompt."

## 2. For Complex Changes: Plan → Execute

Before a non-trivial implementation, the agent should explore the
codebase, identify relevant components, produce an implementation plan,
and only then modify code.

But **do not over-plan**. Strong models benefit from architectural
intent, invariants, and success criteria more than instructions for
every class and method. A useful plan describes:

**what changes → affected components → preserved invariants →
verification.**

An excessively detailed planner can amplify an early design mistake
throughout the implementation.

## 3. Keep `AGENTS.md`, `CLAUDE.md`, and Repository Rules Short

Persistent instructions are useful, but should not become a project
encyclopedia. Include information that the agent cannot reliably infer,
needs across many tasks, or repeatedly gets wrong.

``` markdown
# Development
Install: uv sync
Tests: pytest
Static checks: ruff check . && mypy src

# Architecture
API -> Service -> Domain -> Infrastructure
Domain code must not import web-framework or ORM modules.

# Conventions
- asyncio only.
- Prefer existing abstractions.
- Database migrations must remain backward-compatible during rolling deploys.

# Verification
1. Run relevant unit tests.
2. Run mypy and ruff.
3. Run integration tests for cross-module changes.
```

A strong rule is:

> **Do not predict every possible agent mistake. Turn actual recurring
> mistakes into repository rules.**

## 4. Prefer Retrieval Over Context Dumping

Avoid manually stuffing dozens of files into the context window. Give
the agent repository navigation, grep, semantic search, and similar
retrieval tools.

Instead:

``` text
Investigate how domain provisioning is implemented.
Find the relevant code before proposing changes.
Follow existing patterns.
```

One architectural anchor can help:

``` text
Follow the transaction pattern used by src/domains/create.py.
```

Let the agent discover the rest. Excessive context can degrade reasoning
by adding irrelevant or competing signals.

## 5. Reset Contaminated Context

Do not keep one conversation alive indefinitely. Start fresh when a
logical unit is complete, the task changes, the agent repeats mistakes,
an early bad assumption contaminates later work, or too much irrelevant
history has accumulated.

For long-running tasks, use a structured handoff:

``` markdown
# STATUS

Completed:
- reproduced certificate renewal failure;
- added deterministic integration test;
- identified race between renewal and nginx reload.

Current failure:
tests/integration/test_ssl_renewal.py::test_concurrent_renewal

Evidence:
...

Next:
Inspect locking in certificates/renewal.py.
```

Then continue in a clean context window.

## 6. The Verification Loop Matters More Than the First Patch

A strong workflow is:

``` text
inspect → edit → build/run → inspect failure → edit → test → repeat
```

The agent needs an executable development environment. For
Python/backend work, expose `ruff`, `mypy`/`pyright`, unit and
integration tests, Docker Compose, application logs, database
inspection, API calls, and benchmarks.

For a hosting panel, also expose browser/Playwright testing, DOM and
network inspection, disposable VMs or containers, nginx/apache
configuration validation, service status, and DNS/TLS fixtures.

The ability to **observe the consequences of its own changes** is what
turns a code generator into a useful coding agent.

## 7. Use Tests as an External Oracle

There is a major difference between:

``` text
Implement the feature and write tests.
```

and:

``` text
These externally defined acceptance tests describe the required behavior.
Make them pass without weakening them.
```

The second is stronger because the implementation agent does not control
both the code and the definition of success.

For critical functionality:

``` text
spec/test author → implementation agent → independent evaluator
```

This is particularly useful for security, concurrency, billing,
permissions, database migrations, deployments, certificates, and DNS
management.

## 8. Use Multiple Agents Only for Truly Parallel Work

Multi-agent systems are practical, but not automatically better. Good
parallel tasks include implementation, test creation, security review,
performance investigation, documentation, and independent debugging
hypotheses.

A poor pattern is sending several agents after the same root cause.
Parallel-agent systems need task ownership or locking to prevent
duplicate and conflicting work.

For a small local change:

> **One strong agent is usually better than several agents competing
> over the same problem.**

## 9. Isolate Parallel Agents

A good architecture is:

``` text
                orchestrator
                     |
        +------------+------------+
        |            |            |
     agent A      agent B      agent C
        |            |            |
    worktree A   worktree B   worktree C
        |            |            |
        +--------- git -----------+
```

Use git worktrees or separate clones, separate branches,
containers/sandboxes, task ownership, and CI as the integration gate.
Avoid multiple autonomous agents mutating the same working tree.

## 10. MCP: Prefer a Few High-Value Tools

A coding agent increasingly works beyond the repository:

``` text
repo
├── GitHub
├── issue tracker
├── Sentry
├── PostgreSQL
├── browser
└── internal tooling
```

But dozens of MCP servers create tool-selection ambiguity, token
overhead, a larger attack surface, and more complicated permissions.

Start with **two or three integrations that directly support the
workflow**, and add more only when they demonstrate clear value.

## 11. Agent-Friendly CLI Often Beats More Documentation

For a hosting platform, expose stable commands:

``` bash
./dev domain inspect example.com
./dev ssl renew example.com
./dev dns check example.com
./dev service logs nginx --last 5m
./dev deploy sandbox example.com
./dev test provisioning
```

This is more robust than repeatedly making the agent compose fragile
chains of `docker`, `curl`, `jq`, `psql`, `systemctl`, and similar
commands.

> **Agent-friendly tooling is becoming an engineering asset just like
> human-friendly tooling.**

## 12. Prefer Sandboxing to Endless Confirmation Dialogs

Repeated permission prompts create approval fatigue. A stronger boundary
is:

``` text
agent
  |
sandbox
  ├── scoped filesystem
  ├── network allowlist
  ├── temporary credentials
  └── disposable environment
```

Good defaults are sandbox/container execution, access only to the
required repository, network deny-by-default or allowlists, read-only
production access, short-lived credentials, and human approval for
deploys, production database mutations, secrets, and destructive
operations.

An unrestricted host shell should not be the default for autonomous
agents.

## 13. Treat Agent Configuration as Software Supply Chain

Treat `.cursor/`, `.claude/`, `AGENTS.md`, skills, hooks, and MCP
configuration with similar care to dependencies, Dockerfiles, and CI
configuration.

Recent 2026 research found security/configuration defects in a
meaningful fraction of public coding-agent setups, including unpinned
MCP components and overly broad shell permissions.

Therefore: review third-party skills, pin versions where practical,
minimize permissions, do not blindly execute unknown hooks, and
version-control agent configuration.

## 14. Do Not Use the Most Expensive Model for Everything

Route tasks according to difficulty:

  Task                         Model class
  ---------------------------- -------------
  Rename / boilerplate         fast
  Simple unit tests            fast
  Documentation                fast
  Obvious refactor             medium
  Unfamiliar codebase          strong
  Architecture                 frontier
  Concurrency bug              frontier
  Security review              frontier
  Migration/deployment logic   frontier

Model routing matters even more with parallel agents. Frontier inference
is usually wasteful for mechanical work.

## 15. Simplify the Harness When Models Improve

Every planner, verifier, memory layer, or specialized prompt usually
compensates for a model weakness. When a new model generation arrives:

``` text
new model → rerun evals → remove unnecessary scaffolding → keep measurable improvements
```

Do not endlessly accumulate orchestration layers designed around old
model limitations.

## 16. Use Best-of-N for Difficult Reasoning

For architecture or difficult debugging, several independent plans can
outperform one long trajectory:

``` text
Agent A → plan A
Agent B → plan B
Agent C → plan C
             ↓
           judge
             ↓
        implementation
```

You usually do not need three full implementations. Generate independent
plans or hypotheses, compare them, then implement the best one.

This works well for architecture, debugging hypotheses, algorithms, API
design, and query optimization.

## 17. If the Trajectory Is Broken, Restart

A bad workflow:

``` text
bad assumption → bad patch → corrective prompt → patch over patch → new inconsistency
```

Often the better workflow is:

``` text
revert → improve spec → fresh context → restart
```

This can be cheaper and produce cleaner code than a long repair loop
built on a flawed initial direction.

## 18. Design an Agent-Friendly Repository

A good repository should provide:

``` text
one-command setup
one-command test
deterministic tests
local reproducibility
clear module boundaries
searchable code
machine-readable errors
fixtures / seed data
observability
architecture constraints
```

For a hosting panel, reproducible test environments are especially
useful: an agent should be able to safely create a domain, user,
database, or certificate; modify web-server configuration; test DNS/TLS
behavior; and then destroy the environment.

> If a new senior developer struggles to run and verify the repository,
> a coding agent will usually struggle too.

## 19. `Tests Passed` Does Not Mean Production-Ready

Green tests are only one signal. Critical code may require:

``` text
tests
+ static analysis
+ security checks
+ architecture review
+ runtime validation
+ performance checks where relevant
+ independent/human review
```

Agent-generated PRs can pass tests while still introducing
maintainability, security, or architectural problems. Verification
should be layered.

## 20. The Human Role Shifts Toward Intent and Verification

A modern workflow increasingly looks like:

``` text
               HUMAN
                 |
       intent / architecture
                 |
               planner
                 |
               builder
                 |
          +------+------+
          |             |
        tests         runtime
          |             |
          +------+------+
                 |
             evaluator
                 |
               diff
                 |
               HUMAN
```

Humans remain especially important for product judgment, architecture,
invariants, security boundaries, acceptance criteria, unusual
trade-offs, and final evaluation of plausible but incorrect results.

# Recommended Workflow

For a serious software-development project:

``` text
1. Issue/spec
   ↓
2. Agent explores repo
   ↓
3. Plan
   ↓
4. Human checks architecture/invariants
   ↓
5. Fresh implementation context
   ↓
6. Agent implements
   ↓
7. Targeted tests + static checks + integration/runtime checks
   ↓
8. Independent review agent
   ↓
9. Agent fixes verified findings
   ↓
10. Full CI
   ↓
11. Human reviews final diff
```

For a large parallel task:

``` text
                 specification
                       |
                     planner
                       |
        +--------------+--------------+
        |              |              |
   agent/worktree A agent/worktree B agent/worktree C
        |              |              |
        +--------------+--------------+
                       |
                  integration
                       |
                    evaluator
                       |
                final verification
```

Add multi-agent orchestration only when a single strong agent has
actually become the bottleneck.

# Practical Checklist

1.  **Build a verification loop, not a perfect prompt.**
2.  Give the agent a complete executable development environment.
3.  Define tasks as engineering issues with acceptance criteria.
4.  Use Plan → Execute for complex changes, but do not over-plan.
5.  Keep `AGENTS.md` and repository rules concise.
6.  Prefer retrieval over context dumping.
7.  Use fresh contexts and structured handoffs.
8.  Separate builder and evaluator for critical tasks.
9.  Parallelize only genuinely parallelizable work.
10. Isolate agents with worktrees and containers.
11. Connect only high-value MCP/tools.
12. Build an agent-friendly CLI.
13. Make sandboxing and scoped credentials the default.
14. Review skills, MCP servers, and hooks as supply-chain dependencies.
15. Route simple and difficult tasks to appropriate model classes.
16. Simplify the harness when newer models make scaffolding unnecessary.
17. Use Best-of-N for difficult reasoning.
18. If the trajectory is corrupted, revert and restart.
19. Do not treat green tests as sufficient verification.
20. Optimize the repository for **verified outcomes**, not generated
    lines of code.

# Sources

1.  OpenAI --- [Harness engineering: leveraging Codex in an agent-first
    world](https://openai.com/index/harness-engineering/), 2026.
2.  Anthropic --- [Harness design for long-running application
    development](https://www.anthropic.com/engineering/harness-design-long-running-apps),
    2026.
3.  Cursor --- [Best practices for coding with
    agents](https://cursor.com/blog/agent-best-practices), 2026.
4.  OpenAI --- [How OpenAI uses
    Codex](https://openai.com/business/guides-and-resources/how-openai-uses-codex/),
    2026.
5.  Anthropic --- [Building a C compiler with a team of parallel
    Claudes](https://www.anthropic.com/engineering/building-c-compiler),
    2026.
6.  OpenAI --- [Open-source Codex orchestration:
    Symphony](https://openai.com/index/open-source-codex-orchestration-symphony/),
    2026.
7.  OpenAI --- [Running Codex
    safely](https://openai.com/index/running-codex-safely/), 2026.
8.  Cursor --- [MCP for coding
    agents](https://cursor.com/guides/coding-agent-mcp), 2026.
9.  Cursor --- [Model routing](https://cursor.com/guides/model-routing),
    2026.
10. GitHub --- [Best practices for Copilot coding
    agent](https://docs.github.com/en/copilot/using-github-copilot/using-copilot-coding-agent-to-work-on-tasks/best-practices-for-using-copilot-to-work-on-tasks).
11. Anthropic --- [Demystifying evals for AI
    agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents),
    2026.
12. Kapner et al. --- [Scanning the Harness: An Empirical Study of
    Supply-Chain Defects in AI Coding-Agent
    Configurations](https://arxiv.org/abs/2609.07360), 2026.
13. [Empirical study of agentic pull
    requests](https://arxiv.org/abs/2601.16839), 2026.
