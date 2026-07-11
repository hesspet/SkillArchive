---
name: skills-overview-creator
description: Create or refresh a project-specific SkillsOverview.md inventory of installed project, global, and built-in OpenCode skills. Use this skill whenever a user asks to list, document, inventory, summarize, synchronize, or update installed skills, skill documentation, SkillsOverview.md, or available agent capabilities. It must preserve an existing overview on network failure, ask where to create a missing overview, add verified skills.sh links when available, and adapt descriptions and examples to the current project.
compatibility: Requires filesystem search, web access for skills.sh checks, and optional Git CLI access.
---

# Skills Overview Creator

Create a complete, project-aware Markdown overview of the skills currently available to OpenCode. Treat preserving an existing file as more important than producing a partial update.

## Safety invariants

- Finish skill discovery, project analysis, skills.sh checks, content generation, and validation before changing the target file.
- Do not delete or truncate an existing `SkillsOverview.md` before the replacement is ready and validated.
- Treat skills.sh `404` or `410` as "not listed" and continue without a skills.sh link.
- Treat DNS, TLS, connection, timeout, rate-limit (`429`), server (`5xx`), malformed-response, and unresolved redirect failures as technical skills.sh failures. Stop without changing the target or Git index.
- Never invent a skills.sh URL. Add one only after the exact candidate page returns a successful final `2xx` response and identifies the expected skill.
- Never run Git rollback commands such as `git restore`, `git checkout`, or `git reset`.
- If an existing overview was already lost or modified before a failure, stop, disclose this clearly, and ask the user to restore the file manually with Git. Suggest a command only; do not execute it.
- Preserve unrelated working-tree and index changes.

## 1. Determine the target

1. Use a path explicitly supplied by the user.
2. Otherwise search the current project for files named `SkillsOverview.md`.
3. If exactly one exists, update it without asking for a path.
4. If none exists, ask where to create it and propose `docs/SkillsOverview.md`.
5. If multiple files exist, ask which exact path to update.

Do not create a missing file until the user answers the path question.

## 2. Record initial state

Before work that can change files:

- Determine whether the project is a Git repository.
- Record whether the target exists.
- If it exists, record its content hash and relevant Git status.
- Record the current staged-file list so it can be checked later without modifying it.

These observations are safeguards, not permission to revert anything.

## 3. Discover installed skills

Inventory all sources available in the current environment:

- Project skill directories such as `.agents/skills`, `.opencode/skills`, and `.claude/skills`.
- Global OpenCode skills such as `~/.config/opencode/skills` and other user-level skill roots exposed by the current environment.
- Built-in or session-provided skills listed by OpenCode even when they have no filesystem directory.
- Lock files such as `skills-lock.json`, which can provide canonical source repository and skill paths.

Read each available `SKILL.md` frontmatter and enough body content to understand purpose and workflow. Do not follow directory links twice. Deduplicate by skill name while retaining every distinct scope, path, and source. Prefer project metadata over global metadata, then built-in metadata when descriptions conflict.

Classify every skill as one or more of:

- project-local
- global
- built-in or session-provided

## 4. Understand the project

Read concise project context before writing descriptions:

- `AGENTS.md` and equivalent instructions
- `README.md`
- project overview or architecture documentation
- manifests and major entry points when needed

Detect the documentation language from explicit project instructions and dominant documentation language. Ask once if language is ambiguous.

Translate generic skill capability into concrete project relevance. Do not claim a skill is relevant when the project provides no matching technology or workflow. Examples should mention real project components when useful, but remain valid requests for that skill.

## 5. Resolve documentation links

For every skill:

1. Prefer the documentation URL explicitly declared by its metadata.
2. When canonical GitHub source metadata contains `owner/repository` and the exact skill name, derive the skills.sh candidate `https://skills.sh/<owner>/<repository>/<skill>`.
3. Verify the candidate page and final redirect before including it.
4. A verified `404` or `410` means the skill is not listed. Continue and document its local source or repository instead.
5. If no trustworthy source mapping exists, do not guess a candidate URL. Document the known local source.
6. On a technical skills.sh failure, abort before any target-file or Git-index change.

Checking an unrelated website does not substitute for validating the exact skill page.

## 6. Generate the complete document

Generate the entire Markdown document away from the target. Use the detected project language and this structure:

```markdown
# Skill overview

[Scope and freshness note]

## Project-local skills

### skill-name

[Project-specific purpose]

- Scope and source
- Typical triggers
- Documentation
- Verified skills.sh link, when available
- Example request

## Global and built-in skills

[Same fields]

## Management

[Relevant update and lock-file guidance]
```

Quality requirements:

- Every discovered skill appears exactly once as a heading.
- Multiple locations or scopes for one name remain visible in its metadata.
- Descriptions, triggers, and examples agree with the underlying `SKILL.md`.
- Project-specific descriptions do not invent files, frameworks, or capabilities.
- A missing skills.sh page is not described as an error.
- No unverified skills.sh link appears.
- Existing content is fully replaced only after the new document passes validation.

## 7. Write safely

After all remote checks and validation succeed:

### Existing target

1. Write the complete replacement to a temporary file in the target directory.
2. Validate the temporary file again.
3. Replace the target in one atomic rename or replace operation supported by the platform. Do not delete the target first.
4. Remove temporary artifacts.
5. Do not stage the updated file. Confirm the Git index remains unchanged.

### Missing target

1. Create parent directories only after the user confirms the target path.
2. Write and validate the complete file.
3. If this is a Git repository, stage only the newly created overview with `git add -- <exact-path>`.
4. Do not stage any parent directory, wildcard, or unrelated file.
5. Do not commit.

## 8. Verify and report

Verify:

- target existence and complete content
- no temporary artifacts remain
- all discovered skills are represented
- all included skills.sh links were verified
- existing target: Git index unchanged
- new target in Git repository: only the target was newly added to the index

Report the target path, skill count by scope, links added, unlisted skills, and Git action taken. If aborted, report the technical failure and confirm that the existing target and Git index were not changed.

## Failure after accidental modification

If checks show that an existing target changed or disappeared despite an aborted run:

1. Stop all further writes.
2. State exactly what happened.
3. Ask the user to restore the old file manually.
4. If Git tracks it, suggest a non-destructive command such as `git restore --worktree -- <path>` only as text.
5. Do not execute that command or any other rollback.
