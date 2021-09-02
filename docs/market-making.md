# Market making funds



Here, we provide a step-by-step guide on to create a market making fund and connect it to a bot running on google cloud


1. Create fund and set an delegate address for sending instructions
2. Clone basic market making bot repo
3. Set the bot on cloud and add in delegate private keys
4. Check the positions through manager dashboard and claim performance fee i.e $MNGO tokens 


### Create fund 
* Visit [Investin][1] dashboard and click on start fund
[1]:https://sol.beta.investin.pro/user/dashboard

![Placeholder](assets/11.png){: align=center }

* Select market making from type of fund selection and click on create fund
* Add minimum deposit, performance fee %: Share of mngo accrued which goes to the manager as performance reward. On top of that, manager would earn the usual performance fees if the fund performance goes above the minimum return percentage
* After create fund, generate a new keypair using: solana-keygen new --outfile <id.json>
* Fund the newly created address with some SOL
* Clone repo: https://github.com/MuneebMohammed/mango-explorer/tree/investin_mm
* Click show config button on dashboard page, copy it to a file: investin.json
* Setup the marketmaking bot in a python virtualenv:
Requirements: Python v3.8
Setup environment
``` pip install virtualenv
    virtualenv venv
    virtualenv -p /usr/bin/python3 venv
    source venv/bin/activate 
    pip install -r requirements.txt```

Run the marketmaking bot
```./bin/marketmaker --name "Investin MM" --market BTC-PERP --oracle-provider pyth --position-size-ratio 0.2  --existing-order-tolerance 0.0001 --pulse-interval 5 --order-type POST_ONLY --confidence-interval-level 0.05  --cluster-name mainnet --cluster-url https://mango.rpcpool.com --group-name mainnet.1 --investin investin.json ```


* 

    ![Placeholder](assets/113.png){: width="300" align=center }

* Set the delegate address whose private key you will be adding in bot configuration

<figure>
  <img src="(assets/113.png)" width="300" />
  <!-- <figcaption>Image caption</figcaption> -->
</figure>

* Visit github and clone the repository on your computer

* To run locally follow the readme instructions in the repository

* To run on the cloud create a account on GCP and add private keys of your delegate in config.json