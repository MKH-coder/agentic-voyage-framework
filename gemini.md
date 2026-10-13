# GEMINI.md - Agentic Architecture Configuration

You operate within a 3-layer architecture that separates concerns to maximize reliability, transparency, and efficiency when interacting with this repository.

## The 3-Layer Architecture

### Layer 1: Directive (What to do)
- **Purpose**: SOPs (Standard Operating Procedures) written in Markdown, living in `directives/`.
- **Contents**: Define goals, inputs, tools/scripts to use, expected outputs, and edge cases.
- **Style**: Natural language instructions, like you'd give a mid-level employee.

### Layer 2: Orchestration (Decision making)
- **Purpose**: Intelligent routing and context handling.
- **Contents**: Read directives, call execution tools in the correct order, handle errors, and manage context.
- **Style**: You are the glue between user intent and execution. Avoid trying to perform complex programmatic heavy lifting manually if a script exists.

### Layer 3: Execution (Doing the work)
- **Purpose**: Deterministic execution via scripts in `execution/`.
- **Contents**: Environment variables, API tokens, and configurations stored securely in `.env`.
- **Style**: Handle API calls, data processing, file operations, and database interactions reliably, testably, and fast.

## Operating Principles

1. **Check for tools first**: Before writing or executing a script, check the `execution/` directory per your directive. Only create new scripts if a suitable one does not already exist.
2. **Self-anneal when things break**: 
   - Read error messages and stack traces carefully.
   - Fix the script and test it again.
   - Update the directive with what you learned (API limits, timing nuances, edge cases).
3. **Update directives as you learn**: Directives are living documents. When you discover API constraints or better approaches, update the documentation.

## GitHub Integration Workflow

- **Issues & PRs**: Reference relevant directives when opening or responding to GitHub issues and pull requests.
- **Automation**: Ensure any CI/CD or automated scripts look to `directives/` for workflow definitions.
