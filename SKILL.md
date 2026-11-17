---
name: scope-creep-detector
description: Audit software implementation plans and Git diffs against the original request to detect unnecessary features, unrelated refactors, abstractions, dependencies, and behavioral changes. Use when asked to review scope, avoid overengineering, or assess whether changes go beyond requirements. Audit is read-only by default; strict mode requires explicit user approval for questionable expansion.
---

# Scope Creep Detector

## Purpose
Compare proposed or completed software changes with the user's actual requirements. Prefer the smallest **sufficient** solution, not necessarily the fewest lines or files.

## Modes
- **Audit (default):** Read-only. Identify and explain questionable expansion; never modify files or block execution.
- **Strict (only when explicitly requested):** Before implementing questionable or out-of-scope changes, pause and ask for user approval. Do not treat silence as approval. This is an instruction-level checkpoint, not a guaranteed enforcement mechanism.

## Workflow
1. **Establish scope baseline.** Extract requested behavior, explicit constraints, non-goals, acceptance criteria, and relevant existing conventions. Distinguish user-stated facts from assumptions. If no original request is available, request it or state that the audit is provisional.
2. **Identify changes.** For plans, enumerate proposed work. For code, inspect the relevant diff and surrounding code as needed. Prefer the intended base branch or commit; if unavailable, state which comparison was used. Do not execute untrusted project scripts without authorization.
3. **Trace changes to scope.** For each material change, identify its requirement or technical justification. Consider direct requirements, necessary supporting work, existing architecture, correctness, accessibility, tests, security, and migration compatibility.
4. **Classify.** Mark each significant change as:
   - **Required:** Directly implements an explicit requirement.
   - **Justified:** Necessary supporting work, with concrete rationale.
   - **Questionable:** Benefit is plausible but not established by scope or evidence.
   - **Out of scope:** Unrelated feature or change without a defensible dependency on the request.
5. **Prioritize findings.** Focus on consequential additions: new features, dependencies, abstractions, public API changes, migrations, broad refactors, configuration, and behavior changes. Do not flag formatting, test coverage, or ordinary implementation details just because they add lines.
6. **Recommend minimal correction.** Say what to retain, remove, simplify, defer, or clarify, and why. Flag risks of removing anything essential.
7. **Respect mode.** In audit mode, report only. In strict mode, stop before questionable expansion and seek explicit approval; if already implemented, recommend changes but do not revert without authorization.

## Evidence rules
- Cite file paths and line numbers when available, or precise plan sections.
- Never claim a test, diff, or repository inspection was performed unless it actually was.
- Distinguish observed facts, inferences, and unresolved questions.
- Avoid invented scope scores, arbitrary thresholds, or equating line count with quality.
- If scope is ambiguous, classify conservatively as Questionable rather than Out of scope.
- Preserve security, correctness, accessibility, compatibility, and necessary tests even if not explicitly requested.

## Report format
**Scope baseline:** One or two sentences describing the requested outcome and known constraints.

**Verdict:** Within scope / Some expansion / Significant expansion / Insufficient context.

**Findings:** For each meaningful finding, show classification, affected files or plan steps, evidence, rationale, and recommended action. Omit empty categories.

**Keep:** Essential or justified changes worth preserving.

**Open questions:** Only decisions requiring clarification.

**Next action:** The smallest safe action to align implementation with scope.

Be concise. If there is no meaningful scope creep, say so without manufacturing findings.

For detailed decision examples, read `references/classification-guide.md`.
