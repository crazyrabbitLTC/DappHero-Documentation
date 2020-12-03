---
description: Accessing the current users information
---

# User 🤖

The User feature allows you to access information about the currently connected user. 

{% hint style="info" %}
To access the current user, you must implement a [Network Enable](network.md#network-enable) element first. 
{% endhint %}

### Static User Features

Most user features are `static` features, meaning they are loaded as soon as the user clicks the `network enable` element.  Additionally, some User Features have formatting and display options that allow you to customize how the returned data is displayed to the user. 

### Current User Address Feature

 Display the current user's full Ethereum address:

```markup
<div
   data-dh-feature="user" 
   data-dh-property-address="true">
   *User Address*
</div>

```

| Tag | Accepted Values | Required |
| :--- | :--- | :--- |
| `data-dh-feature` | `user` | Yes |
| `data-dh-property-address`   | `true` `false` | Yes |
| `data-dh-modifier-display` | `short` | optional  |

### Displaying Shortened Addresses 

To show a truncated address, you can also add `data-dh-modifier-display="short"` to the element like the example below:

```markup
<h2
   data-dh-feature="user" 
   data-dh-property-address="true"
   data-dh-modifier-display="short">
   *User Address Truncated*
</h2>
```

This will display the address in the following format `0x5...EaEA`

### 

### User Balance

Display the current user's balance:

```markup
<div
    data-dh-feature="user"
    data-dh-property-balance>
    *User Balance*
</div>
```

**Example Return Value:** `7511222555444777333`

### Define the units and precision of the balance 

To show the user's balance in ether add `data-dh-modifier-display-units="ether"`

To define the number of decimal places add `data-dh-modifier-units=3`

```markup
<div
          data-dh-feature="user"
          data-dh-property-balance
          data-dh-modifier-units="ether" 
          data-dh-modifier-decimals="3">
          *User Balance*
</div>
```

| Tag | Accepted Values | Required |
| :--- | :--- | :--- |
| `data-dh-feature` | `user` | Yes |
| `data-dh-property-balance`   | none | Yes |
| `data-dh-modifier-units` | `ether` `wei` | optional  |
| `data-dh-modifier-decimals` | `integer` | optional |

