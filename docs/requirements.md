# Requirements Specification

## 1. Overview

This document defines the functional and non-functional requirements for the Terraform/Docker static analyzer developed in Go. The system aims to detect security misconfigurations, drift-prone patterns, and potential configuration-state inconsistencies.

Requirements are prioritized as **Must**, **Should**, or **Could**.

## 2. Functional Requirements

### FR-01: Terraform Analysis
**Priority:** Must

The system shall parse Terraform configuration files using HashiCorp HCL v2.

**Acceptance:** Valid `.tf` files are parsed, and invalid syntax produces clear errors.

### FR-02: Dockerfile Analysis
**Priority:** Must

The system shall analyze Dockerfiles and identify insecure instructions.

**Acceptance:** The analyzer detects predefined issues such as mutable `latest` image tags.

### FR-03: Security Detection
**Priority:** Must

The system shall detect security misconfigurations using predefined rules.

**Acceptance:** Known Terraform and Dockerfile security issues are correctly identified in test files.

### FR-04: Configuration-State Comparison
**Priority:** Must

The analyzer shall compare supported Terraform configuration attributes with exported state data.

**Acceptance:** Differences are identified in predefined test cases and reported as potential inconsistencies, not confirmed cloud drift.

### FR-05: CLI Interface
**Priority:** Must

Users shall execute scans through a command-line interface.

**Acceptance:** Valid file paths are accepted, and invalid paths produce clear errors.

### FR-06: JSON Reporting
**Priority:** Must

The system shall generate structured analysis reports.

**Acceptance:** Reports contain valid JSON with issue descriptions, severity levels, and affected files.

### FR-07: Remediation Recommendations
**Priority:** Should

The analyzer should suggest possible solutions for detected issues.

### FR-08: SARIF Reporting
**Priority:** Could

The system may support SARIF reports for integration with development tools.

## 3. Non-Functional Requirements

### NFR-01: Offline Operation
**Priority:** Must

The analyzer shall operate without live cloud access.

**Acceptance:** Local scans run without internet access or cloud credentials after installation.

### NFR-02: Reliability
**Priority:** Must

The system shall handle invalid inputs safely.

**Acceptance:** Invalid files produce errors without unexpected crashes.

### NFR-03: Maintainability
**Priority:** Must

The Go application shall use separate modules for parsing, analysis, and reporting.

**Acceptance:** Components are organized into packages and can be tested using `go test ./...`.

### NFR-04: Cross-Platform Support
**Priority:** Should

The application should support Windows and Linux.

## 4. Requirements Traceability

Requirements are linked to the research planned in [Evidence of Relevance](evidence-of-relevance.md).

**Provisional relationships:**

- **FR-01–FR-03:** Configuration errors and security concerns.
- **FR-04:** Configuration inconsistencies and drift risks.
- **FR-05–FR-06:** User preferences for scanning and reporting.
- **FR-07:** User expectations for remediation.
- **NFR-01:** Need for offline analysis.

These relationships will be updated with verified finding IDs after completing the DIP-11 user interviews.

## 5. Conclusion

These requirements define the initial scope of the Go-based Terraform/Docker static analyzer and provide a foundation for system architecture, implementation, and testing.