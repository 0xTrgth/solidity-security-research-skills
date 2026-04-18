# Usage Example

This file shows how to use the Solidity audit skills in a practical review workflow.

## Main Goal

Use the skills in this repository to review a Solidity smart contract codebase carefully, reduce false positives, and produce structured audit findings.

## Recommended Skill Order

1. full-review
2. bug-hunter
3. skeptic
4. lead-auditor

This order works well because:
- full-review builds the system understanding
- bug-hunter generates concrete candidate issues
- skeptic filters weak claims
- lead-auditor produces the final clean report

## Example Natural-Language Commands

Install this skills repository and run a full Solidity smart contract review on the codebase.

Install this skills repository and run the bug hunter on the Solidity contracts.

Install this skills repository and run the skeptic on all candidate findings.

Install this skills repository and run the lead auditor to produce the final audit report.

Update skills to the latest version.

## Example Usage Pattern

### Step 1: Run Full Review
Purpose:
- understand the protocol before hunting bugs
- identify critical contracts and attack surfaces
- define key invariants
- get an initial review baseline

Expected output:
- protocol understanding summary
- trust model
- privilege map
- asset flow summary
- attack surface summary
- initial confirmed findings
- initial unconfirmed hypotheses

### Step 2: Run Bug Hunter
Purpose:
- aggressively search for vulnerability candidates
- inspect sensitive functions and modules
- produce exploit hypotheses with attacker logic

Expected output:
- candidate finding titles
- affected functions and contracts
- suspicious mechanism
- attacker capability
- attack sketch
- possible consequence
- initial severity guess

### Step 3: Run Skeptic
Purpose:
- challenge all candidate findings
- remove false positives
- reduce severity inflation
- identify missing evidence

Expected output:
- why the candidate may be valid
- why it may be invalid
- mitigating logic found
- missing evidence
- remaining risk
- final judgment:
  - strengthened
  - weakened
  - rejected

### Step 4: Run Lead Auditor
Purpose:
- consolidate surviving findings
- remove duplicates
- calibrate severity
- produce professional output

Expected output:
- protocol summary
- attack surface summary
- confirmed findings
- unconfirmed hypotheses
- highest-risk modules
- next review targets

## Good Review Habits

- Start with understanding, not bug hunting.
- Do not trust surface-level patterns.
- Track fund flow carefully.
- Check privilege boundaries early.
- Check signed intent carefully.
- Check accounting invariants repeatedly.
- Challenge every serious finding before accepting it.
- Keep unconfirmed issues separate from confirmed ones.

## Recommended Review Priorities

When time is limited, prioritize:
1. asset-moving functions
2. privileged functions
3. signature-based flows
4. settlement / claim / liquidation / auction logic
5. upgradeability and initializer logic
6. accounting-heavy paths
7. external integrations and token assumptions

## Important Rule

Do not judge review quality by the number of findings.
Judge it by:
- correctness
- exploitability depth
- false-positive resistance
- clarity of reporting