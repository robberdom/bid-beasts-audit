# L-01 — First Bid Cannot Equal Minimum Price

## Severity  
**Low**

## Summary  
The auction incorrectly enforces that the **first bid must be strictly greater than `minPrice`**, even though documentation and typical auction behavior state it should allow bids **equal to or greater than** the minimum price.

## Description  
Standard auction mechanics allow the initial bid to match the configured `minPrice`.  
However, in the implementation, the validation logic requires:

firstBid > minPrice

This prevents valid bids equal to `minPrice`, restricting user experience and causing unexpected reverts.

## Impact  
- Users attempting to bid exactly `minPrice` will be unable to participate.  
- Auction parameters become misleading, since `minPrice` isn’t truly the minimum accepted price.

## Recommendation  
Update the condition to:

firstBid >= minPrice

This aligns implementation with documentation and normal auction expectations.

## References  
- Contest: First Flight #49

