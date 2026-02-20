# Alex & Arms Ceramica - Agent Memory Rules

This project uses persistent memory files so any agent can quickly recover context.

## Required behavior for every agent turn

1. Read `memory/project-context.md` and the latest section of `memory/conversation-log.md` before substantial work.
2. After each meaningful user interaction, append a short summary entry to `memory/conversation-log.md`.
3. If goals, priorities, or constraints changed, update `memory/project-context.md`.
4. Keep entries concise, factual, and date-stamped.

## Communication profile: Jelly

- Jelly is not a software developer and does not write production code.
- Explain technical concepts in plain language with clear definitions of terms.
- When sharing code or implementation details, state what each part is doing and why.
- Avoid assuming deep backend/infrastructure/software architecture background.
- Prefer functional/system-level explanations and actionable next steps.

## Memory files

- `memory/project-context.md`: durable context (goals, audience, constraints, active priorities).
- `memory/conversation-log.md`: chronological log of discussions, decisions, and requests.
- `memory/next-actions.md`: current TODOs and handoff notes for the next session.
