# Gravis Finance Gswap Farming Big Bang Round
This contract was created for farming BigBang round buyers.

URL farming BigBang round: https://nftfarming.gravis.finance/?network=56
Contract Gswap Farming BigBang Round: https://bscscan.com/address/0x6af334b742d51799f600992f967d2edbbafecce6

Contract Collectible BigBang: https://bscscan.com/address/0x155e2ab16d5eb9269ec526baa66b32bc5ce0f58a


### Gswap Farming Big Bang Round

#### Deployment

To deploy the contract you need to provide following params:

1. Reward token address, should be ERC20 token.
2. Token provider address, this is regular Ethereum/BSC address, which has sufficient Reward token balace and correctly set allowance to Deployed contract address.
3. Array of GravisCollectible contract addresses. There are 3 pools set up on contract deployment, each of could use separate GravisCollectible instance. This instance should have `transferFor` method.
4. Each pool inside contract, has `id` param, which represents token type of GravisCollectible NFT contract.
5. For testing purpose or when deploying to testnet, it is advisable to change `uint256 constant SPEED_INCREASE_PERIOD = 10 days;` to lower value, as this variable represents farming speed increase interval.

#### Deposit

Users can deposit NFT by using `deposit` method, with following params:

- poolId `[0,1,2]` where:
  0 - Believer Pool
  1 - Advocate Pool
  2 - Evangelist Pool
- amount of NFT tokens to deposit

#### Claim

Users can claim Reward token by using `claimRewards` method, with following param:

- poolId `[0,1,2]` where:
  0 - Believer Pool
  1 - Advocate Pool
  2 - Evangelist Pool



#### Contracts deployment cost

```
·-----------------------------------------------|---------------------------|-------------|-----------------------------·
|             Solc version: 0.6.12              ·  Optimizer enabled: true  ·  Runs: 200  ·  Block limit: 12450000 gas  │
················································|···························|·············|······························
|  Methods                                      ·              100 gwei/gas               ·       1877.38 usd/eth       │
······················|·························|·············|·············|·············|···············|··············
|  Contract           ·  Method                 ·  Min        ·  Max        ·  Avg        ·  # calls      ·  usd (avg)  │ │
······················|·························|·············|·············|·············|···············|··············
|  GravisMaster       ·  allowClaim             ·          -  ·          -  ·      28498  ·           34  ·       5.35  │
······················|·························|·············|·············|·············|···············|··············
|  GravisMaster       ·  claimRewards           ·     103702  ·     167264  ·     149625  ·           75  ·      28.09  │
······················|·························|·············|·············|·············|···············|··············
|  GravisMaster       ·  deposit                ·     143827  ·     197836  ·     188610  ·           47  ·      35.41  │
······················|·························|·············|·············|·············|···············|··············
|  GravisMaster       ·  pause                  ·          -  ·          -  ·      28001  ·            4  ·       5.26  │
······················|·························|·············|·············|·············|···············|··············
|  GravisMaster       ·  setBonusDeadlineTime   ·          -  ·          -  ·      45631  ·            9  ·       8.57  │
······················|·························|·············|·············|·············|···············|··············
|  GravisMaster       ·  unpause                ·          -  ·          -  ·      28005  ·            2  ·       5.26  │
······················|·························|·············|·············|·············|···············|··············
|  Deployments                                  ·                                         ·  % of limit   ·
│
················································|·············|·············|·············|···············|··············
················································|·············|·············|·············|···············|··············
|  GravisMaster                                 ·    2713125  ·    2713149  ·    2713148  ·       21.8 %  ·     509.36  │
················································|·············|·············|·············|···············|··············
·-----------------------------------------------|-------------|-------------|-------------|---------------|-------------·
```

#### Test coverage report

```
-------------------------|----------|----------|----------|----------|----------------|
File                     |  % Stmts | % Branch |  % Funcs |  % Lines |Uncovered Lines |
-------------------------|----------|----------|----------|----------|----------------|
 contracts/              |    99.21 |    95.16 |      100 |    99.19 |                |
  GravisMaster.sol       |    99.21 |    95.16 |      100 |    99.19 |            365 |
 contracts/interfaces/   |      100 |      100 |      100 |      100 |                |
  IGravisCollectible.sol |      100 |      100 |      100 |      100 |                |
-------------------------|----------|----------|----------|----------|----------------|
All files                |    99.21 |    96.62 |      100 |      100 |                |
-------------------------|----------|----------|----------|----------|----------------|
```

#### Deploy GravisMaster

```
yarn deploy --network bsctest --tags Master

yarn verify --network bsctest 0x... --constructor-args src/002_arguments.js
yarn verify --network bsctest 0x25dBEEad8A106deD522831E11bEf339141D9aa94 --constructor-args src/002_arguments.js
```

```
yarn deploy --network bsc --tags Master

yarn verify --network bsc 0x6aF334B742d51799F600992f967d2edBbAFeCCE6 --constructor-args src/002_arguments.js
```
