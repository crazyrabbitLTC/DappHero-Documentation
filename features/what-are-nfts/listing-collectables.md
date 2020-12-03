---
description: How to display lists of Collectibles
---

# Listing Collectibles

## General Concepts

Lists in DappHero work a bit different than most features. With lists, we create first an _instance_ of our feature, we then also create a _container_ that represents the data we wish to display. When our website is live, the DappHero engine will duplicate the container for each piece of data inside our "list" that is returned. 

The _container_ in DappHero is created by assigning an HTML element a `data-dh-property-asset-item` tag and a `UniqueID` which matches our _instance_ `UniqueID`. The DappHero engine will recognize this block of HTML as the block you wish to duplicated for each Collectible item for which you want to display information and can be used to create exciting dynamic lists with barely any code! 

The Collectible feature is powered by the [OpenSea API](https://opensea.io/) and will only return tokens indexed by their mainnet service \(currently over 10 million items\).

#### List all Collectibles owned by an address

To list all the Collectible tokens that are owned by an address, it is necessary to provide only the owners address. This can be a contract address or a users address and it will return a list of all the tokens owned by this address, regardless of Collectible contract address. 

```markup
<!-- This top level div is the method Instance -->
<div
      data-dh-feature="nft"
      data-dh-property-tag-id="<<UniqueID>>"
      data-dh-property-asset-owner-address="<<address>>">
      
      <div data-dh-property-tag-id="<<UniqueID>>" 
           data-dh-property-asset-item="true">
      
        <img data-dh-property-asset-json-path="image_url" />
        <h3 data-dh-property-asset-json-path="name"></h3>
        
      </div>
</div>
```

#### Filtering by Contract Address

To filter by a specific contract address, add the line `data-dh-property-asset-contract-address="<<Address>>"` and it will filter for only the contracts owned by the user of this particular collectible contract. This is useful, for example, to show all the CryptoKitties owned by a single address.

#### List of all Collectibles by Collectible contract address

To list all the collectibles created by a specific contract, it is necessary only to provide the collectible contract address. The order displayed will be the order returned from the OpenSea API. 

```markup
<!-- This top level div is the method Instance -->
<div
      data-dh-feature="nft"
      data-dh-property-tag-id="<<UniqueID>>"
      data-dh-property-asset-contract-address="<<Address>>">
      
      <div data-dh-property-tag-id="<<UniqueID>>" 
           data-dh-property-asset-item="true">
           
        <img data-dh-property-asset-json-path="image_url" />
        <h3 data-dh-property-asset-json-path="name"></h3>
        
      </div>
</div>
```

### List of specific Collectibles by owner

```markup
<div
      data-dh-feature="nft"
      data-dh-property-tag-id="<<UniqueID>>"
      data-dh-property-asset-token-id="list of ids, 1,2,3"
      data-dh-property-asset-owner-address="<<Address>>">
      
      <div data-dh-property-tag-id="<<UniqueID>>" 
           data-dh-property-asset-item="true">
        
        <img data-dh-property-asset-json-path="image_url" />
        <h3 data-dh-property-asset-json-path="name"></h3>
        
      </div>
</div>
```

In this case: 

```markup
data-dh-property-asset-token-id="list of ids, 1,2,3"
```

The List of IDs is a list that is formatted as a comma separated array of values. So in this case if we wanted to see the tokens 101,102,103 of the owner of `address` we would do: 

```markup
data-dh-property-asset-token-id="101,102,103"
```

{% hint style="warning" %}
Note: When listing a specific group of tokens with the `data-dh-property-asset-token-id` tag, you will not be able to combine it with the `pagination-offset` or `pagination-limit` tags. The result will return no tokens. 
{% endhint %}

## Pagination and Limits

When working with lists of Collectible tokens, controlling the number of items retrieved from the API or displayed to the user is very important. To do this we have created pagination modifiers that allow you to control the number of items displayed, and to add handy pagination buttons to give users the chance to page through large sets of items. 

| Tag | Property | Required |
| :--- | :--- | :--- |
| `data-dh-property-pagination-limit` | integer | optional |
| `data-dh-property-pagination-offset` | integer | optional |
| `data-dh-property-pagination-prev` | none | optional |
| `data-dh-property-pagination-next` | none | optional |

#### pagination-limit

This is the number of tokens you want returned in a list. The default is 20 and the max is 300. This is also the number of tokens that will be displayed on your website. This can be used without `pagination-prev` or `pagination-next` to limit the number of displayed results. 

#### pagination-offset

In situations where the number of Collectible tokens returned \(for example: all the CryptoKitties\) is greater than you can display, the `pagination-offset` value allows you to choose from where in the list you start displaying the Collectibles. So for example, if you have a limit of 20 out of a possible total of 40, then an offset of 0 would display Collectibles 1-20, while an offset of 1 would display Collectibles 21-40.

#### pagination-prev

By attaching `data-dh-property-pagination-prev` to a button element, by clicking on the button users will be able to move backwards in the list.

#### pagination-next

The opposite of `pagination-prev`

```markup
<div
      data-dh-feature="nft"
      data-dh-property-tag-id="<<UniqueID>>"
      ...
      data-dh-property-pagination-limit="<<number of tokens>>"
      data-dh-property-pagination-offset="<<the offset>>"
      data-dh-property-asset-owner-address="<<Address>>">
      

      <button data-dh-property-tag-id="<<UniqueID>>" 
      data-dh-property-pagination-prev="true">prev</button>
      

      <button data-dh-property-tag-id="<<UniqueID>>" 
      data-dh-property-pagination-next="true">next</button>

      <div data-dh-property-tag-id="<<UniqueID>>" 
           data-dh-property-asset-item="true">
           
        <img data-dh-property-asset-json-path="image_url"/>
        <h3 data-dh-property-asset-json-path="name"></h3>
      
      </div>
</div>
```

These tags effectively lets us "page" through a long list of results. This is useful if you wish to limit the number of resulting tokens that are displayed on a single page. This can be helpful for design when for example, you want to show only a single token per page and allow the users to page through through the like a gallery. 

