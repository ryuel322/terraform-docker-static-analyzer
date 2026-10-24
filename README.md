## Development of a static analysis tool for Infrastructure-as-Code scripts (Terraform/Docker) to detect configuration drift and security vulnerabilities.

A static analysis tool for Infrastructure-as-Code (Terraform and Dockerfile) that detects security vulnerabilities and signs of configuration drift before deployment.

## Problem statement
Infrastructure is increasingly defined as code (Infrastructure as Code). However, errors in Terraform and Docker configurations: such as open network access, unencrypted data storage, hardcoded secrets, a lack of version pinning, or discrepancies between the declared and actual state can go unnoticed and make their way into the production environment. Existing tools provide different levels of support for security checks and drift detection, often in separate tools. This project aims to cover both aspects in one analyzer.

## Target users
DevOps and platform engineers who maintain Terraform and Docker configurations
Developers who write infrastructure code
Students and small teams without a dedicated security team

## Expected outcomes
A tool that analyzes Terraform and Dockerfile sources and reports security issues
Detection of configuration drift using static artifacts (code and state snapshots)
Readable reports with explanations and recommendations
Evaluation of the tool against a baseline on a prepared test set

## Team
**Student:** Dayana Kulmagambetova, SE-2425 - Project management, requirements analysis, literature review, system and technology comparison, architecture and design, implementation, testing and evaluation, documentation
**Supervisor:** Omirzak Islam

## Scope and current status

**In scope:** static analysis of Terraform (.tf, state/plan JSON) and Dockerfiles; security rules; drift detection from static artifacts; report generation.

**Out of scope:** access to live cloud infrastructure, automatic remediation, support for other IaC languages.

**Status:** analysis and design stage (pre-defense 1). No runnable code yet.

## Technologies
To be finalized after the technology comparison (see docs/technology-comparison.md).

## Links
YouTrack project: https://terraformdockerstaticanalyzer.youtrack.cloud/projects/DIP & https://terraformdockerstaticanalyzer.youtrack.cloud/agiles/204-1/current 
 Documentation: see the docs/ folder
docs/project-proposal.md
docs/literature-review.md
docs/existing-systems-comparison.md
docs/technology-comparison.md
docs/requirements.md
docs/evaluation-plan.md

## Setup, execution and testing
Will be added as soon as runnable code is available.


