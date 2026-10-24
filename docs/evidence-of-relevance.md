# Evidence of Relevance

**YouTrack Issue:** DIP-11

## 1. Overview

The purpose of this research is to validate the need for a static analysis tool that detects security vulnerabilities and potential configuration drift in Terraform and Docker files.

The target users include Software Engineering students, Cybersecurity students, developers, and DevOps engineers.

The research uses short interviews to identify common challenges, understand user needs, and validate project requirements.

## 2. Interview Questions

The following questions are used during the discussions:

1. Have you worked with Terraform or Docker?
2. What difficulties have you experienced when working with infrastructure configuration files?
3. Have you encountered security misconfigurations or configuration inconsistencies?
4. Would a tool that detects potential problems without cloud access be useful? Why?
5. What features would you expect from such a tool?

## 3. User Discussions

### Discussion 1 — Software Engineering Student

- **Participant:** [Name or anonymous identifier]
- **Date:** [Date]
- **Method:** [Online / In person]

**Answers:**
- Q1: [Actual answer]
- Q2: [Actual answer]
- Q3: [Actual answer]
- Q4: [Actual answer]
- Q5: [Actual answer]

### Discussion 2 — Cybersecurity Student

- **Participant:** [Name or anonymous identifier]
- **Date:** [Date]
- **Method:** [Online / In person]

**Answers:**
- Q1: [Actual answer]
- Q2: [Actual answer]
- Q3: [Actual answer]
- Q4: [Actual answer]
- Q5: [Actual answer]

### Discussion 3 — Developer / DevOps Representative

- **Participant:** [Name or anonymous identifier]
- **Date:** [Date]
- **Method:** [Online / In person]

**Answers:**
- Q1: [Actual answer]
- Q2: [Actual answer]
- Q3: [Actual answer]
- Q4: [Actual answer]
- Q5: [Actual answer]

## 4. Key Findings

### Verified Findings

Complete this section after reviewing the actual interview answers.

- **F1:** [Finding supported by participant responses]
- **F2:** [Finding supported by participant responses]
- **F3:** [Finding supported by participant responses]

### Assumptions

The following assumptions require user validation:

- **A1:** Users may benefit from automated Terraform and Dockerfile security checks.
- **A2:** Offline analysis may be useful when cloud access is unavailable.
- **A3:** CLI-based reports may simplify integration into development workflows.

These assumptions must not be presented as verified findings without supporting evidence.

## 5. Relationship to Requirements

After completing the interviews, connect the verified findings to the requirements in `docs/requirements.md`.

- **F1 → [Requirement ID]:** [Explain how the finding influences the requirement]
- **F2 → [Requirement ID]:** [Explain how the finding influences the requirement]
- **F3 → [Requirement ID]:** [Explain how the finding influences the requirement]

## 6. Conclusion

The completed interviews will provide evidence for refining the functional and non-functional requirements of the proposed Terraform/Docker static analyzer.

The final requirements should reflect verified user needs, while unverified assumptions will remain subject to further evaluation.