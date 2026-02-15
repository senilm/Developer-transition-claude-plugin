---
name: analyzing-codebase
description: Scans JavaScript and TypeScript project codebases to build a comprehensive tech profile including dependencies, architecture, design patterns, code complexity, test coverage, and CI/CD setup. Use when analyzing a project for developer onboarding, knowledge transfer, or transition planning.
---

# Codebase Analyzer

Produces a deep technical profile of a JS/TS project as a Markdown report. This profile is consumed by other transition toolkit skills (assessment-generator, learning-plan-generator, readiness-assessor).

## When to use

- User asks to "analyze this codebase" or "scan this project"
- Beginning a developer transition process
- Generating a tech profile for onboarding

## Workflow

1. **Scan dependencies**: Read package.json and identify all runtime, dev, and peer dependencies. Categorize them by purpose (framework, testing, utilities, build tools, etc.)

2. **Analyze architecture**: Examine the project directory structure (2-3 levels deep). Identify the architectural pattern — in this case, look for SAM/serverless patterns like Lambda handlers, template.yaml, API Gateway configurations, layers, etc.

3. **Identify design patterns**: Look at the actual code for patterns used — how handlers are structured, middleware usage, error handling approach, shared utilities, database access patterns, authentication, etc.

4. **Assess code quality signals**: Check for test setup (Jest, Mocha, etc.), linting config (ESLint, Prettier), CI/CD pipelines (GitHub Actions, CodePipeline, etc.), and any pre-commit hooks.

5. **Generate the profile report**: Compile all findings into a single Markdown file saved at `transition/codebase-profile.md` in the project root.

6. **Verify**: Re-read the generated report and cross-check against the actual codebase. Fill any gaps.

## Output

Save the final report to `transition/codebase-profile.md`. Every section should have real content — use "Not used in this project" rather than omitting sections.
