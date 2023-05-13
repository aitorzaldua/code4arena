## [G‑23] Functions guaranteed to revert when called by normal users can be marked payable

If a function modifier such as onlyOwner is used, the function will revert if a normal user tries to pay the function. Marking the function as payable will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are CALLVALUE(2),DUP1(3),ISZERO(3),PUSH2(3),JUMPI(10),PUSH1(3),DUP1(3),REVERT(0),JUMPDEST(1),POP(2), which costs an average of about 21 gas per call to the function, in addition to the extra deployment cost

There are 22 instances of this issue:

File: contracts/Comptroller.sol

927:      function addRewardsDistributor(RewardsDistributor _rewardsDistributor) external onlyOwner {

961:      function setPriceOracle(PriceOracle newOracle) external onlyOwner {

973:      function setMaxLoopsLimit(uint256 limit) external onlyOwner {
https://github.com/code-423n4/2023-05-venus/blob/9853f6f4fe906b635e214b22de9f627c6a17ba5b/contracts/Comptroller.sol#L927

File: contracts/Pool/PoolRegistry.sol

188:      function setProtocolShareReserve(address payable protocolShareReserve_) external onlyOwner {

198:      function setShortfallContract(Shortfall shortfall_) external onlyOwner {
https://github.com/code-423n4/2023-05-venus/blob/9853f6f4fe906b635e214b22de9f627c6a17ba5b/contracts/Pool/PoolRegistry.sol#L188

File: contracts/Rewards/RewardsDistributor.sol

125:      function initializeMarket(address vToken) external onlyComptroller {

163       function distributeBorrowerRewardToken(
164           address vToken,
165           address borrower,
166           Exp memory marketBorrowIndex
167:      ) external onlyComptroller {

171:      function updateRewardTokenSupplyIndex(address vToken) external onlyComptroller {

181:      function grantRewardToken(address recipient, uint256 amount) external onlyOwner {

187:      function updateRewardTokenBorrowIndex(address vToken, Exp memory marketBorrowIndex) external onlyComptroller {

219:      function setContributorRewardTokenSpeed(address contributor, uint256 rewardTokenSpeed) external onlyOwner {

233:      function distributeSupplierRewardToken(address vToken, address supplier) external onlyComptroller {

249:      function setMaxLoopsLimit(uint256 limit) external onlyOwner {
https://github.com/code-423n4/2023-05-venus/blob/9853f6f4fe906b635e214b22de9f627c6a17ba5b/contracts/Rewards/RewardsDistributor.sol#L125

File: contracts/RiskFund/ProtocolShareReserve.sol

53:       function setPoolRegistry(address _poolRegistry) external onlyOwner {
https://github.com/code-423n4/2023-05-venus/blob/9853f6f4fe906b635e214b22de9f627c6a17ba5b/contracts/RiskFund/ProtocolShareReserve.sol#L53

File: contracts/RiskFund/RiskFund.sol

99:       function setPoolRegistry(address _poolRegistry) external onlyOwner {

110:      function setShortfallContractAddress(address shortfallContractAddress_) external onlyOwner {

126:      function setPancakeSwapRouter(address pancakeSwapRouter_) external onlyOwner {

205:      function setMaxLoopsLimit(uint256 limit) external onlyOwner {
https://github.com/code-423n4/2023-05-venus/blob/9853f6f4fe906b635e214b22de9f627c6a17ba5b/contracts/RiskFund/RiskFund.sol#L99

File: contracts/Shortfall/Shortfall.sol

348:      function updatePoolRegistry(address _poolRegistry) external onlyOwner {
https://github.com/code-423n4/2023-05-venus/blob/9853f6f4fe906b635e214b22de9f627c6a17ba5b/contracts/Shortfall/Shortfall.sol#L348

File: contracts/VToken.sol

505:      function setProtocolShareReserve(address payable protocolShareReserve_) external onlyOwner {

515:      function setShortfallContract(address shortfall_) external onlyOwner {

1350      function _initialize(
1351          address underlying_,
1352          ComptrollerInterface comptroller_,
1353          InterestRateModel interestRateModel_,
1354          uint256 initialExchangeRateMantissa_,
1355          string memory name_,
1356          string memory symbol_,
1357          uint8 decimals_,
1358          address admin_,
1359          address accessControlManager_,
1360          RiskManagementInit memory riskManagement,
1361          uint256 reserveFactorMantissa_
1362:     ) internal onlyInitializing {
https://github.com/code-423n4/2023-05-venus/blob/9853f6f4fe906b635e214b22de9f627c6a17ba5b/contracts/VToken.sol#L505


## [GAS-2] Constructors can be marked payable
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.