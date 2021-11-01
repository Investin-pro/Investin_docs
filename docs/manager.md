# Managers/Traders

## Overview
Ultimately, the success of running a decentralized fund management protocol is reliant on the managers. Therefore, the goal of Investin is to have the future owners of protocol be the Managers using the protocol.  The protocol has been keenly designed to incentivize traders to become Managers by providing and using their expertise in DeFi to benefit all users of protocol.


## Fund creation

=== "Solana"
    Managers are required to interact with the Investin protocol to create their funds. Unique PDAs are created for each fund that will handle custody of the assets. The cost of creating funds is around ~0.02 Sol which is primarily the rent of the Fund Account to account for the state of the Fund. Only one fund can be created per address.

    ```yaml
    FundInstruction::Initialize { min_amount, min_return, performance_fee_percentage }
    ```


=== "EVM"
    Managers are required to interact with Investin smart contracts to create funds. Since the function call is a interaction with on chain contracts managers are required to pay gas which estimates to around 250,000 gwei. Only one fund can be created per address.
    ``` yaml
    function createFund (uint _minAmount, 
    uint256 _minReturn, uint _performanceFeePercentage) external returns(address)
    ```



At the initialization of a fund the manager is expected to provide certain parameters such as:

* Minimum amount

    This refers to the minimum investable amount that an investor is required to deposit in the fund. The manager can set this according to their criteria of investment strategy to attract their target audience.

* Minimum return

    The manager can set the minimum returns they will be targeting before collecting the performance fee on the positive returns made on AUM. The higher it's set, the better in terms of gaining investors' confidence. This parameter once set cannot be changed and the contract will allow manager to collect their fee only when the minimum return criteria is met. The current minimum is set at a 5% return on investment.

* Performance fee

    The manager needs to set the performance fee they will be collecting when the minimum return is met on each individual investment. The performance fee parameter is range bound to a ceiling of 40% and 1/10th of the total performance fee collected by the Manager is allocated towards Investin. 




## Trading

Investin aims to offer multiple avenues of trading to its Managers to reduce slippage and trading fees thus maximizing users' profits. Currently we offer trading on [Raydium][1], [Orca][2], [Pancake][4], and soon on [Sushi][3].

[1]: https://raydium.io/swap/
[2]: https://orca.so
[3]: https://app.sushi.com/swap
[4]: https://exchange.pancakeswap.finance/#/swap

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

Investin factory contract maintains a whitelist of trading pairs approved for trading through the protocol. This whitelist is updated through community voting.


### Drawdowns

Investin holds the discretionary power to dissolve any fund if the performance of the fund is particularly poor and/or investors are being exploited. This has been included to safeguard investors and promote a healthy community around the protocol. Assets are returned to the corresponding owners.



## Fees

Managers are entitled to collect fees over the investments to ensure longevity in the relationship between them and Investors.

### Management fee

A fixed 1% management fees has been set in the smart contracts which managers can collect when they move the funds from the initial router vault to their fund contracts. This amount is intended to compensate the Manager for the costs borne from transaction fees. This fee can be collected from the Manager Dashboard.

<!-- ### Swap fee

The contract will keep a count of swaps done by the manager and if the fund's performance is above the minimum return set during fund creation, they will be allowed to collect the fees they spent on swapping. `Manager is expected to keep the swap fee in base token of the fund, they won't be able to collect the fee in case the funds are invested in other assets` -->

### Performance fee

As mentioned earlier, the Manager will be able to collect the performance fee on each investment upon fulfilling the minimum return they set for their Fund during the creation process. This feature ensures Managers meet the predefined returns before collecting any performance fee. 1/10th of the total fee collected by the Manager is allocated to the protocol.

!!! info
Manager is expected to keep the performance fee amount available in base denomination of the fund when they wish to claim it. They will not be able to collect the fee in the case that the amount is invested in other assets.

## Staking (revenue sharing)

Details will be added soon...


### Miscellaneous

* We expect Manager's to create a discord/telegram groups for all their investors or ask them to join the relevant discord channel to explain their investment philosophy. They can also add a short thesis on Investin's UI and add links to their socials. 
* To minimize end investment fee incurred on withdrawal by Investors and to create a long-term alliance, Managers are expected to set intervals of redemption by keeping the majority of funds in the base token for ease of withdrawals. 

