# CLAUDE.md

Instructions for agents using this repository.

## What This Repo Is

A library of Solidity security research skills for AI agents.

These skills are designed for:
- codebase understanding
- vulnerability hypothesis generation
- false-positive rejection
- exploit verification
- severity assessment
- final audit-style reporting

## Rules

- One skill, one purpose.
- Prefer real, verified findings over quantity.
- Always separate confirmed findings from unconfirmed hypotheses.
- Do not hallucinate unknown behavior.
- Do not report uncertain issues as confirmed.
- Always inspect trust boundaries, privilege boundaries, value flow, and invariants.
- Always challenge a suspected issue before confirming it.