# Technology Comparison

## 1. Overview

Comparison technologies suitable for developing the Terraform/Docker static analyzer. The main selection criteria are performance, compatibility, maintainability, ease of implementation, and support for offline analysis.

## 2. Programming Language

**Alternatives:**

**Go:** High performance, native compilation, and strong support for infrastructure development tools.
**Python:** Simple syntax, extensive libraries, and rapid development.
**JavaScript (Node.js):** Cross-platform compatibility and a large package ecosystem.

**Selected: Go**

Go was selected because it provides efficient performance, supports standalone CLI applications, and integrates with existing Terraform and Docker parsing libraries. Familiarity with Go also simplifies development and maintenance.

## 3. Terraform Parsing

**Alternatives:**

**HashiCorp HCL v2:** Official Go library for parsing HCL configuration files.
**Regular expressions:** Simple but unreliable for complex nested configurations.
**Custom parser:** Flexible but requires significant development effort.

**Selected: HashiCorp HCL v2**

The `hashicorp/hcl/v2` library provides structured parsing of Terraform configuration files, allowing the analyzer to identify resources, attributes, and potentially insecure settings.

## 4. Dockerfile Parsing

**Alternatives:**

**Moby BuildKit Dockerfile Parser:** Go parser for Dockerfile instructions.
**Regular expressions:** Suitable for simple patterns but limited for complex instructions.
**Custom parser:** Provides flexibility but increases development complexity.

**Selected: Moby BuildKit Dockerfile Parser**

The `moby/buildkit/frontend/dockerfile/parser` package converts Dockerfile instructions into an abstract syntax tree (AST), enabling analysis of commands such as `FROM`, `RUN`, and `USER`.

## 5. Terraform State and JSON Processing

**Alternatives:**

**Go encoding/json:** Standard library for processing JSON data.
**HashiCorp terraform-json:** Provides structured Go types for Terraform JSON outputs.
**Custom JSON parser:** Offers flexibility but requires unnecessary development effort.

**Selected: Go encoding/json**

The standard Go JSON library will be used to process exported Terraform state data and generate structured analysis reports. Offline configuration-state comparison logic will be implemented separately.

## 6. User Interaction and Reporting

**Alternatives:**

**CLI with JSON reports:** Lightweight, cross-platform, and suitable for automation.
**REST API:** Enables external integration but requires additional development.
**Web interface:** User-friendly but introduces frontend complexity.

Selected: CLI with JSON reports

A command-line interface is suitable for the initial prototype because it allows local analysis without running a server. JSON reports will contain detected issues, severity levels, and recommendations. SARIF support may be added in future development.

## 7. Conclusion

The proposed technology stack consists of Go, HashiCorp HCL v2, Moby BuildKit Dockerfile Parser, Go encoding/json, and a CLI with JSON reporting.

These technologies provide a foundation for developing a lightweight, cross-platform static analyzer capable of detecting security misconfigurations and potential configuration inconsistencies without requiring live cloud infrastructure access.

## 8. References

1. Go — https://go.dev/
2. HashiCorp HCL — https://github.com/hashicorp/hcl
3. HCL Parser — https://pkg.go.dev/github.com/hashicorp/hcl/v2/hclparse
4. Moby BuildKit — https://github.com/moby/buildkit
5. Go JSON Package — https://pkg.go.dev/encoding/json
6. Terraform JSON — https://github.com/hashicorp/terraform-json