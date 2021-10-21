# Managers/Traders

## Overview
The future owners of protocol on whose success the experiment of running a decentralized fund management protocol can be made possible in a truly trustless and non custodial way. The protocol has been keenly designed to incentivize traders who provide their expertise in DeFi to benefit both the users of protocol.



## Fund creation

=== "Solana"
    Managers are required to interact with the Investin Program to create funds. Unique PDAs are created for each fund that will handle custody of the assets. The cost of creating funds is around ~0.02 Sol which is primarily the rent of the Fund Account to account for the state of the Fund. Only one fund can be created per address.

    ```yaml
    FundInstruction::Initialize { min_amount, min_return, performance_fee_percentage }
    ```


=== "EVM"
    Managers are required to interact with Investin smart contracts to create funds. Since the function call is a interaction with on chain contracts managers are required to pay gas which estimates to around 250,000 gwei. Only one fund can be created per address.
    ``` yaml
    function createFund (uint _minAmount, 
    uint256 _minReturn, uint _performanceFeePercentage) external returns(address)
    ```



As the intialization function call can be seen above the manager is expected to provide certain paramters like:


* Minimum amount

    This refers to the minimum investable amount that an investor is required to deposit in the fund. The manager can set this according to their criteria of investment strategy to attract their target audience.

* Minimum return

    The manager can set the minimum returns they will be targetting before collecting the performance fee on the profitable returns made on the fund. The higher its set, the better in terms of gaining investors' confidence. This paramater once set cannot be changed and the contract will allow manager to collect their fee only when the minimum return criteria is met. The current value is set to be a minimum of 5% return on invesment.

* Performance fee

    The manager needs to set the performance fee they will be collecting when the minimum return set by them is met on each investment independently. The performance fee parameter is range bound to a ceiling of 40% and 1/10th of the total fee collected by the Manager is allocated to the protocol.








## Trading

Investin aims to offer multiple avenues of trading to its managers/traders and is always looking forward at making the cost of trading bare minimum to maximize trader's profits. Currently we offer trading on [pancakeswap][1] and [raydium][2] soon on [sushiswap][3]

[1]: https://exchange.pancakeswap.finance/#/swap
[2]: hhttps://raydium.io/swap/
[3]: https://app.sushi.com/swap

### Swap 


=== "Solana"
    
    ```yaml
    FundInstruction::Swap { instr, amount_in, min_amount_out}
    ```
=== "EVM"
    
    ``` yaml
    function swap (address tokenIn, address tokenOut, uint amountIn) 
    public returns (uint[] memory _amounts)

    ```
 
    

### Trading pairs

Investin factory contract maintains a whitelist of trading pairs approved for trading through the protocol. This whitelist can be updated through community voting.


### Drawdowns

Investin holds the discretionary power to dissolve any fund if the performance of any fund is very poor and investors are being rugged. This has been included to safeguard investors and promote a healthy community around the protocol.



## Fees

Manager are entitled to collect fees over the investments to insure longetivity in relations between them and investors

### Management fee

A fixed 1% management fees has been set in the smart contracts which managers can collect when they move the funds from router to their fund contracts. This amount is intended to incentivise the Manager for the costs borne for transaction fees and can be collected from the Manager Dashboard. 

<!-- ### Swap fee

The contract will keep a count of swaps done by the manager and if the fund's performance is above the minimum return set during fund creation they will be allowed to collect the fee they spent on swapping. `Manager is expected to keep the swap fee in base token of the fund, they won't be able to collect the fee in case the funds are invested in other assets` -->

### Performance fee

As discussed earlier manager will be entitiled to collect the performance fee on each investment upon fulfiling the minimum return they set for their Fund during the creation process. This feature ensures managers meet the predefined returns before collecting any performance fee. 1/10th of the total fee collected by the Manager is allocated to the protocol.

!!! info
    Manager is expected to keep the performance fee amount available in base denomination of the fund when they wish to claim it, they wont be able to collect the fee in case the amount is invested in other assets


## Staking (revenue sharing)

Details will be added soon..


### Miscellaneous

* We expect manager's to create a discord/telegram groups for all their investors or ask them to join the relevant discord channel to explain their investment philosophy, they can also add a short thesis on investin's UI and add their socials link. 
* To minimize end investment fee incurred on withdrawal by investors and to create a long term alliance, managers are expected to set intervals of redemption by keeping the majority of funds in base token for ease of withdrawals. 

