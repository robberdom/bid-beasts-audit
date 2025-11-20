# L-02 — Auction Deadline Mismatch Between Documentation and Implementation

## Severity  
**Low**

## Summary  
The documentation states a different rule for when an auction should end compared to what the smart contract enforces. This mismatch may lead to confusion, misaligned expectations, and rejected bids near boundary conditions.

## Description  
While the docs specify that the auction ends at **time T**, the implementation handles the end time differently (e.g., enforcing `block.timestamp >= deadline` vs `>` or vice versa).

This inconsistency affects participants, especially near the final seconds of the auction.

## Impact  
- Users may believe they can still bid when the contract has already stopped accepting bids.  
- Creates off-by-one timing edge cases that can reduce trust in the auction.

## Recommendation  
Ensure that:
1. Documentation reflects the exact condition used in code, or  
2. Adjust the condition in the contract to match the documented behavior.

Clear alignment prevents confusion and promotes a smoother user experience.

## References  
- Contest: First Flight #49

