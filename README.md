# Solidity Security Agent Prompts

A prompt pack for AI agents that help review Solidity smart contract codebases.

## Purpose

This repository contains structured prompts for multi-agent smart contract security review workflows.  
The goal is to help agents:

- understand protocol architecture
- analyze trust boundaries
- identify vulnerabilities from Critical to Informational
- debate and reject false positives
- verify exploitability carefully
- produce structured findings

## Included Agents

- Master Auditor
- Lead Auditor
- Architecture Agent
- Bug Hunter Agent
- Skeptic Agent
- Exploit Verifier Agent
- Severity Agent

## Repo Structure

- `prompts/` → core agent prompts
- `templates/` → finding/report templates
- `examples/` → example usage
- `SYSTEM.md` → shared system-level instructions

## Usage

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/solidity-security-agent-prompts.git
cd solidity-security-agent-prompts
