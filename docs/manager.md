# Managers/Traders

## Overview
The future owners of protocol on whose success the experiment of running a decentralized fund management protocol can be made possible in a truly trustless and non custodial way. The protocol has been keenly designed to incentivize traders who provide their expertise on crypto markets to benefit both the users of protocol.



## Fund creation

Managers are required to interact with Investin smart contracts to create funds. Since the function call is a interaction with on chain contracts managers are required to pay gas which estimates to around 500,000 gwei
=== "Layer 1"
    
    ``` yaml
    function createFund (string calldata _fundName, uint _minAmount, 
    uint256 _minReturn, uint _performanceFeePercentage) external returns(address)
    ```

=== "Layer 2"
    
    ```yaml
    comming soon on a rollup near you
    ```

As the intialization function call can be seen above the manager is expected to provide certain paramters as:

* Fund name 

    The name of the fund which acts the identifier of the fund and can only be set during intialization of fund, choose wisely and a attractive name that sets the fund apart from others.

* Minimum amount

    This refers to minimum investable amount that an investor can invest in the fund. The manager can set this according to their criteria of investment strategy to attract their niche level of investors.

* Minimum return

    The manager can set the minimum returns they will be targetting before collecting the performance fee on the profits made on the fund. The higher its set the better. This paramater once set cannot be changed and the contract will allow manager to collect there fee only when the minimum return criteria is met. The current range bound set is from 5-50% return on invesment

* Performance fee

    The manager needs to set the performance fee they will be collecting when the minimum return set by them is met on total assets under management. The performance fee parameter is range bound and can be set in 5-50% range.








## Trading

Investin aims to offer multiple avenues of trading to its managers/traders and is always looking forward at making the cost of trading bare minimum to maximize trader's profits. Currently we offer trading on [uniswap][1] and [pancakeswap][2] 

[1]: https://pages.github.com/
[2]: https://pages.github.com/

### Swap 

=== "Layer 1"
    
    ``` yaml
    function swap (address tokenIn, address tokenOut, uint amountIn) 
    public returns (uint[] memory _amounts)

    ```

=== "Layer 2"
    
    ```yaml
    comming soon on a rollup near you
    ```
 
    
The swap functions on investin does not require approvals since the amm contract is inherited and the call will be between contract accounts. 

### Trading pairs

Investin factory contract will maintain a whitelist of trading pairs approved for trading through the protocol. This whitelist can be updated through community voting.


### Drawdowns

Investin holds the discretionary power to dissolve any fund if the performance of any fund is very poor and investors are being rugged. This has been included to safeguard investors and promote a healthy community around the protocol.



## Fees

Manager are entitled to collect fees over the investments to insure longetivity in relations between them and investors

### Management fee

A fixed 1.5% management fees has been set in the smart contracts which managers can collect when they move the funds from router to their fund contracts. This amount will be shown on manager dashboard interface. 

### Performance fee

As discussed earlier manager will be entitiled to collect the performance fee on meeting the criteria they reach the minimum return they set for themselves during deploying funds. This feature insures managers meet certain targets of profits before collecting any performance fee.

