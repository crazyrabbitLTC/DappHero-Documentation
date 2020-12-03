---
description: A simple end-to-end encrypted database in the browser
---

# Database

{% hint style="info" %}
This is an experimental feature, have fun, but remember it \*could\* break
{% endhint %}

### Details

The DappHero database is a super simple, in browser, end-to-end encrypted database that can be access directly from the window object in the browser. 

Each database is scoped to the `ProjectId` of your project and can be used as a fast, efficient `key:value` store. 

Users are scoped to DappHero, so a user that signs up at any DappHero site will also be a valid user on your site and vice versa. The Database however is not shared, so the data available to you will be specific to your projectId. 

The data in the database is encrypted client side in the browser for each user and is backed up to Amazon AWS in an encrypted format. DappHero can not access this data and can not retrieve user credentials, so if they lose their login- it's gone. 

All functions are async. DappHero Database is based on [UserBase](www.userbase.io).

### signUp

`window.dapphero.db.signUp({username: "my name", password: "xxxxx"})`

### signIn

`window.dapphero.db.signIn({username, password})`

### signOut

`window.dapphero.db.signOut()`

### openDatabase

`window.dapphero.db.openDatabase(callbackToReceiveDatabase)`

### insertItem

`window.dapphero.db.insertItem(item)`

### updateItem

`window.dapphero.db.updateItem(item, itemId)`

### deleteItem

`window.dapphero.db.deleteItem(itemId)`

### 

