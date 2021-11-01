# Investors

## Overview

We see investors as the main users who provide capital to capable Managers. Their success and satisfaction will determine Investin's future. The protocol shall ensure both types of users are well incentivized to conduct a trustless business relationship and that managers are given access to almost all possible DeFi strategies with the fund assets. Investors are provided with a best-in-class UI with built-in safety standards. Protecting Investor capital is the main priority. 


## Make investment


=== "Solana"

    Investors are required to interact with the Fund program and deposit in the base denomination of the fund. This amount is initially stored in the router vault and an investor account is created to identify each investment. A unique investment receipt corresponding to each individual's investment is also created in this process.

    ```yaml
    FundInstruction::InvestorDeposit { amount }
    ``` 

    The investor receipt allows Investin protocol to provide features like:

    1. Enables investments to be composable and be used as a debt receipt for further use. This includes a flexible performance claim by the Manager on investments that continue to stay active for longer periods.
    2. Investor stoploss i.e. investors can define the percentage of profit or loss at which they wish to withdraw.

=== "EVM"

    Investors are required to interact with the router contract and give approval of the base token with which they would like to invest in any fund. After the approval investors can proceed to call the make investment function which mints an ERC 721 token and send it to the caller's address while transferring the said amount of approved tokens to the router.
    We use a different approach at solving the fund management system by using the ERC 721 standard to identify investors on blockchain.


    ``` yaml
    function makeInvestment(uint amount) external returns(uint256)
    ```

    ### IVNy token

    IVNy is a non-fungible token based on OpenZeppelin's ERC 721 standard. This token is used as a confirmation receipt that all investors shall receive on a successful investment transaction. The token holds no value and is merely used to identify investors of a particular fund. `Beware the loss of access to the address holding IVNy token can result to loss of investment as contracts are hardcoded and only recognize investors through these non-fungible tokens.`

    Advantages of using an NFT: 

    1. Once minted investor can use the same token in the wallet to interact with the protocol at almost 40% less gas expense since the protocol will know details about the investor, token acts as a marker.
    2. ==We plan to integrate lending feature for IVNy NFT holders i.e. investors can borrow by staking their IVNy token as collateral.==
    3. Assets can be added to existing allocation in any fund and partial assets can be withdrawn as well

    


<!-- === "Solidity"
    
    ``` yaml
    function makeInvestment(uint amount) external returns(uint256)
    ```

=== "Solana"
    
    ```yaml
    FundInstruction::InvestorDeposit { amount }
    ``` -->


 

### Performance

The performance on an invested amount is queried on-chain and the smart contracts use on-chain AMM liquidty pool reserves to calculate asset price. Hence, the performance will be subject to an error(+/-2%) but upon ending the investment the price at execution determines the final performance. Blockchain is open by design and any investor can query the fund address to keep tabs on performance.



=== "Solana"
    
    ```yaml
    the fund is a program derived address(PDA) 
    ```

=== "Solidity"
    
    ``` yaml
    function getInvestmentDetails(uint tokenId) external view returns
    (uint128 investedAmount, 
    uint128 startPerformance, 
    uint128 currentPerformance, 
    uint128 currentReturns)
    ```


## End Investment


=== "Solana"

    This instruction can only be called by an Investor's address. In order to achieve the composability of Investin's architecture we handle the withdrawal process in multiple steps. This is to overcome the current limitation of 35 accounts and 200,000 compute limit per transaction.  In each step the specific transaction updates on the investor account(receipt). `There is no lockup period; Investors remain in full control of funds and can deposit/withdraw at their convenience.`

    Example flow:
    
    A Fund having positions in 4 assets that originated from Raydium and 2 margin positions open on Mango markets is handled in the following transactions:
    
    1. The Investor share is calculated on the total fund AUM. The assets owed by fund are accounted in this stage.
    2. The necessary outstanding spot positions in the Fund are settled and sent to the Investor's wallet address
    3. The borrows are settled on both margin positions and according to Investors' share, the positions are closed. It is important to note here that the health of margin account remains same since only the margin amount is changed.
    4. The Investor's share of the margin positions are settled by withdrawing from the Mango account and sending directly to the Investor's address.

=== "Solidity"

    This function can only be called by Investors holding IVNy token and consists of two sub-functions which gives Investors the option to either collect 100% of their investment or make a partial withdrawal to book profits on invested amount.

    The investors have the option to receive their investment according to fund allocation which is the cheapest option to withdraw or they can provide the token in which they would like to get their investment withdrawn from fund.
    `There is no lockup period; Investors remain in full control of funds and can deposit/withdraw at their convenience.`





<!-- === "Solidity"
    
    ``` yaml
    function partialWithdraw(uint _tokenId, uint128 _amount, bool allTokens) external
    ```

=== "Solana"
    
    ```yaml
    FundInstruction::InvestorWithdraw { amount }
    ``` -->

## Fees

* Management fee

    A 2% upfront management fee is deducted on each successful investment out of which 1% is given to the manager who uses the fees to manage expenses of running the fund. This includes transferring tokens to fund contract and transaction cost of trading with AMM LPs. The management fee will not be deducted if the Investor withdraws their investment before the Manager moves tokens from the router vault to their fund contract. 

* Performance fee

    The managers can only collect their performance fee if they reach the minimum return on the individual's investment. This minimum ROI is range bound and can be anywhere between 5-40%. 1/10th of the total fee collected by the Manager is allocated to the protocol. If the manager makes less than the ROI they set, the investors will not be charged any performance fee and can withdraw at any time. This system of reaching a minimum ROI for each investor before being able to collect fees only encourages Managers to continue making strong investment decisions for his Investors.

<!-- === "Solidity"
    
    ``` yaml
    function getFundDetails() external view returns
    (Fund name, 
    manager_address, 
    min_amount, 
    min_return, 
    perf_fee) 
    ```

=== "Solana"
    
    ```yaml
    coming soon 
    ``` -->

## Miscellaneous 

* There is a possibility that an investment made to a fund has not been moved to fund contract by the Manager for an extended period of time. This means the investment will be in an inactive state and no performance made by the relevant fund will be reflected on such investment. The state of investment can be checked through state function or on the Investor dashboard. 
