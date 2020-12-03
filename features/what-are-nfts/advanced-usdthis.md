---
description: Referring to the current Collectible's information
---

# Advanced: $THIS

{% hint style="info" %}
This documentation is unfinished
{% endhint %}

Advanced features such as [getting parameters from the URL bar](advanced-url-query-params.md), or referencing the [current user](advanced-usdcurrent_user.md) are important to building dynamic functionality for Collectibles. To complete this functionality and give users the ability to dynamically generate links from Collectibles in a list to a page of a single collectible, we have created the ability for an HTML block to dynamic reference itself with the const `$THIS...`

### Usage

The `$THIS...` const is useful when it is necessary to refer to the current item, for example when creating dynamic links that should be unique for each collectible item.  

| CONST | Purpose |
| :--- | :--- |
| `$THIS_ContractAddress` | Substituted with current Contract Address |
| `$THIS_TokenID` | Substituted with current TokenID |
| `$THIS_OwnerAddress` | Substitutes with current OwnerAddress |

### Example

For a live Demo: [DappHero-nft-example](https://glitch.com/~dapphero-nft-example).

Suppose you wanted to build a webpage that showed a dynamic list of Collectibles based on the contract address of a particular NFT contract. This is fairly easy to do, [ list the Collectibles](listing-collectables.md#general-concepts). Now let's say you wrap each Token's image in an `anchor` tag, turning the image itself into a link that when clicked upon takes the user to a new webpage that shows a [Single Collectible](single-collectibles.md). Creating a Single Collectible is also fairly easy, but the question is- how would you pass the data about WHICH collectible you want to display on the Single Collectible page? 

This is where we use `$THIS...`

```markup
<div
      data-dh-feature="nft"
      data-dh-property-tag-id="000"
      data-dh-property-asset-contract-address="<<contractAddress>>">
     
   <div
      data-dh-property-tag-id="000"
      data-dh-property-asset-item="true">
      <a
         href="./singleNFT.html?assetTokenId=$THIS_TokenID&assetContractAddress=$THIS_ContractAddress">
         <img data-dh-property-asset-json-path="image_url"/>
         </a>
     </div></div>
```

Let us take a closer look at line 9-12. What we are doing here is creating a link to a new page but passing URL Query Params for the DappHero engine to catch in the `singleNFT.html` page. You could manually pass the details `assetTokenId=1234` but then you would be stuck always rendering this one token. Instead, because we are inside the `asset container` from line 6-9 which gets rendered for each Collectible returned, we can access THIS specific token. If we use $THIS\_TokenID in the `href` link, it will get replaced with the token currently displayed, for example '1234'. If we do the same for the `assetContractAddress` we can now link to the `singleNFT.html` page passing all the information required for that page to render dynamically the specific collectible token we are interested in. 

```markup
<a
href="./singleNFT.html?assetTokenId=$THIS_TokenID&assetContractAddress=$THIS_ContractAddress">
<img data-dh-property-asset-json-path="image_url"/>
</a>
```

### Forms

Using the `$THIS...` const is useful for more than just creating dynamic links- it can also be used to create dynamic forms. This means you can combine the Collectible feature with other features like smart contracts- allowing users to interact with smart contracts using the about the current token they are looking for. A great example for this would be to create a Collectible store front connected to a smart contract to let people buy or sell Collectibles directly from your website!

Have a look at this simple example. 

```markup
<form action="">
        TokenID: <input type="text" value="$THIS_TokenID"><br><br>
        Owner Address: <input type="text" value="$THIS_OwnerAddress"><br><br>
        <input type="submit" value="Submit">
</form> 
```



