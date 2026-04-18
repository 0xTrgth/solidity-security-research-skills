# Review Flow Example

This file shows a concrete example of how an agent should move through a Solidity smart contract audit from start to finish.

## Scenario

You are given a Solidity codebase for a DeFi protocol.
The protocol contains:
- deposits
- withdrawals
- shares
- admin controls
- signature-based actions
- external token integrations

Your job is to review it carefully and report real findings only.

## Phase 1: System Understanding

First, understand the codebase before making any strong claims.

### Questions to answer
- What does the protocol do?
- Which contracts are core?
- Which contracts hold user assets?
- What are the user-facing entry points?
- What are the admin-facing entry points?
- What roles exist?
- Which modules are accounting-sensitive?
- Which modules depend on signatures?
- Which modules depend on external integrations?
- Is the protocol upgradeable?

### Required output
- protocol purpose
- major contracts
- privilege map
- asset flow map
- key state variables
- key invariants
- trust assumptions

## Phase 2: Attack Surface Mapping

Next, identify where attacks can happen.

### Map all relevant surfaces
- deposit and withdrawal paths
- mint and burn paths
- claim and settlement paths
- liquidation or auction logic
- admin controls
- upgrade paths
- external calls
- signature verification paths
- callback and hook paths

### Required output
- list of user entry points
- list of privileged entry points
- list of value-moving functions
- list of state-machine-sensitive functions
- list of integration-sensitive paths

## Phase 3: Candidate Generation

Now generate concrete vulnerability hypotheses.

### Good examples
- A recipient field is not included in signed intent, so a relayer can redirect funds.
- A vault share calculation can be manipulated through donation before mint.
- A withdrawal loop over attacker-inflatable state can permanently DoS claims.
- An initializer path allows unauthorized setup of privileged parameters.
- An admin revocation flow leaves stale state that permanently blocks replacement.

### Bad examples
- This function looks dangerous.
- Maybe reentrancy exists.
- There might be an issue here.

### Required output for each candidate
- title
- affected components
- suspicious mechanism
- attacker capability
- attack sketch
- possible impact
- why it looks suspicious

## Phase 4: Skeptical Challenge

After generating candidates, challenge them.

### Questions to ask
- Can the attacker actually reach the code path?
- Does access control block the path?
- Does later validation prevent the exploit?
- Is the behavior intended by design?
- Does the issue depend on unrealistic assumptions?
- Is the token behavior standard or malicious?
- Is the impact overstated?
- Is the issue only informational?

### Required output
For each candidate:
- why valid
- why invalid
- mitigating logic
- missing evidence
- final judgment

## Phase 5: Exploitability Verification

For surviving candidates, verify realistic exploit logic.

### Questions to answer
- What exact inputs does the attacker control?
- What state conditions must hold?
- What transaction sequence is required?
- What changes happen during exploitation?
- Why does the protocol fail to stop it?
- What is the realistic consequence?

### Required output
- attack preconditions
- exploit path
- realistic impact
- confidence level

## Phase 6: Final Classification

Classify each issue as:
- Confirmed
- Probably Valid
- Unclear
- Rejected

Only Confirmed issues should appear in the main findings section.

Probably Valid and Unclear issues should go into:
- Unconfirmed Hypotheses

Rejected issues should not appear as final findings.

## Phase 7: Final Audit Output

The final output should contain:

### 1. Protocol Understanding Summary
- what the protocol does
- main contracts
- privilege structure
- asset flow
- trust assumptions

### 2. Attack Surface Summary
- user entry points
- admin entry points
- value-moving paths
- signature-based flows
- integration-sensitive paths
- upgrade/emergency paths

### 3. Confirmed Findings
Each finding should include:
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

### 4. Unconfirmed Hypotheses
Each unconfirmed hypothesis should include:
- Hypothesis
- Why It Looks Suspicious
- Missing Evidence
- What Should Be Tested Next
- Current Confidence

### 5. Highest-Risk Modules
List the modules that deserve the most careful manual review.

### 6. Suggested Next Review Targets
List good next steps for deeper testing.

## Final Reminder

Do not try to maximize finding count.

A correct review with 2 real vulnerabilities is better than a noisy review with 15 weak guesses.