---
description: Getting the value of the current user as an input
---

# Advanced: Getting the Current User's Address Dynamically

## $CURRENT\_USER

A common use case for many smart contracts is to return information from a public view method that is associated with the current user. An example would be retrieving the balance of the current users ERC20 token amount. While you could create a normal input field and let a user populate it with their address, for many use cases this would be an inconvenient solution where you might want to show some smart contract state related to the current user on page load. 

To address this common use case,  we have created the reserved keyword **`$CURRENT_USER`** that can be used inside of inputs for smart contracts. 

```markup
<input
      data-dh-property-method-id="000"
      data-dh-property-input-name="<<input method argument name>>"
      value="$CURRENT_USER"
/>
```

In this example, the input field's value would be automatically populated with the value of the current users Ethereum address. 

The `$CURRENT_USER` keyword is particularly useful when the input is hidden. To do this, set the display value of the input to none. 

```markup
<input
      data-dh-property-method-id="000"
      data-dh-property-input-name="<<input method argument name>>"
      style="display:none;"
      value="$CURRENT_USER"
/>
```

