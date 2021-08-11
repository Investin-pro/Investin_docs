# Strategies Overview 

## Pancake/Wault swap farms
<!-- These strategies allow depositors to provide liquidity in the token-pair the strategy is deployed and farm cake token by staking the lp tokens in Masterchef tokens. We use Alpha hamora's formula to exactly estimate the position size when adding liquidity to the pool  -->

These strategies add liquidity in the pair defined by strategy contracts and stake lp tokens in Masterchef contract on behalf of  funds/depositors and issue ERC-20 tokens that represent share of each fund/depositor, the assets are handled in a non custodial manner and can be redeemed by token holders, the formula used is illustrated below which estimates exact position sizing when selling tokens to add liquidity in pools.

[^1]$$
\frac{\sqrt{((2−f)⋅resA)^2+4(1−f)(1-h)⋅amtA⋅resA}−(2−f)⋅resA}{2(1-f)(1-h)}  
$$ 

* f = swap fee
* h = protocol fee
* amtA = deposit amount
* resA = pool amount of asset 

[^1]: Improved & derived from https://blog.alphafinance.io/onesideduniswap/



### Deployed strategies for pairs
#### PCS:

BNB/BUSD,
WEX/BNB,
CAKE/BUSD,
CAKE/BNB,
BTCB/BUSD

Stable farms:

USDC/USDT,
USDT/BUSD,
TUSD/BUSD,
AMPL/BUSD

#### Wswap:

WEX,
IVN/BNB,
WEX/BNB,
WEX/USDT,
BTCB/BUSD,
ETH/BUSD, 
BNB/USDC

Stable farms:

USDT/BUSD,
DAI/BUSD



## Belt finance strategy

This strategy allows funds/depositors to stake in belt vaults that lend assets in multiple protocol to enhance yeilds for the staked asset, allowing funds/depositors to have a position in the asset all the while getting a increased yeild by lending asset in multiple protocols. 

#### Deployed vaults
BNB


## Alpha hamora strategy



## Auto farm strategy 