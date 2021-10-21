# Investors

## Overview

We see investors as key liquidity providers of the platform whose success and satisfaction will determine Investin's future. The protocol shall ensure both the users are well incentivized to conduct a trustless exchange of offerings, while managers are given access to almost all possible market activities with the fund assets. Investors are provided with best in class UI with safety standards built-in to protect capital being the main priority. 


## Make investment


=== "Solana"

    Investors are required to interact with the Fund program and deposit in the base denomination of the fund. This amount is initially stored in the router vault and an investor account is created to identify each investment. A unique investment receipt corresponding to each individual's investment is also created in this process.

    ```yaml
    FundInstruction::InvestorDeposit { amount }
    ``` 

    The investor receipt allows Investin protocol to provide features like:
    
    1. Investor stoploss i.e. investors can define the percentage of profit or loss at which they want to withdraw.
    2. Enables fund PDA's to be composable since the receipt can be used as debt receipt for each investor account.

=== "EVM"

    Investors are required to interact with the router contract and give approval of the base token with which they would like to invest in any fund. After the approval investors can proceed to call the make investment function which mints an ERC 721 token and send it to the caller's address while transferring the said amount of approved tokens to the router.
    We use a different approach at solving the fund management system by using the ERC 721 standard to identify investors on blockchain.


    ``` yaml
    function makeInvestment(uint amount) external returns(uint256)
    ```

    ### IVNy token

    IVNy is a non-fungible token based on OpenZeppelin's ERC 721 standard, this token is used as a confirmation receipt that all investors shall receive on a successful investment transaction. The token holds no value and is merely used to identify investors of a particular fund.`Beware the loss of access to the address holding IVNy token can result to loss of investment as contracts are hardcoded and only recognize investors through these non-fungible tokens.`

    Advantages of using nft: 

    1. Once minted investor can use the same token in the wallet to interact with the protocol at almost 40% less gas expense since the protocol will know details about the investor, token acts as a marker.
    2. ==We plan to integrate lending feature for IVNy nft holders i.e. investors can borrow by staking their IVNy token as collateral.==
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

The performance on invested amount is queried on-chain and the smart contracts use on-chain amm pool reserves to calculate asset price. Hence, the performance will be subject to an error +/-2% but upon ending investment the asset evaluation done by contracts will be final and the true value of the asset. Blockchain is open by design and any investor can query the fund address to keep tabs on performance.



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

    This instruction can only be called by investor address and consists of multiple transactions to overcome the current limitation of 35 accounts and 200,000 compute limit per transaction. In order to achieve the composability of Investin's architecture we handle the withdrawal process in multiple steps. In each step the specific transaction updates on the investor account(receipt). `There is no lockup period; investors remain in full control of funds and can deposit/withdraw at their convenience.`

    Example flow:
    
    A fund having position in 4 assets that are swapped from Raydium and 2 margin positions open on mango markets is handled in the following transaction flows:
    
    1. The Investor share is calculated on the total fund AUM. The assets owed by fund are accounted in this stage.
    2. The dues on fund assets are settled and sent to investor wallet address
    3. The borrows are settled on both margin positions and according to investors' share, the positions are closed. It is important to note here that the health of margin account remains same since only the margin amount is changed.
    4. The dues on margin positions are settled by withdrawing from the Mango account and sending directly to the Investor's address.

=== "Solidity"

    This function can only be called by investor's holding IVNy token and consists of two sub-functions which gives investor's the option to either collect 100% of their investment or make a partial withdrawal to book profits on invested amount.

    The investors have the option to recieve their investment according to fund allocation which is the cheapest option to withdraw or they can provide the token in which they would like to get their investment withdrawn from fund.
    `There is no lockup period investors remain in full control of funds and can deposit/withdraw at their convenience.`





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

    A 2% upfront management fee is deducted on each successful investment out of which 1% is given to the manager who uses the fees to manage expenses of running the fund. This includes transferring tokens to fund contract and calling swap functions to trade using AMMs. The management fee will not be deducted if the investor withdraws their investment before the manager moves tokens to their fund contract. 

* Performance fee

    The managers can only collect their performance fee if they reach the minimum return on the individual's investment. This minimum ROI is range bound and can be anywhere between 5-40%. 1/10th of the total fee collected by the Manager is allocated to the protocol. If the manager makes less than the ROI they set, the investors will not be charged any performance fee and can withdraw at any time. This system of reaching minimum ROI thereby only encourages managers to make more profits and creates a positive feedback loop.

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

* Investors can withdraw funds from the router without incurring any fee if the withdrawal is done before the manager moves tokens to fund contract
* There is a possibility investment made to a fund hasnt been moved to fund contract which means the investment will be in an inactive state and no performance made by the relevant fund will be reflected on such investment. The state of investment can be checked through state function or on the investor dashboard. 
