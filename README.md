# Scope Creep Detector

Portable Agent Skill for auditing software implementation plans and diffs against requirements.

## Use
Ask your AI agent: "Use scope-creep-detector to audit this plan against my original request" or "Audit my changes against the original request in strict mode."

## Install
Place the `scope-creep-detector` directory in your agent's supported skills location, or provide its SKILL.md as project context. Installation and automatic skill discovery differ by ChatGPT and Claude product/environment.

## Modes
Audit is read-only by default. Strict mode adds explicit approval checkpoints, but requires agent cooperation and is not a hard runtime enforcement boundary.
