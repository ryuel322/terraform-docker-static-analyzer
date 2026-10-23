# Comparison of Existing Systems

## 1. Overview

This section compares five existing tools for Infrastructure-as-Code (IaC) security analysis and configuration drift detection: **Checkov, Trivy, KICS, Hadolint, and driftctl**.

The purpose is to evaluate their capabilities, identify limitations, and justify the development of the proposed Terraform/Docker static analyzer.

## 2. Comparison Criteria

The tools are evaluated using nine criteria:

- **C1:** Terraform static analysis
- **C2:** Dockerfile static analysis
- **C3:** Terraform Plan JSON analysis
- **C4:** Offline configuration-state comparison
- **C5:** Operation without live cloud access
- **C6:** Detection of drift-prone configuration patterns
- **C7:** Support for custom security rules
- **C8:** SARIF reporting
- **C9:** Project maintenance status

## 3. Existing Solutions

### 3.1. Checkov

Checkov is an open-source security scanner supporting Terraform, Dockerfiles, and Terraform Plan JSON.

- **Supported:** C1, C2, C3, C5, C7, C8.
- **Partially supported:** C6, through security policies.
- **Not a dedicated feature:** C4.
- **C9:** Publicly maintained open-source project.

**Limitation:** Checkov focuses primarily on security misconfigurations rather than offline comparison of Terraform source code with saved state.

### 3.2. Trivy

Trivy is a security scanner that detects vulnerabilities and misconfigurations in containers and IaC files.

- **Supported:** C1, C2, C3, C5, C7, C8.
- **Partially supported:** C6, through predefined and custom policies.
- **Not a dedicated feature:** C4.
- **C9:** Publicly maintained open-source project.

**Limitation:** Trivy provides comprehensive security scanning but does not offer dedicated offline Terraform configuration-state comparison.

### 3.3. KICS

KICS (Keeping Infrastructure as Code Secure) detects security weaknesses in Terraform, Dockerfiles, and other IaC formats.

- **Supported:** C1, C2, C3, C5, C7, C8.
- **Partially supported:** C6, through security queries.
- **Not a dedicated feature:** C4.
- **C9:** Publicly developed open-source project.

**Limitation:** KICS primarily identifies security misconfigurations rather than differences between Terraform configuration and saved state.

### 3.4. Hadolint

Hadolint is a specialized Dockerfile linter that detects incorrect instructions and insecure configuration practices.

- **Supported:** C2, C5, C6, C8.
- **Not supported:** C1, C3, C4.
- **Limited:** C7, through configuration of existing rules.
- **C9:** Publicly developed open-source project.

**Limitation:** Hadolint only analyzes Dockerfiles and does not support Terraform configuration or state analysis.

### 3.5. driftctl

driftctl detects differences between Terraform state and actual cloud infrastructure.

- **Supported:** Cloud infrastructure drift detection.
- **Not supported under the defined criteria:** C1–C6 and C8.
- **C7:** No general-purpose custom security rule engine documented.
- **C9:** Maintenance mode.

**Limitation:** driftctl requires cloud access for its main drift detection workflow and does not provide static Terraform/Dockerfile security analysis.

## 4. Proposed Solution

The proposed project aims to combine Terraform and Dockerfile security analysis with offline configuration consistency checks.

The main planned features include:

1. Static security analysis of Terraform and Dockerfile configurations.
2. Detection of insecure settings and drift-prone patterns.
3. Comparison of supported Terraform configuration attributes with saved state data.
4. Operation without direct access to cloud infrastructure.
5. Generation of structured reports with detected issues and recommendations.

Unlike tools focused exclusively on security scanning or live infrastructure drift detection, the proposed system will investigate these checks within a single offline workflow.

However, offline configuration-state differences indicate **potential inconsistencies**, not necessarily confirmed drift in deployed infrastructure.

## 5. Conclusion

Existing tools provide effective solutions for IaC security analysis and infrastructure drift detection. However, their functionality is distributed across different approaches.

The proposed analyzer aims to combine selected security checks and offline configuration consistency analysis in a lightweight tool for Terraform and Dockerfile projects.

## 6. References

1. Checkov — https://github.com/bridgecrewio/checkov
2. Trivy — https://github.com/aquasecurity/trivy
3. KICS — https://github.com/Checkmarx/kics
4. Hadolint — https://github.com/hadolint/hadolint
5. driftctl — https://github.com/snyk/driftctl