# Technology Comparison

## Decision 1: Implementation language
| Criterion | Python | Go | TypeScript |
|---|---|---|---|
| Libraries for HCL / Dockerfile parsing | Available | Available (HCL library from HashiCorp) | Limited |
| Development speed for a solo developer | High | Medium | High |
| Distribution as a single binary | No (needs interpreter) | Yes | No |
| Author's experience | [fill in] | [fill in] | [fill in] |
**Decision:** Python. Reason: fastest development within the project timeline (NFR-5), rich ecosystem for parsing and testing.

## Decision 2: Terraform input handling
| Criterion | HCL parser library (e.g. python-hcl2) | tree-sitter grammar | Terraform JSON (plan/state) only |
|---|---|---|---|
| Works without Terraform installed | Yes | Yes | Needs terraform to produce plan JSON; state JSON can be read directly |
| Handles source code (.tf) | Yes | Yes | No |
| Reading state for drift comparison | Separate JSON reader needed | Separate JSON reader needed | Yes |
| Complexity | Low | Medium | Low |
**Decision:** HCL parser library for .tf files plus a JSON reader for state files. Reason: both artifacts are required by FR-1 and FR-6 without live access (FR-8).

## Decision 3: Rule definition format
| Criterion | YAML rules | Rego (OPA) | Python plugins |
|---|---|---|---|
| Easy to write for non-programmers | High | Low | Low |
| Expressiveness | Medium | High | High |
| Extra dependency | No | Yes (OPA) | No |
**Decision:** YAML rules for common checks. Reason: extensibility requirement (NFR-3) with low learning curve.

## Decision 4: Report format
| Criterion | JSON | SARIF | Markdown/HTML |
|---|---|---|---|
| Machine-readable | Yes | Yes | No |
| Integration with code-scanning tools | Custom | Standard | No |
| Human-readable | Medium | Low | High |
**Decision:** console output plus JSON, SARIF as an optional extra. Reason: FR-9 and CI integration (NFR-4).

## Decision 5: Interface
| Criterion | CLI | Web UI | Library API |
|---|---|---|---|
| Implementation effort | Low | High | Medium |
| CI integration | Easy | Hard | Medium |
**Decision:** CLI. Reason: scope and timeline; web UI is out of scope.

## Sources
[add repository / documentation links for each library and format]