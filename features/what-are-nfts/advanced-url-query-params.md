---
description: Set the Collectible Feature instance via URL query params
---

# Advanced: $URL

### Background

To set `data-dh-property-asset-token-id` , `data-dh-property-asset-owner-address` , and `data-dh-property-contract-address` via the URL bar, we can use the special value: `$URL`

This can be a very handy feature for creating dynamic websites that can display a list of Collectible tokens in a dynamic way. Consider for example a webpage that shows a list of tokens owned by user, but then when a user clicks on a particular token in that list, it loads a new webpage that now shows only a single token. 

To do this could be very complicated, but with DappHero $URL query params we've created a shortcut to allow you to create dynamic and exciting experiences around Collectible tokens. By allowing the use of query params, users can now create a single template for their Collectible features without hardcoding any variables. Users can load the same HTML file in their browser but with different query params and it will load different sets of Collectible tokens. 

{% hint style="warning" %}
$URL Query Params can only be used by a single Collectible feature instance per webpage. 
{% endhint %}

To use the `$URL` special variable, simply replace the `token-id`, `owner-address`, or `contract-address` with the value `$URL` and the DappHero engine will search for the values from the browsers URL bar.

```markup
http://www.yourDomain.com/?assetTokenId=...tokenId&assetOwnerAddress=...ownerAddress&assetContractAddress=...contractAddress
```

### HTML

```markup
<div
      data-dh-feature="nft"
      data-dh-property-tag-id="<<UniqueID>>"
      data-dh-property-asset-token-id="$URL"
      data-dh-property-asset-owner-address="$URL" 
      data-dh-property-asset-contract-address="$URL">
      
      <div 
        data-dh-property-tag-id="<<UniqueID>>" 
        data-dh-property-asset-item="true">
      
        <img data-dh-property-asset-json-path="image_url" />
        <h3 data-dh-property-asset-json-path="name"></h3>
        
      </div>
</div>
```

