# Bug Bounty


## Program Overview

This bug bounty is specifically for Investin's on-chain program code, UI only bugs are omitted.


|   Severity  |         Description               |     Bug Bounty  | 
|  |  |    |
|Critical |Bugs that freeze user funds or drain the contract's holdings or involve theft of funds without user signatures. | 10% of the value of the hack up to $50,000. | 
| High |Bugs that could temporarily freeze user funds or incorrectly assign value to user funds. |$2,000 to $10,000 per bug, assessed on a case by case basis|
|Medium/Low |Bugs that don't threaten user funds |$500 to $2,000 per bug, assessed on a case by case basis |


The severity guidelines are based on [Immunefi's classification system] [1].

[1]: https://immunefi.com/severity-updated/

Note that these are simply guidelines for the severity of the bugs. Each bug bounty submission will be evaluated on a case-by-case basis

## Bug Bounty Payment
Bug bounties will be paid in USDC or IVN (in rare cases). Investin team has never refused a bug bounty so far.

## Invalid Bug Bounties
The following are out of scope for the bug bounty:

* Attacks that the reporter has already exploite themselves, leading to damage.
* Attacks requiring access to leaked keys/credentials.
* Attacks requiring access to privileged addresses (admin).
* Incorrect data supplied by third party oracles (this does not exclude oracle manipulation/flash loan attacks).
* Lack of liquidity.
* Third party, off-chain bot errors (for instance bugs with an arbitrage bot running on the smart contracts).
* Best practice critiques.
* Sybil attacks.
