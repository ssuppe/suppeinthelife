---
name: handover-start
description: Read the README.md, docs/ folder, and .tmp/HANDOVER.md, and then address the user's request.
---
# Handover Start Skill

This skill instructs the agent to read the root `README.md`, the project documentation inside the `docs/` directory, and any handover context file at `.tmp/HANDOVER.md` before addressing the user's request.

## Instructions

1. **Read Root README**: Read the `README.md` file in the root of the project to understand the high-level purpose, setup, and run instructions of the application.
2. **Explore Docs Directory**: List and read the contents of the `docs/` directory recursively (including `docs/pm/`, `docs/eng/`, and `docs/design/` subdirectories).
3. **Read Handover File**: Check if `.tmp/HANDOVER.md` exists. If it exists, read it to bootstrap recent context, goals, next steps, and known issues left by the previous agent.
4. **Understand Context**: Synthesize all gathered information to understand the project architecture, recent state, current tasks, and next steps.
5. **Address Request**: Once all context is established, address the user's specific request that followed the `/handover-start` command.
