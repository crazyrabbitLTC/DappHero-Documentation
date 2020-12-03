---
description: How to programmatically force refresh the DappHero Engine
---

# Force Refresh

{% hint style="danger" %}
Force Refresh functionality is experimental.
{% endhint %}

For more advanced use cases, such as manipulation of the DOM via external script such as jQuery, it can be useful to force DappHero to refresh its view of the user's DOM. 

An example use case would be using jQuery to append new DOM elements to the user's webpage. DappHero by default only scans the DOM once, at page load, so if DappHero enabled elements are programmatically added to the DOM after page load, the engine will not be aware of them.  

Additionally, the DappHero core engine does not "watch" the user's DOM, so if a DappHero powered website element is altered via a script, the engine will not be aware of the change. For example, if you were to use jQuery to change the input value of a form field or the value of an invisible input for an auto-invoked method, DappHero will be unaware of this change. 

To assist builders looking to add functionality via external scripts, we have exposed a function on the window that when called will trigger a refresh of the DappHero engine. Call this function at the end of any external script manipulation to ensure DappHero always has the most recent version of the DOM. 

```text
window.dappHero.retriggerEngine()
// or without window
dappHero.retriggerEngine()
```

By invoking the `retriggerEngine()` function, DappHero will re-run and recheck the webpage DOM for changes. 



