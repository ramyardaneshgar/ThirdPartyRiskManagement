
# Cybersecurity Risk Assessment – Company XYZ

## Overview
This repository documents a comprehensive cybersecurity risk assessment for **Company XYZ**, a mid-sized technology enterprise operating in both the **United States** and the **European Union**. The assessment identifies key vulnerabilities, evaluates their likelihood and impact, and provides actionable remediation strategies aligned with recognized security frameworks and compliance mandates.

By Ramyar Daneshgar

**Baseline State:**  
Company XYZ operates on **AWS Cloud**, uses **GitHub** for source control, supports a **remote workforce** with local administrator privileges, and engages a **third-party development team in Ukraine**.  
The organization is subject to **GDPR** and **PCI DSS** requirements.

**Desired State:**  
Adopt a **Zero Trust Architecture**, ensure continuous **regulatory compliance**, and achieve **audit readiness** through robust infrastructure, code, endpoint, and vendor governance controls.

https://www.loom.com/share/91f67eecd6d24af385e8927ac9517043)

---

## Executive Summary
The assessment identified five primary risk vectors impacting the organization’s security posture:

1. Cloud misconfiguration within AWS environments  
2. Source code repository security weaknesses  
3. Endpoint privilege and access control gaps  
4. Regulatory non-compliance with GDPR and PCI DSS  
5. Third-party and supply chain vulnerabilities  

Each domain was evaluated for exposure, mapped against compliance obligations, and prioritized by severity using a risk matrix.

---

## 1. AWS Infrastructure Security Assessment
**Findings:**
- **IAM Over-Privileging:** Excessive roles and policies increase the risk of unauthorized access.  
- **Insufficient Audit Logging:** Incomplete CloudTrail and GuardDuty coverage limits forensic visibility.  
- **Unprotected Data Assets:** Misconfigured S3 buckets and EBS volumes expose sensitive data.  
- **Flat Network Architecture:** Lack of segmentation between PCI and general compute workloads.  

**Recommendations:**
- Enforce least-privilege IAM using **Access Analyzer** and require **MFA** across all roles.  
- Enable and centralize **CloudTrail**, **GuardDuty**, and **Security Hub** logs (≥12-month retention).  
- Apply **Block Public Access**, enforce **KMS encryption** at rest, and **TLS 1.2+/1.3** in transit.  
- Redesign networks with **VPC segmentation**, **security groups**, and **NACLs** to isolate PCI workloads.  

---

## 2. Source Code Repository Security (GitHub)
**Findings:**
- Over-privileged accounts retain unnecessary access to production repositories.  
- Limited audit visibility increases mean time to detection for compromise.  
- Secrets and credentials exposed within source files.  
- Lack of enforced code review or protected branches.  

**Recommendations:**
- Implement **SAML SSO + MFA**, **least privilege access**, and **signed commits**.  
- Enable **GitHub audit logs** and forward events to the corporate **SIEM**.  
- Use **GitHub Advanced Security** for secret scanning and automated credential revocation.  
- Enforce **branch protection policies**, mandatory pull requests, and peer review workflows.  

---

## 3. Endpoint Security for Remote Workforce
**Findings:**
- Persistent **local admin rights** enable privilege escalation.  
- Inconsistent **patch and update management** across remote devices.  
- Limited **EDR/XDR visibility** into advanced threats.  
- Weak remote access and authentication mechanisms.  

**Recommendations:**
- Remove persistent admin rights and enforce **least privilege** through **MDM** (Intune/Jamf).  
- Automate OS and application patching via **Endpoint Manager**.  
- Deploy **EDR/XDR** with **SIEM integration** for real-time detection and response.  
- Mandate **disk encryption**, **DLP policies**, and **Zero Trust Network Access (ZTNA)** for all endpoints.  

---

## 4. Compliance Review (GDPR & PCI DSS)
**Key Compliance Risks:**
- Unauthorized software installations breach **PCI DSS 12.3** and **GDPR Article 5**.  
- Fragmented identity management violates **PCI DSS 8** and **GDPR Article 32**.  
- Cloud data replication across regions risks **GDPR Articles 44–46** non-compliance.  
- Insider threat and weak recovery controls conflict with **GDPR Article 24** and **PCI DSS 10 & 12.10.1**.  

**Recommendations:**
- Centralize IAM with **federated SSO (SAML/OAuth2)** and adaptive MFA.  
- Apply **geo-fencing** and enforce **data localization policies** for regulated data.  
- Deploy **UEBA** and **immutable backups** for anomaly detection and recovery testing.  
- Conduct **Data Protection Impact Assessments (DPIAs)** and maintain **audit documentation**.  

---

## 5. Third-Party Risk Assessment (Ukrainian Development Team)
**Findings:**
- Cross-border data access from a non-adequate jurisdiction introduces GDPR compliance risk.  
- Lack of verified third-party security maturity and governance.  
- Persistent repository and cloud access beyond contractual scope.  
- Potential for insecure coding practices and dependency-based vulnerabilities.  

**Recommendations:**
- Perform **Transfer Impact Assessments (TIAs)** and enforce **data localization policies**.  
- Require **SOC 2 / ISO 27001 certification** and formalize **SLAs** with breach notification clauses.  
- Implement **least-privilege** and **just-in-time (JIT)** access with **MFA** and **UEBA monitoring**.  
- Integrate **SAST**, **SCA**, and **DAST** into CI/CD for continuous code validation.  

---

## Risk Matrix

| Risk Description | Likelihood | Impact | Rating |
|------------------|-------------|---------|---------|
| AWS misconfigured IAM roles | High | High | Critical |
| Secrets exposed in GitHub repository | Medium | High | High |
| Local admin privileges on laptops | High | Medium | High |
| GDPR data transfer non-compliance | Medium | High | High |
| Third-party access risks | Medium | Medium | Medium |
| Lack of PCI network segmentation | Low | High | Medium |

---

## Remediation Roadmap

**Critical (0–30 Days):**  
Lock down AWS IAM roles (least privilege + MFA), enable full encryption (KMS + TLS 1.3), and remove local admin privileges from endpoints.

**High (30–90 Days):**  
Secure GitHub repositories (SSO, MFA, branch protection, secret scanning), embed SAST/DAST/SCA testing into CI/CD, deploy EDR/XDR, and complete GDPR TIAs.

**Medium (90–180 Days):**  
Audit third-party vendor security practices, enforce PCI-compliant segmentation, deploy continuous compliance monitoring with UEBA.

---

## Framework Alignment
- **AWS Security Best Practices** – AWS Whitepaper, 2023  
- **GDPR (Regulation EU 2016/679)** – Articles 5, 24, 32, 44–46  
- **PCI DSS v4.0** – Requirements 3, 8, 10, 12  
- **NIST SP 800-53 Rev.5** – Access Control, Audit, and Continuous Monitoring Families  
- **ISO/IEC 27001:2022** – Information Security Controls  

---

## License
This repository is for educational and demonstration purposes only. It does not represent a formal assessment of any real organization or system.
