---
name: managing-transition
description: Orchestrates the full developer transition process from codebase analysis through assessment, evaluation, and learning plan generation. Use when starting a developer transition, handoff, knowledge transfer, or when someone says they want to onboard a new developer to the project.
---

# Transition Manager

Guides the complete developer transition workflow. Coordinates the other transition toolkit skills in the correct order.

## When to use

- "Start a developer transition"
- "Onboard a new developer"
- "Prepare for knowledge transfer"
- "Hand off this project"

## Transition workflow

Track progress using this checklist:
```
Transition Progress:
- [ ] Step 1: Analyze codebase
- [ ] Step 2: Generate assessment
- [ ] Step 3: Wait for candidate answers
- [ ] Step 4: Evaluate answers
- [ ] Step 5: Generate learning plan
```

### Step 1: Analyze codebase
Run the analyzing-codebase skill to produce `transition/codebase-profile.md`.
If this file already exists, ask the user if they want to regenerate or reuse it.

### Step 2: Generate assessment
Run the generating-assessment skill to produce:
- `transition/phase1-assessment.md` (internal with answer key)
- `transition/phase1-assessment.html` (shareable candidate version)

Tell the user: "Send the HTML file to the candidate. Once they export their answers and send back the file, save it as `transition/phase1-answers.md` and come back."

### Step 3: Wait for candidate answers
**STOP HERE.** Do not proceed until `transition/phase1-answers.md` exists.
Check if the file exists. If not, remind the user that we're waiting for the candidate's answers.

### Step 4: Evaluate answers
Run the evaluating-assessment skill to produce `transition/phase1-report.md`.
Show the user a brief summary of the results before proceeding.

### Step 5: Generate learning plan
Run the generating-learning-plan skill to produce `transition/learning-plan.md`.
Present the final plan to the user.

## Resuming a transition

If a transition is already in progress, check which files exist in the `transition/` folder:
- Only `codebase-profile.md` exists → Resume from Step 2
- `phase1-assessment.md` exists but no answers → Resume from Step 3
- `phase1-answers.md` exists but no report → Resume from Step 4
- `phase1-report.md` exists but no learning plan → Resume from Step 5
- Everything exists → Transition complete, ask user what they need

## Important notes

- Always check for existing files before rerunning a step — don't redo work unless the user asks
- The transition/ folder is the single source of truth for all progress
- Each step must complete successfully before moving to the next
- Step 3 is a hard stop — the process requires human action (candidate taking the test)