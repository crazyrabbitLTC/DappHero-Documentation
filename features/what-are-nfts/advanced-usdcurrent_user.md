---
description: Dynamically getting the address of the current user
---

# Advanced: $CURRENT\_USER

In situations where it doesn't make sense to hard-code the address of the user for which you would like to retrieve a Collectible or list of Collectibles, the special constant `$CURRENT_USER` can be used to dynamically insert the current users address. 

This constant can be used to help create dynamic websites with Collectibles. 

```markup
<div
    data-dh-feature="nft"
    data-dh-property-tag-id="<<UniqueID>>"
    data-dh-property-asset-token-id="<<TokenID>>"
    data-dh-property-asset-owner-address="$CURRENT_USER">
    
    <div 
        data-dh-property-tag-id="<<UniqueID>>" 
        data-dh-property-asset-item="true">
        
        <img data-dh-property-asset-json-path="image_url" />
        <h3 data-dh-property-asset-json-path="name"></h3>
    </div>
</div>
```

