---
description: Using Collectibles in your DappHero project
---

# Getting Started

### Things to keep in Mind

The syntax for working with Collectibles is relatively similar to that of working with smart contracts. We need to create an _instance_ and _elements_ which are connected via a `uniqueId` to link them both together. 

### Feature Collectibles vs Feature Custom Contract

Collectibles are managed by smart contracts deployed on the blockchain. This means you _could_ access them directly using DappHero's ****Smart Contract Feature. For some uses cases it might be preferable to access the smart contracts directly, however for common uses Collectible smart contracts \(most commonly ERC721 contracts\) it will be easier to use the Collectible feature as we have simplified some of the more common use cases. 

The advantage of using the Collectibles feature is that DappHero simplifies the process of interacting with the JSON objects which are used to store the [metadata](https://docs.opensea.io/docs/metadata-standards) which represent individual collectible tokens in a standard way. Following these standards are important if you want your collectible token to be interoperable with public marketplaces. 

## General Concepts

### Unique ID

When you create an _instance_ of a collectible object, you will be able to place the collectibles _elements_ anywhere on your webpage. To link the correct instance with the correct elements, we have introduced a special tag,  `data-dh-property-method-id`, which has a custom unique value that you determine, and which should be used for all elements related to the same functionality. 

```markup
// This element creates our collectable instance
<div ...
data-dh-feature="nft"
data-dh-property-tag-id="myUniqueTag" 
....
/>

// This element is where we are going to be displaying a collectable item
<div ...
data-dh-property-tag-id="myUniqueTag" 
data-dh-property-asset-item="true"
...
/>

```

In the above example, all the elements for a `Collectable` integration are marked with the same unique tag id, `myUniqueTag` in this way, the DappHero Engine knows all these different elements, regardless of where they are on the page, belong together in the same functionality. 

### TokenId

In the ERC721 standard, each token is given a TokenId that represents it as a unique item. This TokenId is needed to identify the specific collectible. 

### Contract Address

As collectibles are governed by smart contracts, such as the [CryptoKitties](https://etherscan.io/address/0x06012c8cf97bead5deae237070f9587f8e7a266d#code) Contract or [BlockCities](https://etherscan.io/address/0x2f2d5aa0efdb9ca3c9bb789693d06bebea88792f#code) Contract, they each have a unique Ethereum Address. This address is what differentiates tokenId\# 100 on CryptoKitties from tokenId\# 100 for BlockCities. A good way to mentally think about this is; _TokenId\# 100 for Contract Address: 0x0....._

### JSON Path

When calling an ERC721 Collectible contract for a specific token, most standard tokens will return a _tokenURI._ This _tokenURI_ generally is a link which points to a place on the internet that stores metadata _about the token_ generally this is a JSON object with properties which describe what the token represents, such as a CryptoKitty name or a CryptoKitty picture. 

To access this metadata,  we use a special DappHero Tag: `data-dh-property-asset-json-path` followed by the item we are looking for such as `image_url` or `name`. This element will be defined on the JSON object returned by the metadata. 

```markup
//psuedo code

//Displaying a token's Image
<img data-dh-property-asset-json-path="image_url" />

//Getting a token name as H3 text                  
<h3 data-dh-property-asset-json-path="name"></h3>
```

Unfortunately while there are some [standards](https://docs.opensea.io/docs/metadata-standards) for how MetaData should be structured, they are not 100% standard. If connecting to a contract with non-standard meta-data you will need to contact the contract creators to understand the format returned by the collectible contract.

### Collectable Data Source and Networks

DappHero uses the [OpenSea API](https://opensea.io/) as a data source for Collectables, currently it does not pull the data directly from the blockchain network. This means that currently the `Collectable` feature only supports the Ethereum Mainnet. 

