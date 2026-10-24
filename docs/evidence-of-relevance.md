# Evidence of Relevance

## 1. Overview

To assess the relevance of the proposed static analysis tool for Infrastructure-as-Code (Terraform/Docker), three potential users with backgrounds in Cybersecurity and Software Engineering were interviewed.

The interviews focused on practical experience with Docker and Terraform, common security misconfigurations, configuration drift, existing validation methods, and expectations regarding automated security analysis.

The collected responses were used to identify user needs and support the initial requirements of the proposed system.

## 2. User Interviews

### Interview 1 - Cybersecurity Student CYB 01

**Participant:** Cybersecurity student  

**Q1. Have you worked with Docker or Terraform? In what projects?**

The participant has used Docker, Docker Compose, and Terraform in university assignments and personal projects. Terraform was used to configure cloud infrastructure in Yandex Cloud.

**Q2. What configuration or security problems have you encountered?**

The participant identified several security risks, including exposed credentials, containers running as root, unrestricted SSH access (`0.0.0.0/0`), unpinned image versions, and unnecessary exposed ports.

**Q3. How do you usually check configuration files for errors?**

The participant uses `terraform validate`, `terraform plan`, Docker Compose validation, Hadolint, TFLint, Trivy, Checkov, and manual configuration reviews.

**Q4. Have you experienced unexpected configuration changes or inconsistencies?**

The participant reported configuration drift caused by manual modifications in the cloud console. Inconsistencies in Docker Compose environments were also mentioned.

**Q5. Would an offline security analysis tool be useful? Why?**

Yes. The participant considered offline analysis useful for protecting sensitive configurations, reducing dependence on external services, and integrating security checks into development workflows.

**Q6. Which features would be most valuable?**

Automated security checks, secret detection, clear remediation recommendations, security standard references such as CIS and OWASP, and support for managing accepted findings.

**Q7. Would you prefer CLI output, JSON reports, or a web interface?**

The participant preferred CLI output and JSON reports. A web interface was considered optional.

### Interview 2 - Software Engineering Student SE01

**Participant:** Third-year Software Engineering student  
**Q1. Have you worked with Docker or Terraform? In what projects?**

The participant used Docker and Terraform during university coursework, particularly in an SRE course and a final project involving a library website.

**Q2. What configuration or security problems have you encountered?**

The participant did not report specific Docker or Terraform vulnerabilities. Previous security-related concerns mainly involved application code and data handling.

**Q3. How do you usually check configuration files for errors?**

The participant uses VS Code debugging tools, automated tests, Docker logs, terminal output, and localhost error messages.

**Q4. Have you experienced unexpected configuration changes or inconsistencies?**

The participant had not directly experienced infrastructure configuration drift.

**Q5. Would an offline security analysis tool be useful? Why?**

Yes. The participant considered such a tool useful because developers without specialized cybersecurity knowledge may overlook security misconfigurations.

**Q6. Which features would be most valuable?**

Automated detection of security problems and a practical security checklist.

**Q7. Would you prefer CLI output, JSON reports, or a web interface?**

The participant preferred CLI output for terminal usage, JSON reports for documentation, and a web interface for everyday interaction.

### Interview 3 - SE Developer DEV01
**Participant:** Developer  

**Q1. Have you worked with Docker or Terraform? In what projects?**

The participant uses Docker to containerize Node.js and Python web applications with PostgreSQL. Terraform is used to practice Infrastructure-as-Code by creating AWS environments, including VPCs, subnets, and EC2 instances.

**Q2. What configuration or security problems have you encountered?**

The participant reported accidentally leaving API keys and passwords in configuration files. Other problems included containers running with root privileges and overly permissive AWS IAM policies.

**Q3. How do you usually check configuration files for errors?**

The participant uses `terraform validate` and `terraform plan` for Terraform configurations, along with Hadolint, yamllint, and IDE syntax highlighting for Dockerfiles and YAML files.

**Q4. Have you experienced unexpected configuration changes or inconsistencies?**

The participant experienced Docker environment differences caused by operating system or dependency variations. Terraform configuration drift was also encountered after manually modifying cloud resources through the AWS console.

**Q5. Would an offline security analysis tool be useful? Why?**

Yes. The participant considered offline analysis useful for identifying exposed credentials before publishing code, protecting private projects, and working in environments with unreliable internet access.

**Q6. Which features would be most valuable?**

The participant highlighted three features:

Secret scanning for hardcoded passwords, tokens, and private keys.
Security best-practice checks, including detection of containers running as root.
Clear explanations and remediation recommendations for identified problems.

**Q7. Would you prefer CLI output, JSON reports, or a web interface?**

The participant preferred CLI output for everyday development and optional JSON reports for Git hooks or future CI integration.

## 3. Analysis of Interview Results

### 3.1. Security Misconfigurations

Two participants (CYB-01 and DEV-01) reported practical experience with security misconfigurations in Docker and Terraform environments.

The most frequently mentioned issues involved exposed credentials, excessive privileges, insecure network access, and unsafe configuration practices.

This finding supports the inclusion of automated security checks in the proposed analyzer.

### 3.2. Configuration Drift and Inconsistencies

CYB-01 and DEV-01 reported infrastructure configuration drift following manual changes through cloud management consoles.

DEV-01 additionally described differences between Docker execution environments. Such differences represent environment inconsistencies but are not necessarily infrastructure configuration drift.

These observations support investigating offline comparison of available Terraform configuration and state artifacts. However, detecting actual cloud infrastructure drift without live infrastructure access remains outside the proposed scope.

### 3.3. Limitations of Existing Verification Methods

Participants reported using tools such as Terraform validation commands, Hadolint, TFLint, Checkov, and debugging utilities.

The interviews indicate that users rely on different verification approaches depending on their technical background.

CYB-01 uses specialized security tools, while SE-01 relies mainly on general development and debugging tools.

This suggests that clear findings and remediation guidance may be particularly valuable for users with limited cybersecurity experience.

### 3.4. Interest in Offline Analysis

All three participants expressed interest in an offline security analysis tool.

Reported benefits included:

Protecting sensitive configuration files.
Detecting issues before committing or publishing code.
Working without reliable internet access.
Supporting local development workflows.
Reducing dependence on external services.

These responses support offline operation as a non-functional requirement.

### 3.5. Preferred Interface and Reporting

All three participants supported CLI output and JSON reporting.

CLI output was preferred for direct terminal interaction, while JSON was considered useful for documentation, automation, and potential CI integration.

SE-01 also expressed interest in a web interface. However, this feature is not essential to the initial project scope.

## 4. Verified Findings

The following findings are directly supported by interview responses:

**F1 — Security misconfiguration risks**

CYB-01 and DEV-01 experienced insecure configuration practices involving secrets, permissions, and container security.

**F2 - Configuration drift**

CYB-01 and DEV-01 reported infrastructure inconsistencies caused by manual changes to cloud resources.

**F3 — Need for automated security checks**

All three participants expressed interest in automated identification of configuration security issues.

**F4 - Offline analysis**

All three participants considered offline operation useful for their development workflows.

**F5 - CLI and JSON reporting**

All three participants expressed support for CLI output and JSON reports.

**F6 - Remediation guidance**

Participants requested understandable explanations, security checklists, or recommendations for resolving detected issues.

## 5. Assumptions and Limitations

Although the interviews provide initial evidence of user needs, several assumptions require further validation.

**A1 - Effectiveness of automated analysis**

Automated security scanning is expected to help identify configuration problems, but its accuracy and effectiveness have not yet been evaluated.

**A2 - Offline drift-related analysis**

The proposed tool is expected to identify certain inconsistencies between available Terraform configuration and state artifacts. It cannot guarantee detection of actual infrastructure drift without live cloud access.

**A3 - Performance and accuracy**

The expected performance and detection accuracy of the Go-based implementation must be validated experimentally.

**A4 - Generalizability**

The interviews involved only three participants. Their responses cannot be assumed to represent the entire DevOps or Infrastructure-as-Code community.

## 6. Requirements Traceability

The interview findings provide supporting evidence for the project's initial functional and non-functional requirements.

**F1 - FR-01, FR-02, FR-03:** Terraform analysis, Dockerfile analysis, and security misconfiguration detection.
**F2 - FR-04:** Offline configuration-state comparison.
**F3 - FR-03:** Automated detection of security issues.
**F4 - NFR-01:** Offline operation.
**F5 - FR-05, FR-06:** CLI output and JSON reporting.
**F6 - FR-07:** Explanations and remediation recommendations.

Secret scanning was explicitly requested by CYB-01 and DEV-01. It should therefore be considered during further requirements refinement, subject to project scope and implementation feasibility.


## 7. Conclusion

The three interviews provide initial evidence supporting the relevance of a static analysis tool for Terraform and Docker configurations.

Participants reported practical security concerns related to exposed secrets, excessive privileges, insecure configurations, and infrastructure inconsistencies. They also expressed interest in automated security checks, offline operation, and accessible reporting formats.

The findings support the project's initial requirements and provide a basis for further development of the proposed Go-based analyzer.

However, the interviews represent a small exploratory sample. The effectiveness, accuracy, and usability of the proposed solution must be evaluated through prototype implementation and controlled testing.
