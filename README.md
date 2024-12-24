# Blockchain-Based Cryptocurrency Security Audit Guide

[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/slowmist_team.svg?style=social&label=Follow%20%40SlowMist_Team)](https://twitter.com/slowmist_team) 

[中文版本](./README_CN.md)

## 1. Cryptocurrency Threat Modeling

SlowMist uses multiple models to identify cryptocurrency threats.

**CIA** Triad: Confidentiality, Integrity, and Availability. These are the primary security goals and principles in a security infrastructure.

**STRIDE** Model: Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service (DoS), and Elevation of Privilege.

**DREAD** Model: Damage Potential, Reproducibility, Exploitability, Affected Users, and Discoverability.

**PASTA**: Define objectives, define the technical scope, decompose the application, analyze threats, identify vulnerabilities, enumerate attacks, and analyze risks and impacts.

## 2. Testing Method

The testing methods are as follows:

| Test Method       | Description                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------:| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Black-box testing | Black-box testing examines the program from a user perspective by providing a wide variety of input scenarios and inspecting the output. Black-box testers do not have access to the internal code. Final acceptance testing that occurs prior to system delivery is a common example of black-box testing.                                                      |
| Gray-box testing  | Gray-box testing combines the two approaches and is popular for software validation. In this approach, testers examine the software from a user perspective, analyzing inputs and outputs. They also have access to the source code and use it to help design their tests. They do not, however, analyze the inner workings of the program during their testing. |
| White-box testing | White-box testing examines the internal logical structures of a program and steps through the code line by line, analyzing the program for potential errors.                                                                                                                                                                                                     |

In black-box testing and gray-box testing, we use fuzz testing, script testing and other methods to test the robustness of interfaces or components by feeding random data or constructing data with a specific structure, and to mine some boundaries. Abnormal behavior of the system under conditions such as bugs or abnormal performance. In the white-box test, we analyze the object definition and logic implementation of the code through methods such as code review, combined with the relevant experience accumulated by the security team on known blockchain security vulnerabilities, to ensure that the key logic and key components in the code are correct. Achieve no known vulnerabilities; at the same time, enter the vulnerability mining mode for new scenarios and new technologies, and find possible 0day errors.

## 3. Vulnerability Severity

The Common Vulnerability Scoring System (CVSS) is an open framework for communicating the characteristics and severity of software vulnerabilities. CVSS consists of three metric groups: Base, Temporal, and Environmental. The Base group represents the intrinsic qualities of a vulnerability that are constant over time and across user environments, the Temporal group reflects the characteristics of a vulnerability that change over time, and the Environmental group represents the characteristics of a vulnerability that are unique to a user's environment. The Base metrics produce a score ranging from 0 to 10, which can then be modified by scoring the Temporal and Environmental metrics. A CVSS score is also represented as a vector string, a compressed textual representation of the values used to derive the score. 

According to the CVSS method, SlowMist team develops the blockchain vulnerability severity level, they are as follows:

| Level      | Description                                                                                                                                                                                                               |
|:----------:| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Critical   | Critical severity vulnerabilities will have a significant impact on the security of the blockchain project, and it is strongly recommended to fix the critical vulnerabilities.                                           |
| High       | High severity vulnerabilities will affect the normal operation of the blockchain project. It is strongly recommended to fix high-risk vulnerabilities.                                                                    |
| Medium     | Medium severity vulnerability will affect the operation of the blockchain project. It is recommended to fix medium-risk vulnerabilities.                                                                                  |
| Low        | Low severity vulnerabilities may affect the operation of the blockchain project in certain scenarios. It is suggested that the project party should evaluate and consider whether these vulnerabilities need to be fixed. |
| Weakness   | There are safety risks theoretically, but it is extremely difficult to reproduce in engineering.                                                                                                                          |
| Suggestion | There are better practices for coding or architecture.                                                                                                                                                                    |
| Infomation | Some features that align with the project design intentions but may lead to user asset loss.                                                                                                                              |

## 4. Public Blockchain Security Research

The SlowMist team's [Blockchain Threat Intelligence](https://bti.slowmist.com/) system continuously tracks ongoing security incidents and applies threat intelligence to its security audit services.

The SlowMist team analyzes and studies publicly known blockchain security vulnerabilities and has compiled a [Blockchain Common Vulnerability List](./Blockchain-Common-Vulnerability-List.md).

## 5. Public Blockchain Security Audit

The SlowMist team employs a comprehensive approach utilizing black-box, gray-box, and white-box testing methods. Depending on the specific audit requirements, they offer various services including a mainnet security audit and layer 2 security audit that primarily use black-box and gray-box methods, and a source code security audit that focuses on white-box testing. Additionally, they provide customized application chain security audit solutions tailored for specific development frameworks.

### 5.1 Layer1 & layer2 mainnet security audits

In layer1 & layer2 project mainnet security audits, the SlowMist team employs a "**black-box + gray-box**" strategy to conduct rapid security testing in a manner that closely simulates real-world attacks.

The vulnerabilities checked by the SlowMist team include:

- Insufficient entropy of private key random numbers
- Precision loss in private key seed conversion
- Theoretical reliability assessment of symmetric encryption algorithms
- Supply chain security of symmetric crypto algorithm reference libraries
- Keystore encryption strength detection
- Hash algorithm length extension attack
- Theoretical reliability assessment of hash algorithms
- Theoretical reliability assessment of signature algorithms
- secp256k1 k-value randomness security
- secp256k1 r-value reuse private key extraction attack
- ECC signature malleability attack
- ed25519 private key extraction attack
- Schnorr private key extraction attack
- ECC twist attack
- Merkle-tree Malleability attack (CVE-2012-2459)
- Native characteristic false recharge
- Contract call-based false recharge
- Native chain transaction replay attack
- Cross-chain transaction replay attack
- Transaction lock attack
- Transaction fees not dynamically adjusted
- RPC remote key theft attack
- RPC port identifiability
- RPC open cross-domain vulnerability to local phishing attacks
- JsonRPC malformed packet denial-of-service attack
- RPC database injection
- RPC communication encryption
- Excessive administrator privileges
- Non-privacy/Non-dark Coin Audit
- Insufficient number of core nodes
- Excessive concentration of core node physical locations
- P2P node maximum connection limit
- P2P node independent IP connection limit
- P2P inbound/outbound connection limit
- P2P shapeshift attack
- P2P communication encryption
- P2P port identifiability
- Consensus algorithm potential risk assessment
- Block time offset attack
- Miner grinding attack
- PoS/BFT double-signing penalty

### 5.2 Source Code Security Audit

Source code security auditing refers to the comprehensive security testing of a project's source code by the SlowMist team using a "**white-box**" strategy. White-box auditing typically involves a combination of automated static code analysis and manual review.

#### 5.2.1 Static Source Code Analysis

The SlowMist team utilizes open-source or commercial code scanning tools for static code analysis and manually examines the identified issues. We support all popular languages, including **C/C++/Golang/Rust/Java/Nodejs/C#**.

The static coding issues checked by the SlowMist team include:

- **Unused Variables or Imports**: Declared but unused variables or imported modules.
- **Code Formatting Issues**: Inconsistent indentation, excessive line length, etc.
- **Improper Resource Closure**: Unclosed resources such as files or database connections.
- **Magic Numbers**: Direct use of numeric constants instead of named constants.
- **Potential Security Vulnerabilities**: Issues like SQL injection, XSS, etc.
- **Integer Overflow**: Unexpected behavior due to calculations exceeding the range of integer types.
- **Floating-Point Precision Issues**: Calculation errors due to the limitations of floating-point representation.
- **Deadlocks**: Threads waiting on each other to release resources, causing a stalemate.
- **Race Conditions**: Program behavior depending on the uncontrolled order of execution in multi-threaded or concurrent environments.
- **Memory Leaks**: Dynamically allocated memory not properly released, leading to increasing memory usage.
- **Infinite Recursion**: Recursive functions lacking proper termination conditions, causing stack overflow.
- **String Formatting Vulnerabilities**: Insecure string formatting leading to potential security issues.
- **Divide-by-Zero Errors**: Failure to check for zero in divisor during division operations.
- **Null Pointer Dereferencing**: Attempting to access memory at the location pointed to by a null pointer.
- **Buffer Overflow**: Writing data exceeding the buffer's capacity, potentially leading to security vulnerabilities.
- **Type Conversion Errors**: Improper type conversions causing data loss or incorrect results.
- **Hard-Coded Keys or Sensitive Information**: Directly embedding keys or sensitive information in code, posing security risks.
- **High Code Complexity**: Long functions or methods, excessive logical branches.
- **Code Duplication**: Identical or similar code blocks appearing in multiple locations.
- **Inconsistent Naming**: Unclear or inconsistent naming of variables, functions, classes, etc.
- **Insufficient or Outdated Comments**: Lack of necessary comments or comments that do not match the code.
- **High Coupling**: Complex interdependencies between modules, making maintenance and expansion difficult.
- **Low Cohesion**: Modules or classes with functions that are not closely related, with unclear responsibilities.
- **Improper Exception Handling**: Catching overly broad exceptions or ignoring exceptions.
- **Hard-Coding**: Using constant values directly in the code instead of configuration parameters.
- **Inconsistent Code Formatting**: Non-uniform use of indentation, spaces, etc.
- **Performance Issues**: Unnecessary loops, frequent object creation, etc.
- **Poor Testability**: Code that is difficult to unit test or integrate test.
- **Violation of Design Principles**: Violations of principles like the Single Responsibility Principle, Open/Closed Principle, etc.
- **Poor Readability**: Confusing code structure, making it difficult to understand.
- **Insecure Random Number Generation**: Using random number generation methods unsuitable for secure purposes.
- **Time and State Issues**: Vulnerabilities like TOCTOU (Time-of-Check to Time-of-Use).
- **Path Traversal**: Failing to properly validate file paths, potentially accessing unauthorized files.
- **Outdated Dependencies**: Use of libraries that are no longer maintained or have known security vulnerabilities.

#### 5.2.2 Manual Code Review

The SlowMist team performs a line-by-line code review to identify coding flaws and logical errors. The vulnerabilities we focus on mainly include:

- Cryptographic signature security
- Account and transaction security
- RPC security
- P2P security
- Consensus security
- Business logic security

### 5.3. Application Chain Security Audit

The SlowMist team adopts the strategy of "**White-box**" to conduct a complete security test on the project, looking for common coding pitfalls as follows:  

- Replay Vulnerability
- Reordering Vulnerability
- Race Conditions Vulnerability
- Authority Control Vulnerability
- Block data Dependence Vulnerability
- Explicit Visibility of Functions
- Arithmetic Accuracy Deviation Vulnerability
- Malicious Event Log
- Asynchronous Call Security

Currently we support:  

1. Cosmos-SDK Framework Based Blockchain Audit  
2. Substrate Framework Based Blockchain Audit  

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

### 7. Open Audit Report
Refer to [Knowledge-Base](https://github.com/slowmist/Knowledge-Base/tree/master/open-report-V2)
