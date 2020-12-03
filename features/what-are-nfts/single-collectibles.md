---
description: Retrieving a single collectible and displaying it's data
---

# Single Collectibles

Collectibles are represented by smart contracts, and this means they have a number of standard properties such as a contract, a deployed contract address, and collectible owners. Depending on what we are trying to do, we will need difficult combinations of these parameters to get the right token.

#### Get a single Collectible by TokenID and Owner Address

This will return any single token with a `TokenId` and owned by `OwnerAddress` If there are multiple tokens with `TokenId` owned by this address, it will only return the first token that it finds.

```markup
<!-- This top level div is the method Instance -->
<div
    data-dh-feature="nft"
    data-dh-property-tag-id="<<uniqueID>>"
    data-dh-property-asset-token-id="<<TokenId>>"
    data-dh-property-asset-owner-address="<<OwnerAddress>>">
    
    <div data-dh-property-tag-id="<<uniqueID>>" 
         data-dh-property-asset-item="true">
         
         <img data-dh-property-asset-json-path="image_url" />
         <h3 data-dh-property-asset-json-path="name"></h3>
         
    </div>
    
</div>
```

In the case that an owner potentially owns multiple tokens with the same `TokenId` in different Collectible contracts you can filter by using: 

`data-dh-property-asset-contract-address="<<Address>>"`  in the Collectible instance after specifying the `asset-owner-address`. This will return results only from this specific collectible contract address.

#### Get a single Collectible by TokenID and Contract Address

If the owner address is not relevant, by suppling only a `TokenId` and `ContractAddress` a single token will be returned. 

```markup
<!-- This top level div is the method Instance -->
<div
    data-dh-feature="nft"
    data-dh-property-tag-id="<uniqueID>>"
    data-dh-property-asset-token-id="<<TokenID>>"
    data-dh-property-asset-contract-address="<<ContractAddress>>">
   
    <div data-dh-property-tag-id="<<uniqueID>>" 
         data-dh-property-asset-item="true">
         
        <img data-dh-property-asset-json-path="image_url" />
        <h3 data-dh-property-asset-json-path="name"></h3>
        
    </div>
      
</div>
```



