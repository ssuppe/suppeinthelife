---
title: "The importance of TDD"
date: 2026-05-30T17:41:27Z
tags: ["ai-learnings"]
draft: false
---

Everyone knows AI is excellent at generating quick proofs of concept. It can spin up working code in minutes. But as a project grows-when you add features, modify existing ones, refactor, etc, things can go off the rails pretty quickly. Suddenly the AI is breaking previously working features, and you're going around in circles.

For a long time I'd just click through all the features and doublecheck they were still working. But this is maddening and really slow!

Over time, I've kind of rediscovered programming 101, but delegated it down to the agents. I don't know if this works for production code, but for my side projects it's been really great for stability, reliability and speed.

### High-Standard Documentation
Up-to-date documentation is the foundation. I keep design specs, product requirements, and engineering processes documented under `docs/`. This context acts as the source of truth, and saves me from re-explaining things on every new chat. This is the best quality of life gift I can give myself.

### TDD Baked into the Workflow
When I was a software engineer, writing tests was standard practice. For side projects, it’s easy to skip them. But in the era of AI-assisted coding, writing tests first is the ultimate guardrail. I instruct the AI to write the tests before drafting the implementation. It keeps the agent honest, and if the agent starts breaking existing features, I know right away.

### Automated Pre-Commit Gates
To guarantee code correctness on every commit, I use git hooks (via `.husky/pre-commit` in `goodnumbers`) to run automated checks. Unless a commit is documentation-only, it must pass:
* **Linting** via `lint-staged`
* **TypeScript builds** for both frontend and backend
* **All test suites**

If any check fails, the commit is aborted. Nothing broken ever reaches the repository.

This does slow things down sometimes, but I feel it's worth it for higher confidence!

### Interactive Testing Skills
I also have a manual skill called engineer-test. I can run this skill at any time to:
* Automatically execute test runs and check coverage gaps.
* Refine test cases and verify edge cases.
* Force the agent to follow a strict Red/Green (TDD) workflow.

Here is the exact `engineer-test` skill configuration I use:

```markdown
---
name: engineer-test
description: Enforce TDD and verify test coverage.
---
# Engineer Test

Review the current implementation and tests. 

### Context
1. Check `docs/eng/plan.md` for the current task's testing requirements.
2. Scan the `tests/` or `src/**/*.test.ts` files.

### Task
1. Verify if we are following a "Test-First" (Red-Green-Refactor) workflow.
2. Check for sufficient coverage of edge cases, error states, and core logic.
3. Run the project's test suite and report results.
4. Suggest specific missing tests if coverage is incomplete.
```

