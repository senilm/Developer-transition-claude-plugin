---
name: evaluating-assessment
description: Evaluates a candidate's Phase 1 assessment answers against the answer key and generates a strength/weakness report. Scores answers by topic area, identifies knowledge gaps, and produces a readiness report. Use when scoring a developer assessment, evaluating candidate answers, or generating a knowledge gap analysis.
---

# Assessment Evaluator

Scores a candidate's Phase 1 answers and produces a detailed strength/weakness report that feeds into the learning plan generator.

## Prerequisites

- `transition/phase1-assessment.md` must exist (has the questions and answer key)
- `transition/phase1-answers.md` must exist (candidate's exported answers)

If either file is missing, tell the user what's needed.

## Workflow

1. **Load both files**: Read `transition/phase1-assessment.md` (with answer key) and `transition/phase1-answers.md` (candidate's responses).

2. **Map answers to questions**: Match each candidate answer to its corresponding question using the question numbers. If any answers are missing or unclear, note them as "Unanswered."

3. **Score each answer**: Compare against the answer key. For each question assign one of:
   - **Correct**: Demonstrates clear understanding, covers the key points
   - **Partial**: Shows some understanding but missed important aspects
   - **Incorrect**: Does not demonstrate understanding of the concept
   - **Unanswered**: No answer provided

   For short answer and scenario questions, use judgment — the candidate's wording doesn't need to match the answer key exactly. Look for whether they understand the concept.

4. **Map scores back to topics**: Using the topic and tier labels from the internal assessment file, group the scores. For each topic calculate:
   - How many correct / partial / incorrect / unanswered
   - Performance at each tier (basic, intermediate, advanced)
   - Topic verdict: **Strong** (mostly correct), **Moderate** (mixed), **Weak** (mostly incorrect/unanswered)

5. **Identify patterns across topics**: Look for broader signals:
   - Basics strong but advanced weak everywhere? → Needs depth, not breadth
   - Entire topic areas blank or wrong? → Needs fundamentals in those areas
   - Scenario questions consistently weak? → Needs hands-on practice
   - Strong in some areas, weak in others? → Targeted study needed

6. **Generate the report**: Save to `transition/phase1-report.md` with these sections:
   - **Candidate Summary**: One paragraph overall assessment
   - **Score Overview**: Total correct/partial/incorrect/unanswered out of total questions
   - **Topic Breakdown**: Each topic with per-tier scores and verdict (Strong/Moderate/Weak)
   - **Strengths**: Topics and concepts the candidate knows well
   - **Weaknesses**: Knowledge gaps ordered by priority (complete gaps first, then partial gaps)
   - **Patterns**: Any cross-topic observations from step 5
   - **Recommended Focus Areas**: Specific topics to study, ranked by importance

7. **Verify**: Re-read the report. Every weakness listed must trace back to actual wrong or partial answers. Do not assume gaps that aren't supported by the scores.