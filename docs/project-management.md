# Project Management and Risks

## 1. Overview

This document describes the project management approach, responsibilities, milestones, risks, and dependencies for the Terraform/Docker static analyzer.
The project follows an iterative development approach, using GitHub for version control and YouTrack for task planning and progress tracking.

## 2. Project Responsibilities
**Project Member:** Dayana Kulmagambetova
Responsibilities:
Research and requirements analysis.
System architecture and technical design.
Development of the Go-based static analyzer.
Implementation of security detection rules.
Testing, evaluation, and documentation.
GitHub and YouTrack project management.

**Supervisor:** Omirzak Islam Amanzholuly
Responsibilities: Review project deliverables, provide feedback, and evaluate progress.
Additional team members and responsibilities will be documented if applicable.

## 3. Project Milestones

### Milestone 1 — First Pre-Defense
Date: October 24, 2026
Project proposal and literature review.
Existing systems and technology comparisons.
Requirements specification and architecture diagrams.
Prototype materials and evaluation plan.
GitHub and YouTrack documentation.

### Milestone 2 — Second Pre-Defense
Date: To be confirmed by the university.
Implementation of Terraform and Dockerfile parsers.
Development of security detection rules.
Implementation of offline configuration-state comparison.
CLI development and initial testing.

### Milestone 3 — Final Pre-Defense
Date: To be confirmed by the university.
Completed implementation and integration.
Testing and performance evaluation.
Comparison with baseline tools.
Final documentation and project demonstration.

## 4. Risk Management

The following risks may affect project development:

### Risk 1: Complex Terraform Parsing
- **Probability:** Medium
- **Impact:** High
- **Mitigation:** Use HashiCorp HCL v2 and incremental testing to handle complex configurations.

### Risk 2: False Positives in Security Detection
- **Probability:** Medium
- **Impact:** High
- **Mitigation:** Validate security rules using predefined test cases.

### Risk 3: Incorrect Interpretation of Terraform State Differences
- **Probability:** High
- **Impact:** High
- **Mitigation:** Limit supported attributes and distinguish potential configuration inconsistencies from actual infrastructure drift.

### Risk 4: Implementation Delays
- **Probability:** Medium
- **Impact:** High
- **Mitigation:** Prioritize MVP features and regularly monitor project deadlines.

### Risk 5: Insufficient User Feedback
- **Probability:** Medium
- **Impact:** Medium
- **Mitigation:** Conduct 3–5 interviews with potential users to validate project requirements.

### Risk 6: Exposure of Sensitive Configuration Data
- **Probability:** Medium
- **Impact:** High
- **Mitigation:** Process configuration files locally and exclude sensitive values from generated reports.

## 5. Project Dependencies

The main project dependencies are:

User research Requirements: Interview findings inform functional and non-functional requirements.
Requirements Architecture: System components and diagrams are based on approved requirements.
Architecture Implementation: Development depends on the selected Go libraries and component design.
Implementation Testing: Evaluation requires working components and prepared test datasets.
Supervisor feedback Revisions: Significant deliverables are updated according to supervisor comments.

## 6. Project Tracking

Project activities are managed using GitHub and YouTrack.
GitHub Repository:
https://github.com/ryuel322/terraform-docker-static-analyzer

YouTrack Project:
https://terraformdockerstaticanalyzer.youtrack.cloud/projects/DIP/issues

Each significant development task is tracked using a YouTrack issue ID (DIP-x).

Development changes are committed in separate branches, reviewed through Pull Requests, and linked to the corresponding YouTrack tasks.

The `main` branch represents the reviewed project baseline. Pre-defense submissions are identified using Git tags.

## 7. Conclusion

The project management approach provides a structured process for tracking development progress, responsibilities, and risks.
Defined milestones, task dependencies, and GitHub–YouTrack integration support traceability and help ensure that the project meets its academic and technical objectives.