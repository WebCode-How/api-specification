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
{
  "data": [
    {
      "id": 1,
      "content": "In 2008, Google officially released autocomplete and forever...",
      "demoUrl": "http://demo.webcode.how/ajax-autocomplete",
      "excerpt": "Learn how to make a simple AJAX-loading dynamic...",
      "slug": "how-to-make-an-ajax-autocomplete-for-a-search-input",
      "syntax": "javascript",
      "title": "How To Make An Ajax Autocomplete For A Search Input",
      "author": {
        "id": 3,
        "name": "Dean Papastrat",
        "pictureUrl": "http://cdn.webcode.how/3ijofscior.jpg"
      },
      "browser_support": {
        "browsers": [
          {
            "minimumVersion": "21",
            "type": "chrome"
          }
        ],
        "compatibilityTableUrl": "http://caniuse.com/input",
      },
      "demoRepository": {
        "downloadUrl": "https://github.com/WebCode-How/ajax-autocomplete/archive/master.zip",
        "name": "ajax-autocomplete",
        "websiteUrl": "https://github.com/WebCode-How/ajax-autocomplete"
      },
      "prerequisiteArticles": [
        {
          "excerpt": "Learn how to use the HTML input element.",
          "permalink": "http://webcode.how/how-to-make-an-html-input-element",
          "title": "How to Make an Input Element",
          "websiteName": "WebCode.How"
        }
      ],
      "furtherReadingArticles": [
        {
          "excerpt": "Learn how to make native dropdowns using the new HTML5 datalist element.",
          "permalink": "http://blog.teamtreehouse.com/creating-autocomplete-dropdowns-datalist-element",
          "title": "Creating Autocomplete Dropdowns with the Datalist Element",
          "websiteName": "Treehouse Blog"
        }
      ]
    }
  ],
  "paging": {
    "next": "http://api.webcode.how/articles?limit=25&until=1364849754"
    "previous": "http://api.webcode.how/articles?limit=25&since=1364587774"
  }
}
```

This endpoint retrieves all articles, ordered by the date they were published.

### HTTP Request

`GET http://api.webcode.how/articles`

### URL Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
limit | Integer | 25 | Number of articles to return, from 1 to 50
since | Unix Timestamp | null | Unix timestamp all articles returned must be published after
until | Unix Timestamp | null | Unix timestamp all articles returned must be published before

### Response Model \[CursoredData[Article]\]

Field | Type | Description
----- | ---- | -----------
data | Array[Article] | Array of Article objects; see  `/articles/ID or Slug`. Empty if no articles match.
paging | Paging | Contains metadata for paging over articles

#### Paging Object

Field | Type | Description
----- | ---- | -----------
next | String[URI] | Link to next page of articles. Null if no next page.
previous | String[URI] | Link to previous page of articles. Null if no previous page.

## Get An Article

```ruby
require 'webcode-api'

By ID:
webcode.articles(1)

By Slug:
webcode.articles("how-to-make-an-autocomplete-for-a-search-input")
```

```shell
# By ID:
curl "http://api.webcode.how/articles/1"

# By Slug:
curl "http://api.webcode.how/articles/how-to-make-an-autocomplete-for-a-search-input"
```

```javascript
const webcode = require('webcode-api');

# By ID:
let article = webcode.articles.get(1);

# By Slug:
let article = webcode.articles.get("how-to-make-an-autocomplete-for-a-search-input");
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "content": "In 2008, Google officially released autocomplete and forever...",
  "demoUrl": "http://demo.webcode.how/ajax-autocomplete",
  "excerpt": "Learn how to make a simple AJAX-loading dynamic...",
  "permalink": "http://webcode.how/how-to-make-an-ajax-autocomplete-for-a-search-input",
  "slug": "how-to-make-an-ajax-autocomplete-for-a-search-input",
  "syntax": "javascript",
  "title": "How To Make An Ajax Autocomplete For A Search Input",
  "author": {
    "id": 3,
    "name": "Dean Papastrat",
    "pictureUrl": "http://cdn.webcode.how/3ijofscior.jpg"
  },
  "browserSupport": {
    "browsers": [
      {
        "minimumVersion": "21",
        "type": "chrome"
      }
    ],
    "compatibilityTableUrl": "http://caniuse.com/input",
  },
  "demoRepository": {
    "downloadUrl": "https://github.com/WebCode-How/ajax-autocomplete/archive/master.zip",
    "host": "github",
    "name": "ajax-autocomplete",
    "websiteUrl": "https://github.com/WebCode-How/ajax-autocomplete"
  },
  "furtherReadingArticles": [
    {
      "excerpt": "Learn how to make native dropdowns using the new HTML5 datalist element.",
      "permalink": "http://blog.teamtreehouse.com/creating-autocomplete-dropdowns-datalist-element",
      "title": "Creating Autocomplete Dropdowns with the Datalist Element",
      "websiteName": "Treehouse Blog"
    }
  ],
  "prerequisiteArticles": [
    {
      "excerpt": "Learn how to use the HTML input element.",
      "permalink": "http://webcode.how/how-to-make-an-html-input-element",
      "title": "How to Make an Input Element",
      "websiteName": "WebCode.How"
    }
  ]
}
```

This endpoint retrieves an article.

### HTTP Request

`GET http://api.webcode.how/articles/<Slug|ID>`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
ID | Integer | The ID of the article to retrieve
Slug | String | The Slug of the article to retrieve

### Response Model \[Article\]

Field | Type | Description
----- | ---- | -----------
id | Integer | Unique integer representing article
content | String[HTML] | Tutorial content of article
demoUrl | String[URI] | Link to demo page for article
excerpt | String | Under 255 character summary of article
permalink | String[URI] | Link to article
slug | String | SEO-optimized unique identifier for article, used in permalink
syntax | String | Language the article was written for; One of: ["javascript", "coffeescript", "typescript", "jquery"]
title | String | Name of article
author | Author | Object representing who wrote the article
browserSupport | BrowserSupport | Object representing support of browser features used in article
demoRepository | Repository | Object representing the repository with sample code for article
furtherReadingArticles | Array[CondensedArticle] | Array of articles to read after finishing article
prerequisiteArticles | Array[CondensedArticle] | Array of articles indicating prior knowledge needed

#### Author Object

Field | Type | Description
----- | ---- | -----------
id | Integer | Unique integer representing author
name | String | Name of author
pictureUrl | String[URI] | Link to a picture of author

#### Browser Object

Field | Type | Description
----- | ---- | -----------
minimumVersion | String | Min. browser version for support of article's syntax
type | String | Unique identifier representing browser

#### BrowserSupport Object

Field | Type | Description
----- | ---- | -----------
browsers | Array[Browser] | Array of objects representing browsers supported by tutorial
compatibilityTableUrl | String[URI] | Link to chart showing support of features used

#### CondensedArticle Object

Field | Type | Description
----- | ---- | -----------
excerpt | String | Under 255 character summary of article
permalink | String[URI] | Link to article
title | String | Name of article
websiteName | String | Name of the website the article is on
