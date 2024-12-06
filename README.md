# Shopify Short Titles
We can all agree that SEO is important to get people to your website. But once they're there, good design is just as important. For my shop, I wanted the best of both worlds, so I wrote some code[^1] to shorten my product titles on the website's frontend while they maintained their long SEO-formatted titles within the Shopify Admin.

![Shopify Liquid Badge](https://img.shields.io/badge/-Shopify%20Liquid-750460)


## Table of Contents
* [Usage](#usage)   
* [Code](#code)    
* [Questions](#questions) 
* [Donate](#donate)
* [Notes](#notes)


## Usage
Within the Shopify Admin, I have a title format that I use across all products to better my website's SEO and ensure my products are showing up when people are searching for them online. This full title appears in several important places including order confirmation emails, packing slips, share previews, and search engine results.
| Formula | Examples |
| :--- | :--- |
| `Product Name` `Product Type` by `Product Vendor` | Progress Pride Enamel Pin by Pinultimate<br>Internet Friends Enamel Pin Set by Pretty Useful Co.<br>Creator's Club Suncatcher by A Fink & Ink |

With this long format, a user can quickly identify:
* The name of the product
* What the product is
* Who made the product

Anyone searching for just one of those 3 things could also happen upon my shop, so it's important to have all of this information embeded within the actual product. However, once a user has clicked through to my shop, a lot of the product information becomes visual.

Each product card includes the following:
* Product Image
* Product Title
* Product Vendor
* Product Price

In this new format, the long title is redundant. We already have the product vendor listed, so we can remove that from the title. At this point, the user also knows what product they're shopping for (pins), so we can go the extra step to shorten 'enamel pin' to just 'pin':
| Full Product Title | Short Title |
| :--- | :--- |
| <img width="250" alt="dog" src="https://github.com/user-attachments/assets/352fe8f1-9e26-40b6-ba69-e53c6ce83f03"><br>**Labrador Retriever Enamel Pin<br>by Doggie Drawings**<br>Doggie Drawings<br>$15.00 | <img width="250" alt="dog" src="https://github.com/user-attachments/assets/352fe8f1-9e26-40b6-ba69-e53c6ce83f03"><br>**Labrador Retriever Pin**<br>Doggie Drawings<br>$15.00 |

A user scrolling through our products should be able to easily consume the content on the page, and with this short title format, we're left with a visual representation of each product that is clean and straight to the point.



## Code

:file_folder: **snippets/product-item.liquid**

Search for `{%- when 'title' -%}` and replace `{%- liquid -%}` snippet with:
```
{% comment %} [LG] Short Title {% endcomment %}
{%- liquid 
  assign fullTitle = product.title | split: " by "
  assign shortTitle = fullTitle[0] | remove: "Enamel "
  echo shortTitle | escape
-%}
{% comment %} [LG] End Short Title {% endcomment %}
```

:file_folder: **sections/main-product.liquid**

Search for `{%- when 'title' -%}` and replace contents inside `<h1>` with:
```
{% comment %} [LG] Short Title {% endcomment %}
{%- liquid 
  assign fullTitle = product.title | split: " by "
  assign shortTitle = fullTitle[0] | remove: "Enamel "
  echo shortTitle | escape
-%}
{% comment %} [LG] End Short Title {% endcomment %}
```


## Questions
If you have any questions, feel free to find me at:
* Email: laurenguardala@gmail.com
* Website: [larguar.com](https://larguar.com)
* Github: [@larguar](https://github.com/larguar)


## Donate
Appreciate this code? Say thanks with a coffee:

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/W7W21YVJJ)


## Notes
[^1]: This code is specific to the [Combine](https://themes.shopify.com/themes/combine/styles/objects) theme in Shopify, but should work for other themes with some adjustments. File names will likely be different across themes.
