# Solidity Security Research Skills

A skills repository for AI agents that audit Solidity and EVM smart contract codebases.

This repo is focused only on smart contract auditing.
It is not a general security repo, not a web2 pentest repo, and not a generic code review prompt pack.

The goal is to help agents:
- understand the protocol deeply
- find real vulnerabilities
- reject false positives
- verify exploitability carefully
- assess severity realistically
- produce clean audit-style findings

## Supported Usage

Install this skills repository and run a full Solidity smart contract review on the codebase.

Install this skills repository and run the bug hunter on the Solidity contracts.

Install this skills repository and run the skeptic on all candidate findings.

Install this skills repository and run the lead auditor to produce the final audit report.

Update skills to the latest version.

## Core Skills

- full-review
  Runs the complete Solidity audit workflow from architecture understanding to final findings.

- bug-hunter
  Generates concrete vulnerability hypotheses across all Solidity smart contract risk areas.

- skeptic
  Challenges findings, searches for mitigations, and removes false positives.

- lead-auditor
  Consolidates results, deduplicates findings, calibrates severity, and produces the final structured report.

## Review Philosophy

These skills must behave like a real smart contract auditor, not a shallow bug scanner.

That means:
- understanding protocol design before making conclusions
- reasoning about trust boundaries and asset flow
- identifying invariants and sensitive state transitions
- forming concrete exploit hypotheses
- challenging those hypotheses
- verifying realistic exploitability
- separating confirmed findings from unconfirmed hypotheses
- preferring a few strong findings over many weak guesses

## What Agents Should Analyze

Agents using this repo should carefully inspect:
- access control and privilege boundaries
- asset flow and custody
- protocol phases and state transitions
- accounting and invariant safety
- reentrancy and external call ordering
- ERC20, ERC721, ERC1155, ERC4626, and token integration assumptions
- signatures, EIP-712, Permit, Permit2, and replay protection
- upgradeability, initialization, and storage layout risks
- oracle dependencies and freshness assumptions
- liquidation, settlement, auction, and fee logic
- denial of service, griefing, and gas-based failure modes
- front-running, ordering dependence, and MEV-sensitive flows
- cross-contract trust assumptions and integration risks

## Severity Levels

Agents should report issues across all severities:
- Critical
- High
- Medium
- Low
- Informational

Severity must be based on realistic impact and exploitability, not exaggerated pattern matching.

## Output Standards

Confirmed findings must include:
- title
- severity
- confidence
- affected components
- summary
- root cause
- preconditions
- exploit path
- realistic impact
- why the finding is valid
- false-positive checks performed
- recommended fix

Uncertain issues must not be presented as confirmed findings.
They must be placed under:
- Unconfirmed Hypotheses

## Goal

Prefer fewer, stronger, carefully verified findings over many weak guesses.