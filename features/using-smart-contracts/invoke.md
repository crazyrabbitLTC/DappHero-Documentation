---
description: Activating Methods on page load or button click
---

# Invoke

Once you've created your Smart Contract method instance, optionally gathered your users inputs \(not all methods require inputs!\) now we need to _invoke_ our method- **Activate it!**

We can invoke a method in one of two ways: on page load, when your website first loads for the user, or by clicking a button.

#### Invoke on Page Load

To invoke on page load, all you need to do is add `data-dh-property-auto-invoke="true"` to the **method instance** element we created earlier \(thats the one that has the `data-dh-property-contract-name` and `data-dh-property-method-name` attributes.

```markup
<div
    data-dh-feature="customContract"
    data-dh-property-contract-name="dappherotest"
    data-dh-property-method-name="hello"
    data-dh-property-method-id="000"
    data-dh-property-auto-invoke="true"
>
```

This will now auto-invoke a method on page load. This is useful for when you want to pre-populate some data on your website from a smart contract without needing to user to click on a button first. 

For auto-invoked methods which require inputs, use [Invisible Inputs](inputs.md#invisible-inputs).

{% hint style="info" %}
Invoke on page Load will only work for View Methods. Transactions can not be invoked on page.
{% endhint %}

#### Invoke on Button Click

If you want your user to invoke the method, create a button instance and add the tag `data-dh-property-invoke` this will tell the DappHero engine to invoke the smart contract method when the button is clicked.

```markup
<button 
    data-dh-property-method-id="000" 
    data-dh-property-invoke="true"
>
Click Here to Call Your Smart Contract!
</button>
```

### Invoke Reference

| Tag | Value | Required |
| :--- | :--- | :--- |
| `data-dh-property-invoke` | true | yes |
| `data-dh-property-auto-invoke` | true | optional |
| `data-dh-property-method-id` | `<<yourUniqueIdentifier>>` | yes |



