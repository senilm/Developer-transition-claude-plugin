# Question Templates

Reference for question formats and examples. Each question in the assessment should follow one of these templates.

## Multiple Choice
```
### [TOPIC] — [TIER]
**Type:** Multiple Choice

[Question text]

A) [Option]
B) [Option]
C) [Option]
D) [Option]
```

Example:
```
### Lambda Handler Patterns — Basic
**Type:** Multiple Choice

What is the purpose of the callback parameter in this project's Lambda handlers?

A) To return HTML responses to the browser
B) To signal completion and return a response to API Gateway
C) To log errors to CloudWatch
D) To trigger the next Lambda in the chain
```

## Short Answer
```
### [TOPIC] — [TIER]
**Type:** Short Answer

[Question text]

**Expected scope:** [1-2 sentences | a short paragraph | a code snippet]
```

Example:
```
### Error Handling — Intermediate
**Type:** Short Answer

Explain how errors thrown inside a Lambda handler in this project get surfaced to the API consumer. Trace the path from the throw to the API response.

**Expected scope:** A short paragraph
```

## Scenario-Based
```
### [TOPIC] — [TIER]
**Type:** Scenario

**Situation:** [Describe a realistic situation involving this project]

**Question:** [What should the candidate do / what would happen / how would they approach this]

**Expected scope:** [A short paragraph | step-by-step approach]
```

Example:
```
### SAM Configuration — Advanced
**Type:** Scenario

**Situation:** A new API endpoint needs to be added that triggers a Lambda function when a file is uploaded to S3. The function needs access to DynamoDB and should have a 60-second timeout.

**Question:** Walk through exactly what you would add or modify in the SAM template and what new files you would create. Be specific to how this project is structured.

**Expected scope:** Step-by-step approach with file names and config snippets
```

## Guidelines

- Multiple choice works best for Basic tier (tests recognition)
- Short answer works best for Intermediate tier (tests understanding)
- Scenario-based works best for Advanced tier (tests judgment and application)
- Every topic area must have at least one scenario-based question regardless of tier
- All examples in questions should reference actual patterns from this specific project