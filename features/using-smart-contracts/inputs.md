---
description: 'How to get information from the user, to send to your contract method'
---

# Inputs

For contract methods that require user input we can use input fields on our website to collect this input from users. 

An example Input Tag would look like: 

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="simpleMessage"
/>
```

`data-dh-property-method-id` This is the `id` that was set when we created our Method Instance. This needs to match exactly so that the DappHero engine knows that this input is intended for that method instance. 

`data-dh-property-input-name` This is the name of the argument for the method that you are trying to interact with. This must match the name defined in the Smart Contract ABI  

So for example if you had a function written in solidity like this: 

```javascript
function foo(uint bar) public {
    ...
}
```

The value of `data-dh-property-input-name` would be `bar`. This is how we link the input field on our website with the input argument required by the smart contract. **It needs to match for the DappHero engine to know where to put the input data!**

{% hint style="success" %}
A method can take any number of input arguments, but you are required to provide **all** the input arguments for a method in order to make a successful method call. 
{% endhint %}

### Invisible Inputs

For some method instances you might want to hard-code the value of inputs and not give users the option to change the input value. To do this, you can use standard HTML to set the value of an input, and then hide it from the webpage so it is unseen. This is very useful for methods which auto-invoke on page load, but require inputs.

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="simpleMessage"
    value="some input value"
    style="display:none;"
/>
```

### AutoClear Inputs

DappHero will automatically clear the input values of form fields, regardless of the visibility. This is intended to give users a nice experience of having a form 'reset' after clicking submit. 

Normal HTML form behavior is that when a user inputs some information into a form field, then clicks "submit" the default behavior is to clear the form field to prepare it to accept new data. 

For invisible inputs however, with values that are intended to stay the same, reseting the input is most likely not the desired functionality. To prevent this behavior it is necessary to add a `auto-clear` tag to the input to explicitly tell the DappHero engine if you want the form value to be cleared after invocation. 

For various reasons this may or may not be the desired behavior in your application. This can specifically be a problem for **invisible inputs** which will, by default, automatically be cleared after your user clicks 'invoke'. 

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="simpleMessage"
    value="some input value"
    style="display:none;"
    data-dh-property-auto-clear="false"
/>
```

To avoid this problem, you can add a special tag: `data-dh-property-auto-clear="false"` to tell DappHero to not clear your input after a user clicks 'invoke'. 

To learn more about the `auto-clear` flag, read [Advanced: Automatically clearing Inputs](advanced-automatically-clearing-inputs.md).

```markup
<input 
    data-dh-property-method-id="000"
    data-dh-property-input-name="simpleMessage"
    data=dh-property-auto-clear="false"
    value="some default value I don't want deleted"
    style="display:none;"
/>
```

### Units

### Single Anonymous Inputs

When working with Ethereum Smart Contracts, there are some automatically generated public methods created to access lists of information, these are _arrays_ and _mappings._ They can be accessed the same as regular public variables, with a minor change in syntax.

```javascript
//Example Solidity Psuedo Code

contract BallotTest {
   
    string[] public proposalNameArray;
    //or
    mapping(uint => string) public proposalNameMapping;

...other stuff...
}
```

To access a value inside a public array or mapping it is necessary to provide an index or key to request a specific piece of data back from the blockchain. In the above example it would be necessary to first provide an integer to get back a single `proposalNameArray` or `proposalNameMapping`.  

Because these methods are automatically generated by the Solidity compiler, they are given _anonymous_ input names. This means that they have no corresponding `data-dh-property-input-name` to access their values. 

In order to get a value out of an anonymous input, \(arrays or mappings\) you will need to use the special constant: **$true**.

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="$true"
/>
```

This will properly inform the DappHero engine that this is a generated anonymous public method and allow you to pass in data from the user to request specific pieces of data inside of public arrays and mappings. 

{% hint style="warning" %}
The tag format: `data-dh-property-input-name="$true"` is scheduled to be deprecated at some point in the future. For now, continue to use it, but check back regularly to learn when we will plan the change. 
{% endhint %}

### Multiple Anonymous Inputs

There are some situations where you may have more than one anonymous input. A good example of this is the popular [**Wrapped-Eth**](https://etherscan.io/address/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2#code) contract \(which holds over $500 million dollars in ether!\). 

In this contract we have these public method which is a `mapping` of a `mapping`.

```markup
    mapping (address => mapping (address => uint))  public  allowance;
```

The resulting contract ABI looks like this:

`{"constant":true,"inputs":[{"name":"","type":"address"},{"name":"","type":"address"}],"name":"allowance","outputs":[{"name":"","type":"uint256"}]`

If you notice there are **two** inputs with a `name` value of empty string: `''`. To access these we have recently introduced **array indices** notation. To access the the first argument \(The outer address mapping\) you would use the following tag: 

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="[0]" <!-- Notice the array notation 
/>
```

To access the second input you would use: 

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="[1]"
/>
```

Remember in programming with arrays we alway start counting from zero!

### Units

The input units for a contract method are defined on the contract ABI and can not be changed. In some cases however the units required by a smart contract can be confusing to a user and thus need to be converted. 

DappHero currently supports converting between `bytes32` and `ascii` as well as `ether` and `wei`.

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="simpleMessage"
    data-dh-modifier-display-units="ascii"
    data-dh-modifier-contract-units="bytes32"
/>
```

In this example, a user can enter text in `ascii` \(ASCII is the standard way of entering normal text\) but DappHero will convert it to `bytes32` before sending it to the contract.

### Inputs Reference

| Tag | Property | Required? |
| :--- | :--- | :--- |
| `data-dh-property-method-id` | `<<aUniqueString>>` | Yes |
| `data-dh-property-input-name` | `<<input name>> || $true` | Yes |
| `data-dh-property-auto-clear` | `false || true` | optional |
| `data-dh-modifier-display-units` | `ether` `wei` `bytes32` `ascii` | Optional |
| `data-dh-modifier-contract-units` | `ether` `wei` `bytes32` `ascii` | Optional |

