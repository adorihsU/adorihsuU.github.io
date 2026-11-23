<!--
Sync Impact Report:
- Version change: none -> 1.0.0
- Modified principles: none
- Added sections: Core Principles, Tech Stack and Architecture Constraints,
  Quality Gates and Testing Standards, AI Agent Working Agreement, Governance
- Removed sections: none
- Follow-up TODOs:
  - RATIFICATION_DATE: original adoption date is unknown
-->

# adorihsuU.github.io Constitution

## Core Principles

### I. Spec-First and Single Source of Truth

All feature additions and changes MUST begin with updates to `spec.md` and `plan.md` before
code implementation. When specification and code diverge, `spec.md` MUST be synchronized as
the single source of truth before implementation proceeds. `plan.md` MUST describe the approved
design required to satisfy that specification.

### II. Simplicity and YAGNI

Implementations MUST avoid unnecessary abstractions, future-oriented features, and dependencies
that the specification does not require. The smallest readable design that satisfies the
explicit acceptance criteria MUST be selected.

### III. Security and Privacy by Design

The static frontend MUST NOT contain API keys, tokens, authentication credentials, personal
data (PII), or secrets in source code, environment variables, build output, logs, or generated
assets. Data collection and browser persistence MUST be minimized and limited to explicitly
specified requirements.

### IV. Human-in-the-Loop Accountability

AI output is a draft and MUST NOT finalize ambiguous requirements by assumption. When a state
transition, layout, error behavior, dependency choice, or acceptance criterion is unclear,
implementation MUST stop and the AI agent MUST present a focused clarification list to the
human developer.

## Tech Stack and Architecture Constraints

- The implementation MUST use HTML5, CSS3, and TypeScript in strict mode.
- The build MUST emit only static assets that GitHub Pages can serve. The repository MUST NOT
  require server-side application infrastructure.
- The application MUST be implemented as a SPA and MUST operate under the GitHub Pages project
  path `/<repo-name>/`. Root-relative paths MUST NOT be used. Routing MUST use hash routing or
  a `404.html` fallback so direct URLs and reloads do not produce 404 responses.
- The system MUST NOT use a server-side database. State MUST remain in browser memory and, only
  when required by a specification, in `localStorage`, `sessionStorage`, or URL parameters.
- External libraries and UI frameworks MUST be added only when necessary. Browser APIs and
  TypeScript standard capabilities MUST be preferred over packages.

## Quality Gates and Testing Standards

- `tsconfig.json` MUST set `strict: true`. `any` and type assertions using `as` MUST NOT be used.
- Every implementation MUST pass with zero build errors, lint errors, and formatter errors.
- Every feature specification MUST define measurable acceptance criteria. Logic unit tests and
  integration tests for primary screen transitions and user operations MUST pass before
  completion.
- Specifications MUST cover success, failure, boundary, and external-communication failure
  cases, including fallback UI. Implementations MUST use semantic HTML and responsive layouts
  for mobile and desktop viewports.

## AI Agent Working Agreement

- Ambiguous wording such as "適切に" or "よしなに" MUST NOT remain in specifications.
  Unspecified state transitions, layouts, and error behavior require developer clarification
  before implementation.
- A task executed through `/speckit-tasks` MUST remain within its assigned scope. Unrelated
  source changes and discretionary refactoring are prohibited.
- If a hotfix is required, the corresponding `spec.md` MUST be updated after the fix to record
  the resulting behavior.

## Governance

This constitution is the highest-priority constraint for all specification, design,
implementation, testing, and review work. Informal practices may not override it.

Amendments require a documented proposal, the reason for the change, a semantic-version update,
and verification that dependent workflows remain consistent.

The project MUST use semantic versioning: MAJOR for incompatible principle or governance
redefinitions or removals, MINOR for new principles or materially expanded sections, and PATCH
for clarifications or non-semantic wording changes.

Every pull request or implementation review MUST verify compliance with the applicable
constitution principles. Any exception MUST be explicitly approved by the human developer and
documented with a justification and remediation plan.

**Version**: 1.0.0 | **Ratified**: TODO(RATIFICATION_DATE): determine original adoption date | **Last Amended**: 2026-11-23
