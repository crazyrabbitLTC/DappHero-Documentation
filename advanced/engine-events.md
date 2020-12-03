---
description: Listening to the DappHero Core engine
---

# Engine Events

When creating more advanced code and logic it can be important to listen internally to the changes happening inside the DappHero-Core engine. To help do this, we have provided a number of event listeners to help you react to internal changes to DappHero Core processes. 

All listeners take a callback and will be triggered on an event change internally. 

To use these, first listen for the event that signals DappHero has loaded, and then you can listen for DappHero specific events.  

```javascript
<script>
      document.addEventListener(
        "dappHeroConfigLoaded",
        ({ detail: dappHero }) => {
          // Inside here you can listen to any event you want
  
          // dappHero.listenToSmartContractBlockchainEvent(data => {
          //   console.log("The blockChain Events: ", data)
          // })
        }
      );
</script>
```

### List of Listeners: 

#### Smart Contracts

`listenToTransactionStatusChange()`

Fires for each step in the process of preparing and submitting a transaction to the blockchain.  

`listenToSmartContractBlockchainEvent()`

Fires for each event [emitted by an Ethereum smart contract](https://solidity.readthedocs.io/en/develop/abi-spec.html?highlight=events#events). 

`listenToContractOutputChange()`

Fires for a change in smart contract output.

`listenToContractAutoInvokeChange()`

Fires each time a public smart contract method is auto-invoked. For auto-invoked elements, this can be noisy. 

`listenToContractInvokeTriggerChange()`

Fires each time a smart contract is invoked.

#### Network Feature \(ETH Transfer\)

`listentoEthTransfer()`

Fires for an Ethereum transfer event.

#### 3Box Feature

`listenTo3BoxProfile()`

Fires for a 3Box feature event.

#### NFT Feature

These events will fire based on their related functionality. They each work the same. 

`listenToNFTLoadAllToken()`

`listenToNFTLoadMultipleToken()`

`listenToNFTLoadSingleToken()`

#### User Feature

`listenToUserAddressChange()`

Fires for a change in the user address, for example, when switching addresses in MetaMask.

`listenToUserBalanceChange()`

Fires when a users balance changes. 

