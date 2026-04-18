# Invariants Template

Use this template to identify the conditions that should always remain true in a Solidity protocol.

The goal is to force explicit reasoning about accounting safety, authorization boundaries, lifecycle correctness, and value conservation.

## 1. Protocol Context

### Protocol Name
-

### Main Purpose
-

### Core Contracts
-
-
-

### Main Assets
-
-
-

### Important Roles
-
-
-

## 2. Asset Conservation Invariants

These invariants check whether assets can be created, lost, trapped, misrouted, or double-counted.

### Invariant A
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

### Invariant B
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

Examples:
- Total credited user balances should never exceed total assets actually controlled by the protocol.
- Total claimable rewards should never exceed funded rewards.
- Total redeemable shares should remain consistent with total managed assets under intended accounting rules.

## 3. Supply / Share / Debt Invariants

These invariants check consistency between minted assets, burned assets, shares, collateral, reserves, and debt.

### Invariant A
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

### Invariant B
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

Examples:
- Total shares should track the intended ownership claim over assets.
- Debt should never exceed allowed collateralization thresholds under intended protocol rules.
- Burned supply should no longer remain claimable or spendable.

## 4. Authorization Invariants

These invariants check whether only the right actors can perform sensitive actions.

### Invariant A
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

### Invariant B
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

Examples:
- Only authorized roles may upgrade implementations.
- Only the intended signer may authorize signature-based execution.
- Users must not be able to perform admin-only settlement or emergency actions.

## 5. Lifecycle / State-Machine Invariants

These invariants check whether the protocol’s phases and transitions remain valid.

### Invariant A
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

### Invariant B
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

Examples:
- Claims should only be possible after settlement is finalized.
- Cancellation should prevent further participation.
- Finalized rounds should not return to an active state.

## 6. Signature / Replay Invariants

These invariants check whether signed actions are bound tightly enough to user intent.

### Invariant A
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

### Invariant B
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

Examples:
- All security-critical routing fields should be bound into the signed message.
- A nonce should not be reusable once consumed.
- A signature scoped to one chain or contract should not be replayable elsewhere.

## 7. Integration Invariants

These invariants check assumptions about tokens, oracles, wrappers, routers, bridges, and callbacks.

### Invariant A
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

### Invariant B
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

Examples:
- Accounting should remain correct even when token transfers do not behave exactly as assumed, if such tokens are supported.
- Oracle-dependent actions should not proceed using stale or invalid prices.
- External callbacks should not violate internal accounting assumptions.

## 8. Liveness / DoS Invariants

These invariants check whether the protocol remains usable and core flows remain possible.

### Invariant A
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

### Invariant B
- Statement:
- Why it should always hold:
- Relevant contracts/functions:
- What could break it:
- Notes for testing:

Examples:
- Users should remain able to withdraw under normal protocol conditions.
- Claims should not become permanently blocked by attacker-inflated state.
- Settlement should not become impossible due to unbounded loops over user-controlled data.

## 9. Highest-Priority Invariants

List the invariants that deserve the strongest manual and test-based verification.

### Top Invariant 1
- Statement:
- Why high priority:
- Suggested test direction:

### Top Invariant 2
- Statement:
- Why high priority:
- Suggested test direction:

### Top Invariant 3
- Statement:
- Why high priority:
- Suggested test direction:

## 10. Notes for Audit Follow-Up

- Which invariants look hardest to verify?
- Which invariants depend on external integrations?
- Which invariants are most likely to hide High or Critical bugs?
- Which invariants should be turned into property tests or invariant tests first?