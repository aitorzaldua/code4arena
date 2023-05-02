## [GAS‑1] abi.encode() is less efficient than abi.encodepacked()

abi.encodePacked() encodes its parameters using the minimal space required by the type.
If you do not need to pad to 32 bytes or if you are not making calls to a contract,
you need to use abi.encodePacked().

### Lines of code:

Contract: https://github.com/code-423n4/2023-04-eigenlayer/blob/main/src/contracts/core/StrategyManager.sol#L150

`150: DOMAIN_SEPARATOR = keccak256(abi.encode(DOMAIN_TYPEHASH, keccak256(bytes("EigenLayer")), ORIGINAL_CHAIN_ID, address(this)));`

`268: bytes32 structHash = keccak256(abi.encode(DEPOSIT_TYPEHASH, strategy, token, amount, nonce, expiry));`

`276: bytes32 domain_separator = keccak256(abi.encode(DOMAIN_TYPEHASH, keccak256(bytes("EigenLayer")), block.chainid, address(this)));`

