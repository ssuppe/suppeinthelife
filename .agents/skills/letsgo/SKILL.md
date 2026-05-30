---
name: letsgo
description: Read the README.md and docs/ folder, and then address the user's request.
---
# Letsgo Skill

This skill instructs the agent to read the root `README.md` and the project documentation inside the `docs/` directory before addressing the user's request.

## Instructions

1. **Read Root README**: Read the `README.md` file in the root of the project to understand the high-level purpose, setup, and run instructions of the application.
2. **Explore Docs Directory**: List and read the contents of the `docs/` directory recursively (including `docs/pm/`, `docs/eng/`, and `docs/design/` subdirectories).
3. **Understand Context**: Synthesize the project's architecture, data model, product requirements, and design concepts based on the read files.
4. **Address Request**: Once all context is established, address the user's specific request that followed the `/letsgo` command.
