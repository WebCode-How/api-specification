# Search

## Query WebCode.How

```json
{
  "data": [
    {
      "description": "Learn how to make a simple AJAX-loading dynamic...",
      "permalink": "http://webcode.how/how-to-make-an-autocomplete-for-a-search-input",
      "title": "How To Make An Ajax Autocomplete For A Search Input",
      "type": "article"
    }
  ],
  "paging": {
    "next": "http://api.webcode.how/search?q=myquery&limit=25&before=10"
    "previous": "http://api.webcode.how/search?q=myquery&limit=25&after=20"
  }
}
```

```xml
<?xml version="1.0" encoding="utf-8" ?>
<data>
  <searchItem>
    <description>Learn how to make a simple AJAX-loading dynamic...</description>
    <permalink>http://webcode.how/how-to-make-an-autocomplete-for-a-search-input</permalink>
    <title>How To Make An Ajax Autocomplete For A Search Input</title>
    <type>article</type>
  </searchItem>
</data>
<paging>
  <next>http://api.webcode.how/search?q=myquery&limit=25&before=10</next>
  <previous>http://api.webcode.how/search?q=myquery&limit=25&after=20</previous>
</paging>
```

This endpoint searches WebCode.How's articles, ordered by relevance. Author support is roadmapped.

### HTTP Request

`GET http://api.webcode.how/search?q=<Slug|ID>`

### URL Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
format | String | json | Format to return; one of: ["json", "xml"]
q | String | Search string to query for

### Response Model

### Response Model \[CursoredData[SearchItem]\]

Field | Type | Description
----- | ---- | -----------
data | Array[SearchItem] | Array of Search Items
paging | Paging | Contains metadata for paging over articles

#### Paging Object

Field | Type | Description
----- | ---- | -----------
next | String[URI] | Link to next page of articles. Null if no next page.
previous | String[URI] | Link to previous page of articles. Null if no previous page.

#### Search Item

Field | Type | Description
----- | ---- | -----------
description | String | Under 255 character description of search item, such as a bio or excerpt
title | String | Under 255 character title of search item
permalink | String[URI] | Link to the full resource for search item
type | String | Type of result; One of: ["author", "article"]
