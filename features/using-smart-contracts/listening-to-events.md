---
description: Getting advanced functionality
---

# Listening to Events

{% hint style="warning" %}
This documentation describes functionality that is in development. For latest version check the [nightly build](../../updates/changelog.md).
{% endhint %}

For more advanced builders looking to use external scripts to add custom functionality to DappHero powered websites, we are in the process of exposing events. 

**Events**

Listening to events gives you the ability to "monitor" the DappHero engine and react to changes in the state of the blockchain or smart contracts. Events can be used from HTML javascript, jQuery scripts, React or any Javascript Framework. 

**Adding an Event Listener**

To add an event listener in Javascript you would use the following code. In this example, the code will print "DappHero loaded" as soon as DappHero has loaded and is ready. 

```javascript
document.addEventListener("dappHeroConfigLoaded", ({ detail: dappHero }) => {
      // Inside here you can listen to any event you want	
      console.log("DappHero loaded")
});
```

For smart contracts, to listen to a change, for example to monitor the success or failure of a transaction, you would use: 

```javascript
document.addEventListener("dappHeroConfigLoaded", ({ detail: dappHero }) => {
        dappHero.listenToTransactionStatusChange(data => {	
                console.log("Listening to transactionStatusChange", data);	
        });
});
```

The `data` object will contain information about the current action taking place, the status and the contract method Name. This will fire on any smart contract change made in the browser. In the case of `auto-invoke` this can be very noisy. To filter for specific smart contract method you can evaluate the `data.mythodNameKey.value` to see if it matches the specific smart contract method you are interested in.

**Complete Example**

To listen to the smart contract method `transferTokens` from a script \(possibly jQuery\) you would use the following code. It will fire whenever a user or `auto-invoke` interacts with the smart contract method `transferTokens`. 

```javascript
<script>
      document.addEventListener("dappHeroConfigLoaded", ({ detail: dappHero }) => {  
      const methodName = 'transferTokens'
      dappHero.listenToTransactionStatusChange(data => {	
        if(data.methodNameKey.value === methodName) 
        console.log(`Listening to change in ${methodName}`, data);	
      });});
</script>
```

