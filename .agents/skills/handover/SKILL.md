---
name: handover
description: Generate a context handover markdown file at .tmp/HANDOVER.md for the next agent.
---
# Handover Skill

This skill instructs the agent to write out a comprehensive context file to `.tmp/HANDOVER.md` to allow a new AI agent to quickly bootstrap context and take over the task.

## Instructions

1. **Synthesize Current Context**:
   - Determine what the workspace is currently focused on (refer to `TASKS.md`, documentation, recent commits, or outstanding tests).
   - Summarize the high-level goals and project state.
   - Identify current implementation details, recent changes, and active issues/blockers.
   - Identify critical files to read/explore (e.g., entry points, config files, tests, documentation).

2. **Write the Handover Document**:
   - Create or overwrite `.tmp/HANDOVER.md` (creating the `.tmp/` directory if it does not exist) with a structured markdown document.
   - Include the following sections in the handover file:
     - **Active Tasks & Goals**: What are we currently working on, and what is the end goal?
     - **Current Context**: Brief explanation of the feature architecture or system component in focus.
     - **Recent Progress**: What has been implemented or changed recently.
     - **Immediate Next Steps**: Concrete steps the next agent should execute.
     - **Key Files**: List of paths to important files for reading, including brief explanations of their roles.
     - **Active Issues & Blockers**: Known bugs, failing tests, or ambiguous requirements to be resolved.
     - **Verification commands**: Commands to run tests or build the app to verify correctness.

3. **Log & Notify**:
   - Inform the user that the handover file has been created, showing the path and summarizing the key points of the handover.
