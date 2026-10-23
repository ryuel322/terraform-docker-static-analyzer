# Project Proposal

## Project title
Development of a static analysis tool for Infrastructure-as-Code scripts (Terraform/Docker) to detect configuration drift and security vulnerabilities.

## Team members
Dayana Kulmagambetova SE-2425

## Supervisor
Omirzak Islam Amanzholuly

## Problem statement
Infrastructure-as-Code (IaC) makes infrastructure reproducible, but errors in Terraform and Docker files are copied and deployed as easily as correct code. Typical problems include insecure defaults, exposed ports and storage, hardcoded credentials, unpinned versions of providers and images, and divergence between the declared configuration and the actual state of the infrastructure. These problems are often found late, for example during an audit or an incident. Existing static analysis tools offer different levels of support for security checks and for detection of configuration drift, and these capabilities are usually provided by separate tools or at different levels of depth. This project aims to combine security analysis and drift detection from static artifacts in one analyzer for Terraform and Dockerfile sources.

## Target users
DevOps and platform engineers, developers who write infrastructure code, and small teams without a dedicated security specialist, Software Engineering students, Cybersecurity students.

## Aim
To develop a static analysis tool for Terraform and Dockerfile sources that detects security vulnerabilities and indicators of configuration drift and presents the results in a clear, actionable report.

## Objectives
1. Analyze the problem domain and existing tools (literature review, comparison of existing systems).
2. Collect evidence of user needs through discussions with target users.
3. Define functional and non-functional requirements with acceptance criteria.
4. Design the architecture of the analyzer (parser, rule engine, drift detector, report generator).
5. Implement analysis of Terraform and Dockerfile sources with an extensible set of rules.
6. Implement drift detection from static artifacts (configuration code and state snapshots).
7. Evaluate the tool on a prepared test set against a baseline solution.

## Expected outcomes
A working command-line analyzer (prototype) for Terraform and Dockerfile
A set of security and drift rules with documentation
Reports in a human-readable and machine-readable format
Evaluation results (detection quality and analysis time) compared with a baseline
Project documentation and a traceable Git history

## Project scope
**Included:**
 Static analysis of Terraform configuration files and Dockerfiles
 Detection of security misconfigurations by rules
 Detection of configuration drift from static artifacts (code and state snapshots), without access to live infrastructure
 Report

**Excluded:**
 Connecting to cloud providers or running containers
 Automatic fixing of detected issues
 Support for other IaC tools (Ansible, Kubernetes manifests, Pulumi)
 Graphical interface (unless added after discussion with the supervisor)

## Engineering complexity
The project requires parsing of HCL and Dockerfile syntax, building an internal model of resources, designing a rule engine, comparing declared and recorded states, and evaluating results with quality metrics.