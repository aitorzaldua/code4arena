## [GAS‑1] abi.encode() is less efficient than abi.encodepacked()

abi.encodePacked() encodes its parameters using the minimal space required by the type.
If you do not need to pad to 32 bytes or if you are not making calls to a contract,
you need to use abi.encodePacked().

### Lines of code:

Contract: https://github.com/code-423n4/2023-04-eigenlayer/blob/main/src/contracts/core/StrategyManager.sol#L150

`150: DOMAIN_SEPARATOR = keccak256(abi.encode(DOMAIN_TYPEHASH, keccak256(bytes("EigenLayer")), ORIGINAL_CHAIN_ID, address(this)));`

`268: bytes32 structHash = keccak256(abi.encode(DEPOSIT_TYPEHASH, strategy, token, amount, nonce, expiry));`

`276: bytes32 domain_separator = keccak256(abi.encode(DOMAIN_TYPEHASH, keccak256(bytes("EigenLayer")), block.chainid, address(this)));`

`879: abi.encode(` Note: the function is returning a byte32 variable.

Contract: https://github.com/code-423n4/2023-04-eigenlayer/blob/main/src/contracts/pods/EigenPodManager.sol

`175: abi.encode(eigenPodBeacon, "")`

`202: abi.encode(eigenPodBeacon, "")`

## [GAS-2] ++i Costs Less Gas Than i++, Especially When It's Used In For-loops (--i/i-- Too)

i++ contains two extra instructions compared to ++i. These two instructions are DUP (3 gas) and POP (2 gas).

### Lines of code:

contract: https://github.com/code-423n4/2023-04-eigenlayer/blob/main/src/contracts/core/StrategyManager.sol

`466: for(uint256 i = 0; i < queuedWithdrawals.length; i++) {`

contract: https://github.com/code-423n4/2023-04-eigenlayer/blob/main/src/contracts/pods/DelayedWithdrawalRouter.sol

`115: for (uint256 i = 0; i < claimableDelayedWithdrawalsLength; i++) {`

contract: https://github.com/code-423n4/2023-04-eigenlayer/blob/main/src/contracts/libraries/Merkle.sol

`137: for (uint i = 0; i < numNodesInLayer; i++) {`

`145: for (uint i = 0; i < numNodesInLayer; i++) {`



