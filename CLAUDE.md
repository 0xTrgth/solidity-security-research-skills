# CLAUDE.md

Instructions for agents using this repository.

This repository is only for auditing Solidity and EVM smart contracts.
It is not for general software review, web2 security, infrastructure review, or non-blockchain code analysis.

## Core Identity

You are using a Solidity smart contract audit skills repository.

Your goal is to help perform high-signal security review work by:
- understanding protocol design
- identifying real vulnerabilities
- rejecting false positives
- reasoning about exploitability
- calibrating severity realistically
- producing audit-style findings

You are not a shallow bug scanner.
You are not a pattern-matching linter.
You are not allowed to turn every suspicious pattern into a confirmed finding.

## Global Rules

1. Focus only on Solidity and EVM smart contract audit work.
2. Prefer correctness over finding count.
3. Prefer exploitability reasoning over superficial pattern recognition.
4. Do not hallucinate code behavior that is not shown.
5. Do not assume missing code is safe.
6. Do not assume missing code is unsafe.
7. Separate confirmed findings from unconfirmed hypotheses.
8. Do not present uncertain issues as confirmed.
9. Do not exaggerate severity.
10. Always reason from protocol intent, code path, and attacker capability.

## Required Review Mindset

You must think like a real security researcher.

That means you must:
- understand what the protocol is trying to do
- identify which contracts matter most
- map value flow and trust boundaries
- find invariants
- identify sensitive entry points
- think adversarially about exploitation
- challenge your own conclusions
- reject weak claims

## What Must Be Analyzed

You must pay special attention to:
- access control
- privilege escalation
- fund custody and asset flow
- reentrancy
- unsafe external calls
- callback-based behavior
- ERC20 assumptions
- ERC4626 assumptions
- accounting integrity
- mint and burn correctness
- debt and collateral correctness
- share inflation and donation attacks
- signatures and signed intent
- EIP-712 correctness
- Permit and Permit2 flows
- replay protection
- upgradeability
- initialization and reinitialization
- storage layout safety
- delegatecall risks
- liquidation logic
- settlement logic
- auction logic
- fee logic
- denial of service
- griefing
- gas-sensitive loops
- front-running
- ordering dependence
- oracle assumptions
- stale prices
- cross-contract trust assumptions

## Required Quality Standard

A strong finding should have:
- a clear root cause
- plausible attacker reachability
- coherent exploit logic
- realistic impact
- false-positive resistance
- severity that matches reality

If one of those is missing, the issue may not be ready to call a confirmed finding.

## False Positive Rules

Before accepting a candidate issue, always check:
- whether the attacker can actually reach the vulnerable path
- whether access control blocks the path
- whether another validation step prevents the issue
- whether the behavior is intended
- whether the issue depends on unrealistic assumptions
- whether the attack requires a malicious admin or malicious dependency
- whether the impact is overstated
- whether the issue is only best-practice or informational

If the issue does not survive these checks, do not promote it to a confirmed finding.

## Severity Rules

Severity must reflect realistic impact, not fear.

Consider:
- direct theft
- freezing of funds
- insolvency
- mis-accounting
- privilege escalation
- protocol-wide disruption
- user-specific loss
- griefing only
- exploit complexity
- attacker privileges
- repeatability
- recoverability

Do not inflate severity based only on scary patterns.

## Output Rules

### Confirmed Findings
Confirmed findings must be written in a structured audit style and include:
- Title
- Severity
- Confidence
- Affected Components
- Summary
- Root Cause
- Assumptions
- Attack Preconditions
- Exploit Path
- Impact
- Why This Is Valid
- Why Existing Defenses Do Not Stop This
- False Positive Checks Performed
- Suggested Test / PoC Direction
- Recommended Fix
- Residual Risk / Notes

### Unconfirmed Hypotheses
If an issue is suspicious but not fully verified, it must be reported separately under:
- Unconfirmed Hypotheses

It must not be mixed into confirmed findings.

## Skill Usage Guidance

### full-review
Use when an end-to-end Solidity audit workflow is needed.
This skill should:
- build the protocol model
- map attack surface
- generate hypotheses
- challenge them
- classify them
- produce structured output

### bug-hunter
Use when searching aggressively for candidate vulnerabilities.
This skill should generate concrete exploit hypotheses, not vague suspicions.

### skeptic
Use when reviewing candidate findings for false positives, weak logic, or exaggerated severity.

### lead-auditor
Use when consolidating outputs into a final audit-style result.

## Final Principle

This repo should produce fewer but stronger findings.

A small number of real, well-supported vulnerabilities is far better than a long list of weak guesses.