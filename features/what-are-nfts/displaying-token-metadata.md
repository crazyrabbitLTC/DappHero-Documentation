# Displaying Token Metadata

Collectible tokens are based on the ERC721 standard, and most \(not all\) adhere to a [standard Metadata](https://docs.opensea.io/docs/metadata-standards) format popularized by OpenSea the online collectible marketplace. 

{% hint style="info" %}
We will be adding more information and support for metadata at a later date
{% endhint %}

### Loading Metadata

Metadata exists on collectibles as a JSON formatted object. On this object will be information that describes the various characteristics of the collectible. Because this metadata can be virtually anything, we have created a special tag `data-dh-property-asset-json-path` to help you access  it. 

Note: metadata can be potentially extremely nested data, `data-dh-property-asset-json-path` will do it's best to identify the piece of data you are specifically interested in, but for some complex objects or with repeating key names at different levels, it can struggle. Additionally, not all tokens respect the metadata format, even within the same collectible group. We will be releasing a new tag in the future to allow you to identify the exact data attribute you want in the future. 

#### Getting the token Name and ImageURL

Lets take a sample collectible JSON object: 

```javascript
{
  "description": "Friendly OpenSea Creature that enjoys long swims in the ocean.", 
  "external_url": "https://openseacreatures.io/3", 
  "image": "https://storage.googleapis.com/opensea-prod.appspot.com/puffs/3.png", 
  "name": "Dave Starbelly",
  "attributes": [ ... ], 
}
```

Here we have a description, an external URL, image, name and array of attributes. The top level elements, "image" or "name" for example can be access using the following tags: 

```markup
<div
      data-dh-feature="nft"
      data-dh-property-tag-id="000"
      data-dh-property-asset-owner-address="<<User Address>>">

      <div 
          data-dh-property-tag-id="000" 
          data-dh-property-asset-item="true">
        <img data-dh-property-asset-json-path="image_url" />
        <h3 data-dh-property-asset-json-path="name"></h3>
      </div>
</div>
```

In this example we are retrieving a list of collectibles owned by the `user address` the _method instance_ is described in the div from lines 1-4, the parent asset container is the div that opens on line 6 and closes on line 11. The children elements are the `img` tag which displays the token image and the `h3` tag which displays the assets name. As this is a list, it will display multiple tokens owned by this address, with the image and name coming from each respective token. 

For the "attributes" they currently are not natively accessibly via HTML tags, and will require the use of jQuery to access. Look forward to a future DappHero feature to handle this use case!





