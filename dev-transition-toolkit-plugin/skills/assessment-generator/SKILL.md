---
name: generating-assessment
description: Generates a diagnostic assessment for developer transition by reading the codebase tech profile. Creates tiered questions (basic, intermediate, advanced) in multiple formats (multiple choice, short answer, scenario-based) specific to the project's tech stack. Use when creating a Phase 1 test for a new developer, generating onboarding questions, or preparing a knowledge evaluation.
---

# Assessment Generator

Creates a Phase 1 diagnostic assessment tailored to a specific project. Questions are generated from the codebase profile produced by the analyzing-codebase skill.

## Prerequisites

The file `transition/codebase-profile.md` must exist. If it doesn't, run the codebase analyzer first.

## Workflow

1. **Read the codebase profile**: Load `transition/codebase-profile.md` and identify all technologies, patterns, and concepts used in the project.

2. **Categorize topics**: Group findings into testable topic areas based on the technologies and concepts used. For example: "AWS Lambda", "SAM/CloudFormation", "DynamoDB", "API Gateway", "JWT Authentication", etc. Focus on the technologies themselves, not how this specific project uses them.

3. **Generate questions per topic**: For each topic area, create questions that test the candidate's general knowledge of that technology at three difficulty tiers:
   - **Basic**: Does the candidate know what this technology/concept is? (definitions, purpose, when to use it)
   - **Intermediate**: Can the candidate work with it independently? (configuration, common tasks, debugging, best practices)
   - **Advanced**: Can the candidate make architectural decisions with it? (trade-offs, scaling considerations, alternatives, when NOT to use it)

4. **Mix question formats**: Use a variety of question types per the templates in [QUESTION_TEMPLATES.md](QUESTION_TEMPLATES.md). Every topic should have at least one scenario-based question.

5. **Assemble the assessment**: Compile all questions into a single Markdown file. Include:
   - Topic area for each question (for scoring later)
   - Difficulty tier label
   - Question type label
   - Expected answer or answer key (in a separate section at the end)

6. **Save internal version**: Write the full assessment with answer key to `transition/phase1-assessment.md`. This is the internal version for the evaluator — never share this with the candidate.

7. **Generate candidate HTML**: Create `transition/phase1-assessment.html` — a self-contained HTML file that the candidate opens in their browser:
   - Clean, professional design with readable typography
   - All questions numbered sequentially (no topic labels, no difficulty tiers — these would bias the candidate)
   - Radio buttons for multiple choice questions
   - Text areas for short answer and scenario questions
   - A prominent "Export Answers" button at the bottom
   - The export button generates a Markdown file (phase1-answers.md) containing all the candidate's answers, numbered to match the questions, and triggers a download
   - NO answer key anywhere in the HTML (not even hidden in the source)
   - All styling and JavaScript inline in the single HTML file — no external dependencies

8. **Verify**: Check both files:
   - Read the HTML source and confirm the answer key is not present anywhere
   - Confirm every question from the internal markdown appears in the HTML
   - Confirm the export functionality is included

## Important notes

- This is a Phase 1 assessment — it tests the candidate's EXISTING knowledge of the technologies this project uses, NOT their knowledge of this specific codebase
- Questions should be about the technology itself. Ask "Explain how DynamoDB partition keys affect query performance" NOT "Why does this project use userId as the partition key?"
- The codebase profile tells us WHAT technologies to test — it does not provide the questions or answers
- Every question should map back to a technology or concept found in the codebase profile
- Aim for 5-8 questions per topic area across all tiers
- The answer key should contain correct answers based on general technology knowledge
- The goal is to find the candidate's strengths and weaknesses BEFORE they start working on the project