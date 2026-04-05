# Workspace Rules for Everything Claude Code (ECC)

This is the central rulebook for Copilot in this workspace.

## Core Principles
1. **Agent-First** — Delegate to specialized agents for domain tasks (e.g. `@planner`, `@tdd-guide`).
2. **Test-Driven** — Write tests before implementation, 80%+ coverage required.
3. **Security-First** — Never compromise on security; validate all inputs.
4. **Immutability** — Always create new objects, never mutate existing ones.
5. **Plan Before Execute** — Plan complex features before writing code.

## Security Guidelines
**Before ANY commit:**
- No hardcoded secrets (API keys, passwords, tokens). Use environment variables.
- All user inputs must be validated.
- Prevent SQL injection (use parameterized queries) and XSS (sanitize HTML).
- Enable CSRF protection, rate limiting, and generic error messages on endpoints.

## Coding Style
- **Immutability (CRITICAL):** Always create new objects, never mutate. Return new copies with changes applied.
- **File Organization:** Many small files over few large ones. 200-400 lines typical, 800 max. Organize by feature/domain.
- **Error Handling:** Handle errors every level. Provide user-friendly messages for the frontend, log context for the backend. Never silently swallow errors.
- **Quality:** Functions <50 lines, nesting <4 levels, no hardcoded values.

## Testing Requirements
- **Minimum Coverage:** 100%
- **TDD Workflow:** (1) Write failing test (RED), (2) minimal implementation (GREEN), (3) Refactor (IMPROVE).
- Troubleshoot correctly: check test isolation -> verify mocks -> fix implementation.

## Architecture
- **API Responses:** Use a consistent envelope (success indicator, data payload, error message, pagination).
- **Repository Pattern:** Encapsulate data access behind interfaces. Business logic must depend on the interface, not storage specifics.
