# cowork-md-forge

A Claude skill that analyzes any repository and auto-generates a `claude.md` file in the project root. The generated file gives Claude accurate, project-specific context for every future session — stack versions, architecture conventions, constraints, and interaction style.

## What it does

When triggered, the skill:

1. Scans your repo root for config files (`package.json`, `tsconfig.json`, `go.mod`, `Cargo.toml`, etc.)
2. Reads the main manifest to pull exact dependency versions
3. Maps the directory structure to identify architectural patterns
4. Detects linting, testing, and formatting tools
5. Writes a clean `claude.md` to your project root

The output is plain, declarative prose — no AI boilerplate, no em-dashes, no filler phrases.

## Installation

### Via Claude Code (CLI)

1. Copy `SKILL.md` into your Claude skills directory:

```bash
mkdir -p ~/.claude/skills/cowork-md-forge
cp SKILL.md ~/.claude/skills/cowork-md-forge/SKILL.md
```

2. In any Claude Code session, trigger the skill:

```
/cowork-md-forge
```

Or describe what you want: "analyze this repo and generate a claude.md"

### Via Cowork (desktop)

1. Download `SKILL.md`
2. In Cowork, go to Settings > Capabilities > Skills > Install from file
3. Select `SKILL.md`

## Example output

Given a Next.js + TypeScript project, the skill generates something like:

```markdown
# Project Context: my-saas-app

## 1. Scope & Objectives
- Description: SaaS web application built with Next.js App Router and Prisma ORM.
- Focus: Context-aware development alignment.

## 2. Core Stack & Versions
- Runtime: Node.js 20
- Framework: Next.js 14.2
- Language: TypeScript 5.4 (strict)
- Database ORM: Prisma 5.14
- Styling: Tailwind CSS 3.4
- Testing: Vitest 1.6

## 3. Architecture & Conventions
### Directory Layout
- `/src/app`: Next.js App Router pages and layouts
- `/src/components`: Shared UI components
- `/src/lib`: Utility functions and server-side helpers
- `/prisma`: Schema and migration files

### Code Patterns
- Language: Strict TypeScript
- Style: Prefer clean, modular, dry abstractions. Follow existing project patterns.

## 4. Constraints
- DO: Write complete code snippets with clear typing; use absolute imports per `tsconfig.json` paths.
- DON'T: Use deprecated Next.js Pages Router patterns or introduce major new dependencies without a prompt directive.

## 5. Interaction Model
- Style: Concise, direct, technical, and solution-first.
- Code Delivery: Provide complete block implementations rather than ambiguous placeholder comments.
```

## Safety

The skill will never overwrite an existing `claude.md` without asking for explicit confirmation first.

## License

MIT
