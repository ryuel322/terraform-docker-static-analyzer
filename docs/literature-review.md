# Literature Review

## 1. Introduction

Infrastructure-as-Code (IaC) technologies such as Terraform and Docker enable automated infrastructure management but may introduce security vulnerabilities, configuration inconsistencies, and deployment reliability issues.

13 scientific publications addressing IaC security, static analysis, Dockerfile vulnerabilities, and configuration drift detection. The objective is to identify existing approaches, their limitations, and their relevance to the proposed Go-based Terraform/Docker static analyzer.

## 2. Review of Existing Research

### 2.1. Infrastructure-as-Code Security

Rahman et al. (2019) [2] identified seven recurring security smells in IaC scripts, demonstrating the importance of automated security analysis.

Tiemtore and Loulergue (2026) [1] reviewed existing IaC security detection tools and classified their approaches, including rule-based analysis, model-based methods, and machine learning.

Verdet et al. (2025) [5] analyzed security policy adoption across 812 Terraform repositories. Their findings identified differences in security practices across cloud providers, particularly regarding encryption and access control.

These studies support the development of predefined security rules for detecting insecure configurations.

### 2.2. Static Analysis of Terraform

Saavedra et al. (2023) [3] introduced GLITCH, a framework supporting code smell detection across multiple IaC technologies.

Hu et al. (2023) [4] examined static analysis alerts in Terraform configurations and demonstrated that different alert categories require different levels of developer attention.

Qiu et al. (2024) [6] investigated semantic errors in cloud IaC programs, showing that syntactically valid configurations may still fail during deployment.

Chiari et al. (2024) [7] proposed DOML, a modeling approach that supports infrastructure descriptions across multiple IaC technologies.

These publications demonstrate the importance of structured parsing and rule-based analysis. However, detecting complex semantic errors may require additional cloud-specific knowledge beyond basic static checks.

### 2.3. Dockerfile Security and Reliability

Henkel et al. (2020) [8] investigated techniques for understanding Dockerfiles and highlighted the limitations of shallow syntactic analysis.

Rosa et al. (2024) [9] studied Dockerfile code smells and developer responses to automated fixes, demonstrating the practical relevance of remediation recommendations.

Shabani et al. (2025) [10] investigated Dockerfile build flakiness caused by changing dependencies and external conditions.

Zhang and Omoronyia (2026) [11] proposed an LLM-based approach for detecting and explaining Dockerfile security smells.

Dahlmanns et al. (2023) [12] demonstrated the risks of secret exposure in container images.

Together, these studies support checking mutable image tags, insecure execution settings, and potentially exposed secrets. However, static Dockerfile analysis cannot detect every vulnerability present in a built container image.

### 2.4. Configuration Drift Detection

Abuzakuk et al. (2026) [13] introduced RIVA, an LLM-based multi-agent approach for improving the reliability of configuration drift detection.

The research highlights the difficulties of identifying infrastructure inconsistencies, especially when verification tools produce unreliable results.

Unlike runtime infrastructure verification, the proposed diploma project focuses on offline comparison between supported Terraform configuration attributes and saved state snapshots.

Such comparisons can identify potential inconsistencies but cannot independently confirm actual drift in deployed infrastructure.

## 3. Comparative Analysis of Publications
## 3. Comparative Analysis of Publications

The reviewed publications address different aspects of Infrastructure-as-Code security, static analysis, and configuration management.

### 3.1. IaC Security Research

Tiemtore and Loulergue [1] review existing security detection tools, while Rahman et al. [2] identify common security smells in IaC scripts. Verdet et al. [5] examine Terraform security policy adoption across cloud providers.

These studies demonstrate the importance of automated security checks but do not directly address offline configuration-state comparison.

### 3.2. Terraform and Static Analysis

Saavedra et al. [3] introduce GLITCH for detecting IaC code smells. Hu et al. [4] investigate Terraform static analysis alerts, while Qiu et al. [6] explore semantic errors in cloud configurations. Chiari et al. [7] propose DOML for infrastructure modeling.

These approaches improve configuration analysis but focus on security, semantic correctness, or modeling rather than offline drift detection.

### 3.3. Dockerfile Security

Henkel et al. [8] investigate Dockerfile analysis techniques. Rosa et al. [9] study Dockerfile smells and automated fixes, while Shabani et al. [10] examine build reliability problems.

Zhang and Omoronyia [11] explore security smell detection using language models, and Dahlmanns et al. [12] investigate exposed secrets in container images.

These studies highlight Docker security risks but generally do not address Terraform configuration-state consistency.

### 3.4. Configuration Drift Detection

Abuzakuk et al. [13] propose RIVA, an LLM-based approach to configuration drift detection.

Although this research addresses infrastructure consistency, the proposed diploma project focuses on lightweight offline analysis without requiring access to deployed cloud resources.

### 3.5. Summary

The reviewed research demonstrates significant progress in IaC security and configuration analysis. However, security scanning and configuration drift detection are often investigated separately.

The proposed Go-based analyzer aims to combine selected Terraform and Dockerfile security checks with offline configuration-state consistency analysis in a single CLI application.


## 4. Research Gaps and Proposed Contribution

The reviewed literature identifies several challenges:

1. Security misconfigurations remain common in Infrastructure-as-Code projects.
2. Static analysis tools may produce alerts requiring additional interpretation.
3. Dockerfile security and reproducibility problems require different detection techniques.
4. Runtime infrastructure drift detection and offline configuration analysis address different types of inconsistencies.

The proposed project will investigate a lightweight, Go-based static analyzer combining selected Terraform security checks, Dockerfile analysis, and offline configuration-state consistency verification.

The system will use predefined security rules and generate structured JSON reports without requiring live cloud access.

The contribution is a focused integration of these functions, rather than a claim that existing tools cannot perform comparable individual checks.

## 5. Conclusion

The reviewed studies demonstrate the relevance of automated Infrastructure-as-Code security analysis and configuration verification.

Existing research provides approaches based on static rules, semantic analysis, infrastructure modeling, and machine learning.

The proposed diploma project builds upon these findings by designing a Go-based analyzer for Terraform and Dockerfile configurations, with particular attention to offline operation, understandable security findings, and potential configuration-state inconsistencies.

The effectiveness of the proposed approach will be evaluated using controlled test cases and comparisons with existing tools.

## 6. References

[1] Tiemtore, M. H., & Loulergue, F. (2026). *Tools for Detecting Security Issues in Infrastructure-As-Code: A Focused Literature Review.* ESEM 2026. https://doi.org/10.4230/LIPIcs.ESEM.2026.55

[2] Rahman, A., Parnin, C., & Williams, L. (2019). *The Seven Sins: Security Smells in Infrastructure as Code Scripts.* ICSE 2019. https://doi.org/10.1109/ICSE.2019.00033

[3] Saavedra, N., Gonçalves, J., Henriques, M., Ferreira, J. F., & Mendes, A. (2023). *Polyglot Code Smell Detection for Infrastructure as Code with GLITCH.* ASE 2023. https://doi.org/10.1109/ASE56229.2023.00162

[4] Hu, H., Bu, Y., Wong, K., Sood, G., Smiley, K., & Rahman, A. (2023). *Characterizing Static Analysis Alerts for Terraform Manifests: An Experience Report.* IEEE SecDev 2023. https://doi.org/10.1109/SecDev56634.2023.00014

[5] Verdet, A., Hamdaqa, M., Da Silva, L., & Khomh, F. (2025). *Assessing the Adoption of Security Policies by Developers in Terraform Across Different Cloud Providers.* Empirical Software Engineering, 30, 74. https://doi.org/10.1007/s10664-024-10610-0

[6] Qiu, Y., Kon, P. T. J., Beckett, R., & Chen, A. (2024). *Unearthing Semantic Checks for Cloud Infrastructure-as-Code Programs.* SOSP 2024. https://doi.org/10.1145/3694715.3695974

[7] Chiari, M., et al. (2024). *DOML: A New Modeling Approach to Infrastructure-as-Code.* Information Systems, 125, 102422. https://doi.org/10.1016/j.is.2024.102422

[8] Henkel, J., Bird, C., Lahiri, S. K., & Reps, T. (2020). *Learning from, Understanding, and Supporting DevOps Artifacts for Docker.* ICSE 2020. https://doi.org/10.1145/3377811.3380406

[9] Rosa, G., Zappone, F., Scalabrino, S., & Oliveto, R. (2024). *Fixing Dockerfile Smells: An Empirical Study.* Empirical Software Engineering, 29, 108. https://doi.org/10.1007/s10664-024-10471-7

[10] Shabani, T., Nashid, N., Alian, P., & Mesbah, A. (2025). *Dockerfile Flakiness: Characterization and Repair.* ICSE 2025. https://doi.org/10.1109/ICSE55347.2025.00238

[11] Zhang, W., & Omoronyia, I. (2026). *Security Smell Detection in Dockerfiles.* Automated Software Engineering, 33, 135. https://doi.org/10.1007/s10515-026-00684-z

[12] Dahlmanns, M., Sander, C., Decker, R., & Wehrle, K. (2023). *Secrets Revealed in Container Images: An Internet-wide Study on Occurrence and Impact.* ASIA CCS 2023. https://doi.org/10.1145/3579856.3590329

[13] Abuzakuk, S., Crijns, L., Kermarrec, A.-M., Pires, R., & de Vos, M. (2026). *RIVA: Leveraging LLM Agents for Reliable Configuration Drift Detection.* EuroMLSys 2026. https://doi.org/10.1145/3805621.3807644