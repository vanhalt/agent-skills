---
name: project-tech-stack
description: Guidelines and template for documenting or retrieving the project's technical stack, language versions, package manager, and main scripts.
---

# Project Technical Stack Information

Use this skill when you need to record or reference the technical stack configuration for this repository.

## Technical Stack

- **Language:** <programming language(s), comma-separated with version(s), e.g., Ruby 3.2.2, TypeScript 5.3>
- **Language Manager:** <mise | asdf | nvm | rbenv | none>
- **Framework:** <framework(s), comma-separated if multiple, e.g., Rails 7.1, React 18>
- **Monorepo:** <yes | no>
- **Package Manager:** <pnpm | npm | yarn | bun | rubygems>

## Main Scripts & Commands

Run these scripts to set up, migrate, or interact with the project database and environment:

```bash
# Database migration (Node/pnpm)
pnpm run db:migrate:local

# Ruby / Bundler alternative commands
bundle exec <command>
```
