---
description: Connecting to Smart Contracts
---

# Smart Contracts 👩🏾‍🔬

{% hint style="danger" %}
DappHero is currently in **BETA** meaning things might not always work. Please be careful about using it on Mainnet and inform your users to also double check their transactions before confirming. 
{% endhint %}

Traditionally to connect to smart contracts in your website you needed to import javascript libraries into the browser, create a large amount of custom javascript code, and be careful to check for a wide range of conditions. DappHero makes connecting to smart contracts painless and simplifies this task enormously so that you can focus on **what** you are building, rather than **how** to build it.

A DappHero project can be used to connect to any number of smart contracts, there's no limit!

To get started with Smart Contracts, let's quickly review some basics before diving into more detail. 

### How it works

Interacting with custom smart contracts generally takes five steps:

1. [Add a Smart Contract to your project on dapphero.io](adding-smart-contracts/) 
2. [Create a Method Instance element in your website](create-a-method-instance.md)
3. [Create your input elements](inputs.md)
4. [Decide how your method is invoked](invoke.md)
5. [Display the outputs](outputs.md)

{% hint style="info" %}
Read the following paragraphs about Unique ID's to understand how functionality is grouped in DappHero. 
{% endhint %}

### Methods

Smart contracts are made up of **methods,** \(think of **functions** if you have a programing background\) which allow you to interact with the state of the blockchain. You can retrieve information or send information to the blockchain using methods. 

Interacting with smart contracts in DappHero is organized around interacting with _specific_ smart contract methods**.**  Each method does something specific, and you can connect to as few or as many methods of a smart contract as you like on your website. In this way, DappHero represents each method for each contract as a  **method instance.** In practice this makes it very easy to work with smart contracts, as you don't need to worry about the entire smart contract, only the methods you wish to use. 

Learn more about [Creating a Method Instance](create-a-method-instance.md).

### Unique ID

`CustomContracts` methods are different than other DappHero features as their functionality requires multiple components. Unlike `Network` or `User` features which require only one tag to identify an element and replace its data, `CustomContracts` require a variable number of elements that can potentially be located anywhere on the screen. 

To account for the fact that you can put your elements for a `CustomContract` ****anywhere on the page, we have introduced a special tag,  `data-dh-property-method-id`, which has a custom unique value that you determine, and which should be used for all elements related to the same functionality. 

```markup
// This tag gives information about the method instance
<div ...
data-dh-property-method-id="myUniqueTag"
....
/>

// This element is where you define the input
<input ...
data-dh-property-method-id="myUniqueTag"
...
/>

// This button will invoke the method
<button ...
data-dh-property-method-id="myUniqueTag"
...
/>

// This element will display the output
<div ...
data-dh-property-method-id="myUniqueTag"
...
/>
```

In the above example, all the elements for a Custom Contract integration are marked with the same unique tag id, `myUniqueTag` in this way, the DappHero Engine knows all these different elements, regardless of where they are on the page, belong together in the same functionality. 

