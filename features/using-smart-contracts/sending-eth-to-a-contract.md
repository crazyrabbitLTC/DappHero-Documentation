---
description: How to optionally send ETH to a contract method.
---

# Advanced: Sending ETH to a contract method

Sometimes when you are interacting with a contract method, you want to be able to specify that a user can optionally send ETH. To do this with DappHero we have the option to either hardcode the ETH amount \(for example if a contract requires exactly 1 ETH to do some task\) or allow users to optionally input the amount themselves. 

### Hardcoded

{% hint style="danger" %}
This example is in the process of being deprecated. Please try to use 
{% endhint %}

In the case that you wish to hard-code the amount of ETH that should be sent upon interacting with a contract method, you should define the amount in the method instance object with a `data-dh-property-eth-value` tag. 

| Tag | Value | Units |
| :--- | :--- | :--- |
| `data-dh-property-eth-value` | `<<amountOfEther>>` | Ether |

The value for this tag is the amount of ETH to send 

Here is an example of how it could be used in a Method Instance: 

```markup
<div
    data-dh-feature="customContract"
    data-dh-property-contract-name="MyStore"
    data-dh-property-method-name="buyItem"
    data-dh-property-method-id="000"
    data-dh-property-eth-value="1.5"
>
```

In this example, when this method is invoked, 1.5 ETH will be added to the transaction and if the user approves the transaction, this ETH will be sent to the smart contract. 

### Input Fields

In the case that you want to allow your users to specify the amount of ETH they would like to send to a smart contract method, you can attach a `data-dh-property-input-name="EthValue"` tag directly to an input element.

{% hint style="info" %}
Input fields can also be used for sending Hard coded amounts of ETH. Rather than the deprecated method above use the following tags. To hide the input from the user, use `style="display: none;"` as an additional tag. 
{% endhint %}

| Tag | Value |
| :--- | :--- |
| `data-dh-property-input-name` | `EthValue` |

An example of this for an input element would look like this: 

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="EthValue"
/>
```

In this example, when the method is invoked, the amount of ETH to be sent along with the transaction will be defined by the amount in the input `data-dh-property-input-name="EthValue"` is attached. 



