# Blockchain-Based Cryptocurrency Security Audit Guide

[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/slowmist_team.svg?style=social&label=Follow%20%40SlowMist_Team)](https://twitter.com/slowmist_team)

[English Version](./README.md),
[中文版本](./README_CN.md),
[日本語版](./README_JP.md)

This document outlines SlowMist's methodology, testing scope, and service coverage for blockchain and cryptocurrency security audits. It is intended as an overview of the audit approach for public blockchains, application-specific blockchains, smart contracts, and related blockchain applications.

## 1. Cryptocurrency Threat Modeling

SlowMist uses several classical security models to identify potential threats in cryptocurrency systems and to define audit priorities.

| Model | Core Content | Description |
|:---:| --- | --- |
| CIA | Confidentiality, Integrity, Availability | Defines the core objectives of a security architecture. |
| STRIDE | Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege | Helps systematically identify common threat categories and attack surfaces. |
| DREAD | Damage Potential, Reproducibility, Exploitability, Affected Users, Discoverability | Supports risk prioritization for discovered vulnerabilities. |
| PASTA | Define objectives, scope the technology, decompose the application, analyze threats, identify vulnerabilities, enumerate attack paths, and assess risk and impact | Provides a threat analysis process aligned with architecture and business context. |

## 2. Testing Methods

Audit work typically combines black-box, gray-box, and white-box testing.

| Test Method | Description |
|:---:| --- |
| Black-box testing | Verifies program behavior from the user perspective by observing outputs under different input scenarios, without access to internal implementation. |
| Gray-box testing | Designs test cases using a user perspective plus partial source-code awareness, focusing on inputs, outputs, and externally observable behavior. |
| White-box testing | Examines internal logic and implementation details in depth, including line-by-line analysis of critical code paths and potential defects. |

In black-box and gray-box testing, we use fuzzing, script-based testing, and similar techniques to feed interfaces or components with random data or specially structured inputs. This helps evaluate robustness and uncover abnormal behavior in edge cases, such as functional defects or performance anomalies.

In white-box testing, we analyze object definitions, critical flows, and implementation logic through methods such as code review. Combined with the security team's experience in known blockchain vulnerabilities, this helps verify whether key logic and core components contain known risks while also identifying potential 0day issues in new scenarios and emerging technologies.

## 3. Vulnerability Severity Classification

The Common Vulnerability Scoring System (CVSS) is an open framework for describing the characteristics and severity of software vulnerabilities. CVSS includes Base, Temporal, and Environmental metrics: the Base metrics reflect intrinsic properties of the vulnerability, the Temporal metrics capture characteristics that change over time, and the Environmental metrics reflect the impact within a specific deployment context.

Based on the CVSS methodology, SlowMist further defines a vulnerability severity classification tailored to blockchain scenarios:

| Level | Description |
|:---:| --- |
| Critical | Has a major impact on the security of the blockchain project and should be remediated immediately. |
| High | Significantly affects normal system operation and should be fixed as soon as possible. |
| Medium | Has a practical impact on project operation and should be scheduled for remediation. |
| Low | May affect system operation in specific scenarios and should be prioritized according to business context. |
| Weakness | Represents a theoretical security risk that is extremely difficult to reproduce in practice. |
| Suggestion | Does not necessarily constitute a direct vulnerability, but indicates better coding or architectural practices. |
| Information | Matches the intended design, but may still cause user asset loss or security misunderstanding under certain usage patterns. |

## 4. Public Blockchain Security Research

The SlowMist team's [Blockchain Threat Intelligence](https://bti.slowmist.com/) system continuously tracks ongoing security incidents and applies threat intelligence to its security audit services.

The team also analyzes publicly known blockchain security issues and has compiled a [Blockchain Common Vulnerability List](./Blockchain-Common-Vulnerability-List.md) to support risk identification and audit baseline construction.

## 5. Public Blockchain Security Audit

Depending on the audit objective, SlowMist divides public blockchain security auditing into mainnet security and compliance audits, source code security audits, and application-chain audits tailored to specific development frameworks.

### 5.1 Mainnet Security and Compliance Audit

For public chains and Layer 2 mainnets that are already live or about to launch, the audit focuses on the robustness of infrastructure protection, node distribution and disaster recovery, consensus reliability, and the resilience of core code against attacks. Historical audit records and regulatory compliance requirements are also considered to assess the mainnet security baseline and compliance status, resulting in a professional assessment report.

Typical audit areas include:

- Infrastructure security assessment
- Network scale and node distribution assessment
- Consensus algorithm security assessment
- Core code security assessment
- Historical audit and compliance assessment

### 5.2 Source Code Security Audit

Source code security auditing adopts a "**white-box**" strategy and performs in-depth analysis of project source code. It typically combines automated static analysis with manual review to improve both coverage and precision.

#### 5.2.1 Static Source Code Analysis

The SlowMist team uses open-source or commercial code scanning tools for static analysis and manually reviews the findings. Supported mainstream languages include **C/C++/Golang/Rust/Java/Node.js/C#**.

The static analysis scope includes the following categories:

- Code quality and maintainability issues: unused variables or imports, inconsistent formatting, inconsistent naming, insufficient or outdated comments, poor readability, duplicated code, excessive complexity, poor testability, and design principle violations.
- Resource and execution safety issues: improperly closed resources, memory leaks, deadlocks, race conditions, infinite recursion, improper exception handling, and performance issues.
- Basic coding defects: magic numbers, hard-coded constants, type conversion errors, divide-by-zero errors, null pointer dereferences, integer overflow, and floating-point precision issues.
- Typical security risks: SQL injection, XSS, string formatting vulnerabilities, buffer overflow, insecure random number generation, path traversal, TOCTOU-style time and state issues, and hard-coded keys or sensitive information.
- Architecture and supply chain issues: high coupling, low cohesion, and outdated dependencies or dependencies with known security risks.

#### 5.2.2 Manual Code Review

During manual review, the SlowMist team examines critical code paths line by line to identify coding flaws and logical errors that automated tooling may not accurately detect. Primary focus areas include:

- Cryptographic Security
- Account and transaction security
- RPC security
- P2P security
- Consensus security
- Business logic security

### 5.3 Application Chain Security Audit

For application-chain scenarios, SlowMist also adopts a "**white-box**" strategy and performs comprehensive testing with emphasis on common coding pitfalls and framework-level security issues, such as:

- Replay Vulnerability
- Reordering Vulnerability
- Race Conditions Vulnerability
- Authority Control Vulnerability
- Block data Dependence Vulnerability
- Explicit Visibility of Functions
- Arithmetic Accuracy Deviation Vulnerability
- Malicious Event Log
- Asynchronous Call Security

Currently supported:

1. Cosmos-SDK framework-based blockchain audit
2. Substrate framework-based blockchain audit

## 6. Blockchain Application Audit

### 6.1 Smart Contract Security Audit

1. [Ethereum(Solidity) Smart Contract Security Audit](https://www.slowmist.com/en/service-smart-contract-security-audit.html)
2. [EOS(C++) Smart Contract Security Best Practices](https://github.com/slowmist/eos-smart-contract-security-best-practices)
3. [Solana(Rust) Smart Contract Security Best Practices](https://github.com/slowmist/solana-smart-contract-security-best-practices)
4. NEAR smart contract security audit
5. [Sui Move smart contract security audit](https://github.com/slowmist/Sui-MOVE-Smart-Contract-Auditing-Primer)
6. [Aptos Move smart contract security audit](https://github.com/slowmist/APTOS-MOVE-Smart-Contract-Auditing-Primer)
7. [TON smart contract security audit](https://github.com/slowmist/Toncoin-Smart-Contract-Security-Best-Practices)

### 6.2 Other Application

1. Zero-Knowledge Circuit Security Audit  
2. Interchain Bridge Application Security Audit  
3. Browser Plugin Wallet Security Audit  
4. Exchange Security Audit 

## 7. Public Audit Report

Refer to [Knowledge-Base](https://github.com/slowmist/Knowledge-Base/tree/master/open-report-V2)
