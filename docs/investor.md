# Investors

## Overview

We see investors as key liquidity providers of the platform whose success in markets would determine Investin's future. The protocol will fail if both the users are not well incentivized to conduct trustless exchange of offering, while managers have good idea of markets and can sail well investors need particular kind of help and best in class UI with safety standards built in to protect capital at all costs. 


## Make investment

Investors are required in interact with router contract and give approval of the base token with which they would like invest in any fund. After the approval investors can proceed to call the make investment function which mints a erc 721 token and send to the caller's address while transferring the said amount of approved tokens to router.
We use a different approach at solving the fund management system by using erc 721 standard to identify investors on blockchain.

=== "Layer 1"
    
    ``` yaml
    function createFund (string calldata _fundName, uint _minAmount, 
    uint256 _minReturn, uint _performanceFeePercentage) external returns(address)
    ```

=== "Layer 2"
    
    ```yaml
    comming soon on a rollup near you
    ```


### IVN token

IVN is a non fungible token based on openzepplines erc 721 standard, this token is used as a confirmation receipt which all investors shall recieve on a successful investment transaction. The token holds no value and is merely used to identify investors of particular fund. This token cannot be transferred between addresses and can only be sent back to Investin's router contract to retreieve funds. `Beware loss of access to the address holding IVN token can result to loss of investment as contracts are hard coded and only recognize investors through these non fungible tokens.`  

### Performance

The performance on invested amount can be queried on chain and the smart contracts use on chain amm pool reserves to calculate asset price hence the performance will be subject to an error +/-2% but upon ending investment the asset calculation done by contracts will be final and true to the exact decimel at all times. Blockchain are open and any investor can query the fund address to keep tabs on performance.

=== "Layer 1"
    
    ``` yaml
    function createFund (string calldata _fundName, uint _minAmount, 
    uint256 _minReturn, uint _performanceFeePercentage) external returns(address)
    ```

=== "Layer 2"
    
    ```yaml
    comming soon on a rollup near you
    ```

## End Investment

This function can only be called by investor's holding ivn token and consists of two sub functions which requires investor's to first call the end investment function which calculates performance for investor and accordingly sells the share of investor's assets in proportion to get the exact base token that is to be returned according to fund's performance during the investment period. Second function call requires the sending of ivn token back to router which will inturn release investor's tokens back to their address.
`There is no lockup period investors remain in full control of funds and can deposit/withdraw at their convenince.`

=== "Layer 1"
    
    ``` yaml
    function createFund (string calldata _fundName, uint _minAmount, 
    uint256 _minReturn, uint _performanceFeePercentage) external returns(address)
    ```

=== "Layer 2"
    
    ```yaml
    comming soon on a rollup near you
    ```

## Fees

* Management fee

    A 2% upfront management fee is subtracted on each successful investment which is given to manager who uses the fees to manage expenses of running the fund which includes tranferring tokens to fund contract and calling swap functions to trade using amm's. The management fee wont be subtracted if the investor withdraws their investment before the manager moves tokens to their fund contract. 

* Performance fee

    The managers can only collect their performance fee if they reach the minimum return on investment they set, this minimum roi is range bound and can be anywhere between 5-50%. If the manager makes less than the roi they set, the investors wont be charged any performance fee and can withdraw any time. This system of reaching minimum roi therby only encourages managers to make more profits and creates a positive feedback loop.


## Miscelenous 

* Investor's can withdraw funds from router without incuring any fee if the withdrawal is done before manager moves tokens to fund contract
* There is a possibility investment made to a fund hasnt been moved to fund contract which means the investment will be in a inactive state and no performance made by the relevant fund will be reflect on such investment. The state of investment can be checked through state function on ivn contract 
=== "Layer 1"
    
    ``` yaml
    function createFund (string calldata _fundName, uint _minAmount, 
    uint256 _minReturn, uint _performanceFeePercentage) external returns(address)
    ```

=== "Layer 2"
    
    ```yaml
    comming soon on a rollup near you
    ```