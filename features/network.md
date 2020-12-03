---
description: Connecting to the Network and sending ETH
---

# Network ⛓️

The Network feature allows you to connect and get information from the current Ethereum network. You can read information from the currently connected network, allow a user to enable the connection to the current network, and give the User the ability to send ETH. 

{% hint style="info" %}
Want to get started quick with no-code? Check out our no-code template in Webflow!
{% endhint %}

{% embed url="https://webflow.com/website/DappHero-network" caption="Click \"clone\" to make it yours!" %}

{% hint style="info" %}
Prefer to dig in and get your hands dirty with HTML? Remix our Demo on Glitch!
{% endhint %}

{% embed url="https://glitch.com/~dapphero-network" caption="Click \"remix\" to start your own project!" %}

### Network Enable

{% hint style="info" %}
It is **required** that you implement a **Network Enable** element in your webpage. This should ideally be a **`button`**type element that a user clicks to connect to ethereum. Without it, DappHero won't load!
{% endhint %}

| Tag | Property | Required? | Output |
| :--- | :--- | :--- | :--- |
| `data-dh-feature` | "network" | Yes | none |
| `data-dh-property-enable` | "true" | Yes | none |

We recommend that you feature this button prominently, where users will see it immediately. As a matter of privacy and security, DappHero will only be able to process transactions and access your users information once the connection has been approved. 

An example of what an Enable button might look like. When a user clicks on it, they will be requested by MetaMask to give their permission to be connected to your website. 

```markup
<button
    data-dh-feature="network"
    data-dh-property-enable="true">
    *Button Text*
</button>
```

### Network Data

| Tag | Property | Required? | Output |
| :--- | :--- | :--- | :--- |
| **To Display Data** |  |  |  |
| `data-dh-feature`  | "network" | Yes | none |
| `data-dh-property-id` | "true" | optional | Network Id |
| `data-dh-property-name` | "true" | optional | Network Name |
| `data-dh-property-provider` | "true" | optional | Network Provider |

There are many different kinds of Ethereum networks, each have their own ID. To get the value of the current network ID, use: 

```markup
<div
    data-dh-feature="network"
    data-dh-property-id="true">
    *placeholder text*
</div>
```

When your webpage loads, the word "placeholder text" will be replaced with the value of the currently connected Network ID. 

#### Network Name

Along with a Network ID, most public Ethereum networks also have a network name, which can be more intuitive to users than Network ID. Note, if you are connected to a private network or special purpose network, your network may not have a known network name. 

```markup
<div
    data-dh-feature="network"
    data-dh-property-name="true">
    *placeholder text*
</div>
```

#### Network Provider

Currently, users will be bringing their own connection to the Ethereum Blockchain in the form of an in browser wallet such as [MetaMask](http://www.metamask.io). To get the name of the current provider, use: 

```markup
<div
    data-dh-feature="network"
    data-dh-property-provider="true">
    *placeholder text*
</div>
```

{% hint style="info" %}
Currently DappHero supports only MetaMask for users, but will be expanding the number of providers it supports in the near future. 
{% endhint %}

## Transferring ETH

The DappHero Network feature also allows you to let a user transfer ETH. To do this you would add input `elements` to your webpage that you tag for `amount` and recipient `address` respectively. 

{% hint style="info" %}
Current there can be only one instance of ETH transfer per page. This will be changed in a future release of DappHero to allow for multiple transfers per page.
{% endhint %}

| Tag | Property | Required? | Output |
| :--- | :--- | :--- | :--- |
| **FOR SENDING ETH** |  |  |  |
| `data-dh-feature` | "network" | Yes | none |
| `data-dh-property-transfer` | "input" | Yes | none |
| **Input Elements** |  |  |  |
| `data-dh-property-input-name` | "amount" | Yes | none |
| `data-dh-property-input-name` | "address" | Yes | none |
| **Invoke Button** |  |  |  |
| `data-dh-property-transfer` | "invoke" | Yes | none |
| **Units Modifier** |  |  |  |
| `data-dh-modifier-display-units` | "ether" \| "wei" | optional | Input Modifier |

```markup
<!-- An input field for the amount of ETH to send, with the units set to ETH -->
<input 
            data-dh-feature="network"
            data-dh-property-transfer="input" 
            data-dh-property-input-name="amount" 
            data-dh-modifier-display-units="ether">
</input>
      
<!-- An input field for the address to receive the ETH -->
<input
            data-dh-feature="network" 
            data-dh-property-transfer="input"
            data-dh-property-input-name="address">
</input>
    
<!-- A button to invoke the action of sending ETH and request user signature -->
<button 
            data-dh-feature="network" 
            data-dh-property-transfer="invoke">
            Click to transfer!
</button>
```

To require users to send a specific amount of ETH or to a predefined address, you would set the value of the inputs manually and set their style to `display: none` to effectively hide them from the user. 

```markup
<!-- An input field for the amount of ETH to send, with the units set to ETH -->
<input 
            data-dh-feature="network"
            data-dh-property-transfer="input" 
            data-dh-property-input-name="amount" 
            data-dh-modifier-display-units="ether"
            style="display:none;"
            value="<<predefined amount of ETH>>">
</input>
      
<!-- An input field for the address to receive the ETH -->
<input
            data-dh-feature="network" 
            data-dh-property-transfer="input"
            data-dh-property-input-name="address"
            style="display:none;"
            value="<<predefined address>>">
</input>
    
<!-- A button to invoke the action of sending ETH and request user signature -->
<button 
            data-dh-feature="network" 
            data-dh-property-transfer="invoke">
            Click to transfer!
</button>
```





