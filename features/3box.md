---
description: Learn how to access decentralized 3Box user profiles
---

# 3box 👯‍♂️

[3box](https://3box.io/) offers a decentralized storage layer for applications. Currently if a user has created a [3box profile](https://3box.io/hub) with the address they use when visiting your site, you will be able to use DappHero to access their profile information. 

{% embed url="https://webflow.com/website/DappHero-3box-profile" caption="Click \"clone\" to make it yours!" %}

You may want to consider adding some placeholder or default text, as some users will not have set up their 3box profiles. In addition, some users will only have uploaded parts of their profile leaving certain properties blank.

### 3Box Feature Reference

| Tag | Property | Required | Displays |
| :--- | :--- | :--- | :--- |
| `data-dh-feature` | "threebox" | Yes | nothing |
| `data-dh-property-name` | "true" | optional | Users Name |
| `data-dh-property-website` | "true" | optional | Users Website |
| `data-dh-property-location` | "true" | optional | Users Location |
| `data-dh-property-emoji` | "true" | optional | Users Emoji |
| `data-dh-property-job` | "true" | optional | Users Job |
| `data-dh-property-description` | "true" | optional | Users Description |
| **Three Box Image** | \*\*\*\* |  |  |
| `data-dh-property-image` | "true" | optional | Users Image |

To access any of the above properties, with the exception of the image property, follow this template, replacing the property with your desired property value. 



### Display the current user's 3Box Name

```markup
<div
    data-dh-feature="threebox"
    data-dh-property-name="true"
>
    Name will be displayed here
</div>
```

### Display the current user's 3Box Profile Image

To access a user's profile image, it is important to attach the feature to an image element. 

```markup
<img
    src="placeholder image URL"
    data-dh-feature="threebox"
    data-dh-property-image="true"
>
```

