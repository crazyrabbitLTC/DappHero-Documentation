---
description: How to create a Method Instance for your customContract
---

# Create a Method Instance

DappHero organizes functionality for a contract method around a **method instance**. To create a method instance all you need to do is add special data-property tags to your elements \(an easy-to-do task in Webflow or Glitch\) and DappHero will do the rest. 

### Create an instance of your method: 

First you need to create an instance of your method that you would like to interact with. You will then be able to add elements on your webpage that interact with this method, and by giving them each the same unique id, they will all be related, regardless of their placement on your webpage. 

What does this look like? 

```markup
<div
    data-dh-feature="customContract"
    data-dh-property-contract-name="dappherotest"
    data-dh-property-method-name="hello"
    data-dh-property-method-id="000"
    data-dh-property-eth-value="1" 
>
optional text
</div>
```

 `data-dh-feature` **\(required\)** This is how we identify to the DappHero engine that you intend to connect to a smart contract. 

`data-dh-property-contract-name`  **\(required\)** This is the name of your smart contract, it needs to match the name you have listed in your DappHero Admin project exactly. 

`data-dh-property-method-name`  **\(required\)** This is the actual method you are trying to invoke on your smart contract. For example if you have a method `getBalance` on your smart contract, you would add the method name here. 

`data-dh-property-method-id`  **\(required\)** This is custom id that you give your webpage element. All of the elements which are related to this `customContract` method will need to have the **same** id. This way you can place the elements anywhere on the page and DappHero will know they belong together.

`data-dh-property-eth-value` **\(optional\)** For contract methods that accept ETH \(aka: payable functions\) you can hard-code an amount of ETH to be sent to a contract method whenever a user makes a transaction. This is useful when you want users to send a fixed amount of ETH to a contract method.  If you want to let your users define the amount of ETH themselves, you can use an Input field instead.



### Custom Contract Reference: 

| Tag | Property | Required? |
| :--- | :--- | :--- |
| `data-dh-feature` | customContract | Yes |
| `data-dh-property-contract-name` | `<<your-contract-name>>` | Yes |
| `data-dh-property-method-name` | `<<yourMethodName>>` | Yes |
| `data-dh-property-method-id` | `<<aUniqueValue>>` | Yes |
| `data-dh-property-eth-value` | `<<amount of ETH to send>>` | optional |

