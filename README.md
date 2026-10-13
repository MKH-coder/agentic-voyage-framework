# 3-Layer Agentic Architecture Framework

A deterministic, scalable blueprint for AI Pair Programming and Autonomous Agent workflows in software repositories.

Developed by [MKH-coder](https://github.com/MKH-coder).

---

## Architecture Overview

This framework separates concerns into three distinct layers to ensure that AI coding assistants (like Google Antigravity, Gemini, Claude, and Codex) operate predictably, maintain context, and write high-quality code.

```
       +-----------------------------------------+
       |           Layer 1: DIRECTIVE            |
       |      (Markdown SOPs in directives/)      |
       +-----------------------------------------+
                            |
                            v
       +-----------------------------------------+
       |         Layer 2: ORCHESTRATION          |
       |   (AI Pair Programmer / Reasoning Glue) |
       +-----------------------------------------+
                            |
                            v
       +-----------------------------------------+
       |           Layer 3: EXECUTION            |
       |  (Deterministic Scripts in execution/)  |
       +-----------------------------------------+
```

### Layer 1: Directive (What to do)
- **Location**: `directives/`
- **Purpose**: Standard Operating Procedures (SOPs) written in natural language markdown.
- **Contents**: Goals, inputs, script calls, expected outputs, testing standards, and edge cases.
- **Audience**: AI agents and engineers.

### Layer 2: Orchestration (Decision Making)
- **Role**: Intelligent context router & reasoning agent.
- **Purpose**: Reads active directives, selects the right deterministic tools from `execution/`, monitors execution output, and handles errors.
- **Rule**: Avoid manual, brittle prompt gymnastics when a script can perform the task deterministically.

### Layer 3: Execution (Doing the work)
- **Location**: `execution/`
- **Purpose**: Deterministic, testable scripts (Python, Node.js, Shell).
- **Contents**: Environment validators, DB migrations, API testers, build runners.
- **Rule**: All sensitive variables live in `.env` (never hardcoded in code or committed to VCS).

---

## Operating Principles

1. **Check for existing tools first**: Always inspect `execution/` before writing custom one-off scripts.
2. **Self-anneal when things break**:
   - Inspect error traces and logs.
   - Fix scripts and re-run.
   - Update the respective directive in `directives/` with new learnings (rate limits, edge cases).
3. **Keep directives living**: Continuously refine SOPs as features evolve.
4. **Environment Security**: Keep `.env` gitignored and maintain `.env.example` as the canonical template.

---

## Directory Structure

```text
├── .env.example              # Template environment variables
├── .gitignore                # Protects secrets and build artifacts
├── README.md                 # Framework overview
├── gemini.md                 # Agent configuration and instructions
├── directives/               # Layer 1: SOPs and operational guidelines
│   ├── README.md
│   └── example_workflow.md
└── execution/                # Layer 3: Deterministic scripts & tools
    ├── README.md
    ├── verify_env.py
    └── verify_env.js
```

---

## Quick Start

1. Copy this framework into the root of your project:
   ```bash
   cp -r directives execution gemini.md .env.example /path/to/your/project/
   ```
2. Verify environment configuration:
   ```bash
   python3 execution/verify_env.py
   # or
   node execution/verify_env.js
   ```
3. Add custom directives for your application in `directives/`.
