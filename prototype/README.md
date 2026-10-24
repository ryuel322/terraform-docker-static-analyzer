# UX / CLI Prototype

## 1. Overview

This document demonstrates the proposed user interaction with the Go-based Terraform/Docker static analyzer.

The prototype illustrates how users will scan Infrastructure-as-Code files, identify security misconfigurations, and receive structured JSON reports.

## 2. Command-Line Usage

The planned CLI command is:

`iac-analyzer scan --path ./prototype/examples --format json --output report.json`

The analyzer will:

1. Read Terraform and Dockerfile configurations.
2. Apply predefined security and configuration rules.
3. Identify potential security risks.
4. Generate a structured JSON report.

## 3. Example Input

The prototype includes two sample files:

`examples/main.tf` - Terraform configuration containing a publicly accessible SSH rule.
`examples/Dockerfile` - Dockerfile containing a mutable image tag and explicit root execution.

These files demonstrate typical configuration security issues.

## 4. Example Output

The expected output is provided in `examples/sample-report.json`.

Each finding contains:
Rule identifier
Severity level
Affected file
Issue description
Recommended corrective action

## 5. User Interaction

The intended workflow is:

**User - CLI - File Parsing - Security Analysis - JSON Report**

Users provide local configuration files and review the generated findings. No cloud credentials are required for static analysis.

## 6. Prototype Status

This is a conceptual CLI prototype for the first pre-defense. Commands and reports illustrate the intended functionality and do not represent a completed implementation.

The working Go application will be developed and tested during the implementation stage.
