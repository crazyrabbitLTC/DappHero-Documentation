---
description: How to enable or disable automatically clearing a form input field
---

# Advanced: Automatically clearing Inputs

When using a HTML Input form field as an input to a smart contract method, DappHero will automatically clear the value of the input form field after each invocation \(IE: each time someone click the submit button\). This behavior was designed to give users a familiar experience when interacting with a DH powered and to make user their inputs are cleared. 

However there are some situation where clearing the input field might not be desired, so we have included the ability to override this functionality. 

### Overriding the default functionality

To override the default functionality, it is necessary to add `auto-clear` flag with a value, `true` or `false`. This should be added any input for which you wish to change the default functionality, or perhaps give the ability to change the functionality while loaded on the page. 

```markup
<input
    data-dh-property-method-id="000"
    data-dh-property-input-name="simpleMessage"
    data-dh-property-auto-clear="false"
/>
```

| Tag | Property | Required? |
| :--- | :--- | :--- |
| auto-clear | true/false | optional |

If there is no `auto-clear` flag, DappHero will clear the input value after the first invocation. 

Learn more about using `auto-clear` with [invisible inputs](inputs.md#invisible-inputs).

