---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='http://webcode.how' target='blank'>Check out WebCode.How</a>
  - <a href='https://github.com/tripit/slate' target='blank'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the WebCode.How API! You can use our API to access our articles and site metrics that are available publicly.

We have language bindings in Shell, Ruby, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/tripit/slate). We at WebCode.How send a giant thank you to the team that built this wonderful tool.

# Authentication

WebCode.How's public API requires no authentication and has no set rate limits.

Abuse of the API will result in your IP being blocked. Please do NOT perform so many requests that it looks like abuse.

# Articles

## Get All Articles

```ruby
require 'webcode-api'

articles = webcode.articles
```

```shell
curl "http://api.webcode.how/articles"
```

```javascript
const webcode = require('webcode-api');

let articles = webcode.articles.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "browser_support": {
      "browsers": [
        {
          "minimum_version": "21",
          "type": "chrome"
        }
      ],
      "compatibility_table_url": "http://caniuse.com/input",
    },
    "demo_repository": {
      "download_url": "https://github.com/WebCode-How/ajax-autocomplete/archive/master.zip",
      "name": "ajax-autocomplete",
      "website_url": "https://github.com/WebCode-How/ajax-autocomplete"
    },
    "demo_url": "http://demo.webcode.how/ajax-autocomplete",
    "slug": "how-to-make-an-ajax-autocomplete-for-a-search-input",
    "title": "How To Make An Ajax Autocomplete For A Search Input",
    "excerpt": "Learn how to make a simple AJAX-loading dynamic...",
    "content": "In 2008, Google officially released autocomplete and forever...",
    "author": {
      "id": 3,
      "name": "Dean Papastrat",
      "picture_url": "http://cdn.webcode.how/3ijofscior.jpg"
    }
    "prerequisite_articles": [
      {
        "id": 2,
        "excerpt": "Learn how to use the HTML input element.",
        "title": "How to Make an Input Element",
        "url": "http://webcode.how/how-to-make-an-html-input-element",
        "website_name": "WebCode.How"
      }
    ]
    "further_reading_articles": [
      {
        "id": null,
        "excerpt": "Learn how to make native dropdowns using the new HTML5 datalist element.",
        "title": "Creating Autocomplete Dropdowns with the Datalist Element",
        "url": "http://blog.teamtreehouse.com/creating-autocomplete-dropdowns-datalist-element",
        "website_name": "Treehouse Blog"
      }
    ]
  }
]
```

This endpoint retrieves all articles, ordered by the date t.

### HTTP Request

`GET http://api.webcode.how/articles`
