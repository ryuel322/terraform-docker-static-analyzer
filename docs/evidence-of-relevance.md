# Evidence of Relevance

## 1. Overview

To validate the relevance of the proposed Terraform/Docker static analyzer, three potential users with Software Engineering and Cybersecurity backgrounds were interviewed.

The discussions focused on configuration security, infrastructure inconsistencies, existing verification methods, and expected tool functionality.

## 2. User Discussions

### Discussion 1:Cybersecurity Student 

**Date:** 23.10.2026

**Q1. Experience with Docker/Terraform?**

Used Docker in laboratory assignments and personal projects, and Terraform for managing networks, security groups, and virtual machines in Yandex Cloud.

**Q2. Security problems encountered?**

Exposed secrets, root containers, unrestricted SSH access, mutable image tags, and unnecessary open ports.

**Q3. Configuration verification methods?**

Terraform validate/plan, Docker Compose, Hadolint, TFLint, Trivy, Checkov, and manual reviews.

**Q4. Configuration drift experience?**

Experienced infrastructure drift after manual cloud console modifications and Docker Compose inconsistencies caused by missing environment files.

**Q5. Usefulness of an offline analyzer?**

Considered useful for data privacy, CI integration, and independence from external services.

**Q6. Most valuable features?**

Security checks, secret detection, remediation recommendations, CIS/OWASP mapping, and baseline support.

**Q7. Preferred interface?**

CLI with JSON reporting; web interface optional.

### Discussion 2: Software Engineering Student 

**Date:** 23.10.2026

**Q1. Experience with Docker/Terraform?**

Used both technologies during university coursework and a final project involving a library website.

**Q2. Security problems encountered?**

No specific Docker or Terraform vulnerabilities were reported. Security concerns mainly involved application code and data handling.

**Q3. Configuration verification methods?**

VS Code debugging, automated tests, Docker logs, terminal output, and localhost error messages.

**Q4. Configuration drift experience?**

No previous experience reported.

**Q5. Usefulness of an offline analyzer?**

Considered useful because Software Engineering students may lack advanced cybersecurity knowledge.

**Q6. Most valuable features?**

Automated vulnerability detection and a security checklist.

**Q7. Preferred interface?**

CLI for terminal usage, JSON for documentation, and a web interface for daily use.

### Discussion 3: SE Developer 

**Date:** 24.10.2026
**Q1. Experience with Docker/Terraform?**

Used Docker to containerize Node.js/Python applications with PostgreSQL and Terraform to configure AWS VPCs, subnets, and EC2 instances.

**Q2. Security problems encountered?**

Hardcoded API keys and passwords, root container execution, and overly permissive AWS IAM policies.

**Q3. Configuration verification methods?**

Terraform validate/plan, Hadolint, yamllint, and IDE syntax highlighting.

**Q4. Configuration drift experience?**

Experienced differences between Docker environments and Terraform drift caused by manual changes in the AWS console.

**Q5. Usefulness of an offline analyzer?**

Considered useful for detecting credentials before Git commits, protecting private projects, and working without reliable internet access.

**Q6. Most valuable features?**

Secret scanning, security best-practice checks, and clear remediation recommendations.

**Q7. Preferred interface?**

CLI for everyday use and JSON reports for potential Git hooks and CI integration.

## 3. Key Findings

### Verified Findings

The following findings are supported by participant responses:
**F1- Security misconfigurations:** CYB-01 and DEV-01 reported issues involving secrets, excessive permissions, and insecure container configurations.
**F2- Configuration inconsistencies:** CYB-01 and DEV-01 reported infrastructure changes made outside Terraform and resulting inconsistencies.
**F3- Automated security analysis:** All three participants expressed interest in automated security checks.
**F4- Offline operation:** All participants considered local offline analysis useful.
**F5- Interface preferences:** All participants supported CLI and JSON reporting, while SE-01 additionally preferred a web interface.
**F6- Security guidance:** Participants requested understandable findings, remediation advice, or security checklists.

### Assumptions

The following assumptions require further validation:

**A1:** Automated scanning will significantly reduce security misconfigurations.
**A2:** Offline configuration-state comparison will reliably identify relevant inconsistencies.
**A3:** A lightweight Go-based analyzer will be sufficiently accurate and efficient.
**A4:** The preferences of three participants represent the broader target audience.

These assumptions will be evaluated during development and testing.

## 5. Conclusion

The three interviews provide initial evidence of practical security concerns and interest in automated Infrastructure-as-Code analysis.

Participants reported problems involving insecure permissions, exposed secrets, and configuration inconsistencies. All three expressed interest in automated analysis and offline operation.

These findings support the proposed Terraform/Docker static analyzer and inform its functional requirements. Further testing will be necessary to evaluate its effectiveness.