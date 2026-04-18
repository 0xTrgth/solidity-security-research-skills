# Solidity Audit Review Checklist

## Architecture
- What does the protocol do?
- Which contracts are core?
- Which contracts hold assets?
- Which roles are privileged?
- Which external integrations are trusted?

## Access Control
- Are privileged functions correctly restricted?
- Can users bypass role checks?
- Are admin powers broader than intended?
- Are critical operations protected?

## Asset Flow
- How do assets enter the system?
- How do assets move internally?
- How do assets leave the system?
- Can assets be trapped, redirected, inflated, or frozen?

## Invariants
- Can total assets and total shares diverge?
- Can debt exceed collateral?
- Can balances become inconsistent?
- Can allocations or reserves become impossible to satisfy?

## Reentrancy and External Calls
- Are external calls made before state updates?
- Can callbacks reenter sensitive flows?
- Are token transfers or hooks able to break assumptions?

## Token Assumptions
- Does the protocol assume standard ERC20 behavior?
- What happens with fee-on-transfer tokens?
- What happens with rebasing tokens?
- What happens with malicious tokens?
- Are decimals handled safely?

## Signatures
- Are all critical fields included in the signed data?
- Is nonce handling correct?
- Is deadline handling correct?
- Is chain/domain separation correct?
- Is replay possible?
- Are Permit / Permit2 flows binding complete intent?

## Accounting
- Are mint, burn, deposit, withdraw, claim, and settlement paths consistent?
- Can rounding create extraction opportunities?
- Can donation or inflation attacks occur?
- Can accounting drift over time?

## Upgradeability
- Is initialization protected?
- Are reinitializers safe?
- Is storage layout stable?
- Can implementation state be abused?
- Are admin upgrade powers safe?

## Protocol Logic
- Are phase transitions enforced correctly?
- Can actions be performed in the wrong phase?
- Can settlement, auction, claim, or liquidation logic be bypassed?
- Can emergency actions leave the system stuck?

## Liveness / DoS
- Are there unbounded loops?
- Can attackers create gas-heavy state?
- Can claims, withdrawals, or settlement be blocked permanently?
- Can griefing make core functionality unusable?

## Oracle / Pricing
- Is oracle freshness checked?
- Can pricing be manipulated?
- Are decimals and scaling handled correctly?
- Can stale or bad data create insolvency or unfair execution?

## Severity Calibration
- Is there direct theft?
- Is there freezing of funds?
- Is there protocol-wide disruption?
- Is the issue only griefing?
- Is the attacker privileged?
- Is the severity realistic?