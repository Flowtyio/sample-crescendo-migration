*We will use the FlowtyTestNFT contract as an example, you should replace it with your project smart contract*

## Requirements:

- Flow CLI installed into your computer
https://developers.flow.com/tools/flow-cli/install

- Crescendo Flow CLI installed into your computer
https://cadence-lang.org/docs/cadence-migration-guide#install-cadence-10-cli

### Create a new testnet account

- Open the terminal and run the command:
```flow accounts create```

- Enter the account name, for example: testnet-account

- Select testnet network

- At the end you will see that a new account has been added to your flow.json file

### Deploy FlowtyTestNFT pre-crescendo contract version

- Open the flow.json file and inside the deployments object add:
```
    "testnet": {
      "your-testnet-account-name-here": [ "FlowtyTestNFT" ]
    },
```

- Run the command to deploy the contract on the testnet network using your new testnet account
``` flow project deploy -n=testnet ```

### Stage the updated version of the contract on the testnet

- Inside the flow.json file, update the testnet contract address present inside the contracts > FlowtyTestNFT > aliases > testing object, using the new testnet account where you deployed you FlowtyTestNFT contract version 

- Inside the flow.json file, update the FlowtyTestNFT source, to use the crescendo update FlowtyTestNFT version, to it you will need to replace the: 
   - Current source: ```"./contracts/FlowtyTestNFT.cdc"```
   - To the one using cadence 1.0 contract version: ```"./contracts-v1/FlowtyTestNFT.cdc"```

- With the updated paths in the flow.json file you can now run the command that will perform the migration to the updated contract:

```
flow-c1 migrate stage FlowtyTestNFT --network=testnet
```

