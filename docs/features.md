## Types of Funds
 
### Investment Funds
Lightweight funds capable of swapping tokens through AMMs with deep liquidity. These funds were coded with an utmost focus on efficieny and the costs to deposit/withdraw and trade are the lowest in the industry. These funds are purpose built for individual traders with good experience in markets who aspire to start a public fund by themselves by showcasing the track record of their performance. They can also be used by DAOs with managing their treasury in a non-custodial manner or by communities to manage funds collectively.


### Defi Hedge Funds
Highly composable funds with capabilities to integrate almost any on-chain protocol. This allows them generate stable yields irrespective of market conditions. Investin's unique architecture integrates custom strategy contracts that utilize multiple on-chain protocols to capture the best possible yields. 


#### Strategies 


The strategy adapter contracts give Investin funds the ability to interact with multiple protocols allowing them to take part in almost all DeFi activities by tokenizing positions. These strategy contracts create positions in various protocols and issue SPL tokens that represent a Fund's share in the respective strategies. All strategy contracts are independent of each other hence failure in one of the integrated protocols is limited to funds participating in affected strategies. We conduct due diligence while selecting protocols to integrate through our strategies but `Investin does not take any responsibility if the integrated protocols are compromised.` 

1. The farming strategies are autocompounded at the cheapest fee in the industry. This is at a fee of 0.1% on yield generated.
2. Users without a fund can also take advantage of auto-compounding farms and other strategies.
3. Custom strategies can be added that generate stable yields with little to no directional downside risk.
4. Margin trading protocols can be integrated allowing Managers to hedge positions in downward markets.


### Selective transfer to vault

This feature enables fund Managers to accept investments from personally whitelisted addresses. This gives Fund Managers the option to follow the KYC/AML guidelines of their country of residence. Fund Managers have the option to accept all investments or be selective about their Investors.


<!-- ### Dynamic performance 

Fund managers can collect the performance fee accrued through investor withdrawals or choose to dynamically collect the impending fee on the live investments exceeding minimum returns regardless of any crystalization period or withdrawals. The dashboard displays the relevant fee collectable by the fund manager. `This amount must be available in the base token denomination of the fund.` This feature incentivizes managers to set short term profitability goals and collect performance fees on meeting the profit targets. This feature compliments investor stop-loss.  -->







**DAO funds, Quant funds, Investor stoploss and limit/stoploss orders coming soon....**
<!-- ### Dao funds (coming soon)


### Quant funds (coming soon)

### Investor stoploss (coming soon)

### Limit/stoploss orders (coming soon) -->


