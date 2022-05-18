# Blockchain Based Cryptocurrency Security Audit Guide

[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/slowmist_team.svg?style=social&label=Follow%20%40SlowMist_Team)](https://twitter.com/slowmist_team)

## Cryptocurrency Threat Modeling

SlowMist uses multiple models to identify cryptocurrency threats.

**The [ABC](https://arxiv.org/abs/1903.03422)** (Asset-Based Cryptocurrency-focused) threat modeling framework:

ABC's key innovation is the use of collusion matrices. A collusion matrix forces a threat model to cover a large space of threat cases while simultaneously manages this process to prevent it from being overly complex. Moreover, ABC derives a system-specific threat categories that account for the financial aspects and the new asset types that cryptocurrencies introduce. 

**STRIDE** threat model:

STRIDE is often used in relation to assessing threats against applications or operating systems. However, it can also be used in other contexts as well. STRIDE is an acronym standing for the following: Spoofing/Tampering/Repudiation/Information disclosure/Denial of service (DoS)/Elevation of privilege.

## Testing Method
The testing methods are as follows:

| Test Method | Description |
| :---: | --- |
| Black-box testing | Black-box testing examines the program from a user perspective by providing a wide variety of input scenarios and inspecting the output. Black-box testers do not have access to the internal code. Final acceptance testing that occurs prior to system delivery is a common example of black-box testing. |
| Gray-box testing | Gray-box testing combines the two approaches and is popular for software validation. In this approach, testers examine the software from a user perspective, analyzing inputs and outputs. They also have access to the source code and use it to help design their tests. They do not, however, analyze the inner workings of the program during their testing. |
| White-box testing | White-box testing examines the internal logical structures of a program and steps through the code line by line, analyzing the program for potential errors. |

In black-box testing and gray-box testing, we use fuzz testing, script testing and other methods to test the robustness of interfaces or components by feeding random data or constructing data with a specific structure, and to mine some boundaries. Abnormal behavior of the system under conditions such as bugs or abnormal performance. In the white-box test, we analyze the object definition and logic implementation of the code through methods such as code review, combined with the relevant experience accumulated by the security team on known blockchain security vulnerabilities, to ensure that the key logic and key components in the code are correct. Achieve no known vulnerabilities; at the same time, enter the vulnerability mining mode for new scenarios and new technologies, and find possible 0day errors.

## Vulnerability Severity
The Common Vulnerability Scoring System (CVSS) is an open framework for communicating the characteristics and severity of software vulnerabilities. CVSS consists of three metric groups: Base, Temporal, and Environmental. The Base group represents the intrinsic qualities of a vulnerability that are constant over time and across user environments, the Temporal group reflects the characteristics of a vulnerability that change over time, and the Environmental group represents the characteristics of a vulnerability that are unique to a user's environment. The Base metrics produce a score ranging from 0 to 10, which can then be modified by scoring the Temporal and Environmental metrics. A CVSS score is also represented as a vector string, a compressed textual representation of the values used to derive the score. 

According to the CVSS method, SlowMist team develops the blockchain vulnerability severity level, they are as follows:

| Level | Description |
| :---: | --- |
| Critical | Critical severity vulnerabilities will have a significant impact on the security of the blockchain project, and it is strongly recommended to fix the critical vulnerabilities. |
| High | High severity vulnerabilities will affect the normal operation of the blockchain project. It is strongly recommended to fix high-risk vulnerabilities. |
| Medium | Medium severity vulnerability will affect the operation of the blockchain project. It is recommended to fix medium-risk vulnerabilities. |
| Low | Low severity vulnerabilities may affect the operation of the blockchain project in certain scenarios. It is suggested that the project party should evaluate and consider whether these vulnerabilities need to be fixed. |
| Weakness | There are safety risks theoretically, but it is extremely difficult to reproduce in engineering. |
| Suggestion | There are better practices for coding or architecture. |

## Blockchain Mainnet Security Audit

The SlowMist team adopts the strategy of "**Black-box + Gray-box**" to conduct a complete security test on the project in the way closest to the real attack.

The SlowMist team check all vulnerabilities listing  in [SlowMist: Blockchain Common Vulnerability List](./Blockchain-Common-Vulnerability-List.md) (30+ items)

## Cryptocurrency Exchange Listing Security Audit

The SlowMist team adopts the strategy of "**Black-box + Gray-box**" to conduct a complete security test on the project in the way closest to the real attack.

The SlowMist team examines the most concerned vulnerabilities of exchanges, they are as follows:

- Private key prediction
  [Detail](./Blockchain-Common-Vulnerability-List.md#private-key-prediction)

- Rug pull attack
  [Detail](./Blockchain-Common-Vulnerability-List.md#rug-pull-attack)

- Insecure encryption library
  [Detail](./Blockchain-Common-Vulnerability-List.md#cryptographic-attacks)

- Transaction malleability attack
  [Detail](./Blockchain-Common-Vulnerability-List.md#transaction-malleability-attack)

- Transaction replay attack
  [Detail](./Blockchain-Common-Vulnerability-List.md#transaction-replay-attack)

- False top-up attack
  [Detail](./Blockchain-Common-Vulnerability-List.md#false-top-up-attack)

- RPC theft
  [Detail](./Blockchain-Common-Vulnerability-List.md#the-ethereum-black-valentines-day-vulnerability)

## Code-based Testing Audit

The SlowMist team adopts the strategy of "**White-box**" to conduct a complete security test on the project.

### Static Source Code Analysis (SAST)
The SlowMist team checks code quality using open source or commercial code scanners, we support all popular language, such as **C/C++/Golang/Rust/Java/Nodejs/C#**

### Manual Code Review

The SlowMist team manually checks the code line by line, looking for common coding pitfalls as follows:  

- State consistency
- Fail rollback
- Numerical overflow
- Parameter verification
- Error handle
- Boundary check
- Unit test coverage

## Application Chain Security Audit

The SlowMist team adopts the strategy of "**White-box**" to conduct a complete security test on the project, looking for common coding pitfalls as follows:  

- Replay Vulnerability
- Reordering Vulnerability
- Race Conditions Vulnerability
- Authority Control Vulnerability
- Block data Dependence Vulnerability
- Explicit Visibility of Functions
- Arithmetic Accuracy Deviation Vulnerability
- Malicious Event Log

Currently we support:  
1. Cosmos-SDK Framework Based Blockchain Audit  
2. Substrate Framework Based Blockchain Audit  


## Blockchain Application Audit
### Smart Contract Security Audit
1. [Ethereum(Solidity) Smart Contract Security Audit](https://www.slowmist.com/en/service-smart-contract-security-audit.html)
2. [EOS(C++) Smart Contract Security Best Practices](https://github.com/slowmist/eos-smart-contract-security-best-practices)
3. Solana(Rust) Smart Contract Security Best Practices

### Other Application
1. Zero-Knowledge Circuit Security Audit  
2. Interchain Bridge Application Security Audit  
3. Browser Plugin Wallet Security Audit  
4. Exchange Security Audit 
