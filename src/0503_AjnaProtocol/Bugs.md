## [GAS-1] Avoid emitting constants.

### Description

The constants are unnecessary to emit since the value will never change. Each element of an event/emit has a cost of 375 gas.
Reference: https://solodit.xyz/issues/8898

### Lines of code:

Contract: https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol

`683 to 689: emit VoteCast(account_,proposalId,support,incrementalVotesUsed_,"");`

`746 to 752: emit VoteCast(account_, proposalId, 1, votes_,"");`

### Recomendation:

Remove the constants => 1 and ""


## [LOW-1] Different pragma directives are used

### Description

Multiple Solidity pragma: It is better to use one Solidity compiler version across all contracts instead of different versions with different bugs and security checks.

In this case, there are 2 mixed versions, 0.8.14 and 0.8.16

### Contracts with version 0.8.14:

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol

### Contracts with version 0.8.16:

All except the 2 mentioned above.

### Recomendation:

Set all contracts to the same version, ideally the higher version, and test and deploy with it.



