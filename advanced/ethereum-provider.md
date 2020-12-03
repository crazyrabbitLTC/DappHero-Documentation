---
description: Connecting to the exposed ethereum provider with DappHero
---

# Ethereum Provider

For more builders who are incorporating DappHero on mixed technology websites, we have offered the ability to get access to the underlying Ethereum Provider. 

### Window object

An [Ethers.js](https://docs.ethers.io/ethers.js/html/) \(v5\) powered Ethereum provider is available at `window.dappHero.provider`. This provider can be used to create new connections to the Ethereum blockchain without needing DappHero.

```text
window.dappHero.provider
// or without window
dappHero.provider
```

