## Add an Item

```shell
# search suggestion
curl -X POST -H "Content-Type: application/json" \
  -d '{"item_name": "Golden Retriever", \
       "autocomplete_section": "Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"

# product
curl -X POST -H "Content-Type: application/json" \
  -d '{"item_name": "Labradoodle", \
       "autocomplete_section":"Products", \
       "suggested_score": 360, \
       "keywords": ["poodle","labrador","retriever"], \
       "url": "http://www.mydogs.com/labradoodle", \
       "image_url": "https://images.mydogs.com/labradoodle.jpg", \
       "description": "A crossbreed dog created by crossing the Labrador Retriever and the Poodle", \
       "metadata": { "animal": "dog" }' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"
```

```javascript
// search suggestion
constructorio.add(
  {
    item_name: "Golden Retriever",
    autocomplete_section: "Search Suggestions"
  },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);

// product
constructorio.add(
  {
    item_name: "Labradoodle",
    autocomplete_section: "Products",
    suggested_score: 360,
    keywords: ["poodle","labrador","retriever"],
    url: "http://www.mydogs.com/labradoodle",
    image_url: "https://images.mydogs.com/labradoodle.jpg",
    description: "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
    metadata: { "animal": "dog" }
  },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);
```

```ruby
# search suggestion
response = constructorio.add(
  {
    item_name: "Golden Retriever",
    autocomplete_section: "Search Suggestions"
  }
);

# product
response = constructorio.add(
  {
    item_name: "Labradoodle",
    autocomplete_section: "Products",
    suggested_score: 360,
    keywords: ["poodle","labrador","retriever"],
    url: "http://www.mydogs.com/labradoodle",
    image_url: "https://images.mydogs.com/labradoodle.jpg",
    description: "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
    metadata: { "animal": "dog" }
  }
);
```

```python
# search suggestion
response = constructor_instance.add(
    item_name="Golden Retriever",
    autocomplete_section="Search Suggestions")

# product
response = constructor_instance.add(
    item_name="Labradoodle",
    autocomplete_section="Products",
    suggested_score=360,
    keywords=["poodle","labrador","retriever"],
    url="http://www.mydogs.com/labradoodle",
    image_url="https://images.mydogs.com/labradoodle.jpg",
    description="A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
    metadata={ "animal": "dog" })
```

```php
<?php
// search suggestion
$response = $constructorio->add(
  "Golden Retriever", // item name
  "Search Suggestions" // autocomplete section name
);

// product
$response = $constructorio->add(
  "Labradoodle", // item name
  "Products", // autocomplete section name
  array(
    "suggested_score" => 360,
    "keywords" => array("poodle", "labrador", "retriever"),
    "url" => "http://www.mydogs.com/labradoodle",
    "image_url" => "https://images.mydogs.com/labradoodle.jpg",
    "description" => "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
    "metadata" => array(
      "animal" => "dog"
    )
  );
);
```

```perl
# search suggestion
my $response = $constructorio->add(
  item_name => "Golden Retriever",
  autocomplete_section => "Search Suggestions"
);

# product
my $response = $constructorio->add(
  item_name => "Labradoodle",
  autocomplete_section => "Products",
  suggested_score => 360,
  keywords => ["poodle","labrador","retriever"],
  url => "http://www.mydogs.com/labradoodle",
  image_url => "https://images.mydogs.com/labradoodle.jpg",
  description => "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
  metadata => { "animal" => "dog" }
);
```

```java
// search suggestion
boolean success = constructorio.add("Golden Retriever", "Search Suggestions");
// "Golden Retriever" is an item name
// "Search Suggestions" is an autocomplete section name

// product
HashMap<String, Object> params = new HashMap<String, Object>();
params.put("suggested_score", 360);
params.put("url", "http://www.mydogs.com/labradoodle");
params.put("image_url", "https://images.mydogs.com/labradoodle.jpg");
params.put("description", "A crossbreed dog created by crossing the Labrador Retriever and the Poodle");

ConstructorItem item = new ConstructorItem("Labradoodle", params);
item.setKeywords("poodle","labrador","retriever");

boolean success = constructorio.add(
  item,
  "Products"
);

```

```csharp
// search suggestion
ListItem item = new ListItem(
  Name: "Golden Retriever",
  AutocompleteSection: "Search Suggestion"
);
bool success = ConstructorIOAPI.Add(item);

// product
ListItem item = new ListItem(
  Name: "Labradoodle",
  AutocompleteSection: "Products",
  SuggestedScore: 360,
  Keywords: new string[]
  {
    "poodle",
    "labrador",
    "retriever"
  },
  URL: "http://www.mydogs.com/labradoodle",
  ImageURL: "https://images.mydogs.com/labradoodle.jpg",
  Description: "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
  Metadata: new Dictionary<string, string>
  {
      { "animal", "dog" }
  });
);
bool success = ConstructorIOAPI.Add(item);
```

> The above command returns a 204 Success response on success.

To add an item to your autocomplete index, use the `POST /item` call. The `item_name` is required. You can also pass in an optional `suggested_score` between 1 and 100 million, which will influence the item's initial ranking relative to other item scores (the higher the score, the higher in the list of suggestions the item will appear). You can also optionally pass in the item's `keywords` to give us more meta information and help us better determine how and where to display the item when autocompleting. If you would like to add an item that points to a direct link, just pass in that link as a `url`. Finally, because your autocomplete can have multiple sections, like categories, search suggestions, and direct links to products, you must specify which section you are adding an item to. You can do this with the `autocomplete_section` parameter.

### HTTP Request

`POST https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ------- | -----------
item_name | Yes | The name of the item, as it will appear in the autocomplete suggestions
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
suggested_score | No | A number between 1 and 100 million that will influence the item's initial ranking relative to other item scores (the higher the score, the higher in the list of suggestions the item will appear)
keywords | No | An array of keywords for this item.  Keywords are useful if you want a product name to appear when a user enters a searchterm that isn't in the product name iteslf.
url | No | A URL to directly send the user after selecting the item
image_url | No | A URL that points to an image you'd like displayed next to some item (only applicable when url is supplied)
description | No | A description for some item (only applicable when url is supplied)
id | No | An arbitrary ID you would like associated with this item.  You can use this field to store your own IDs of the items to more easily access them in other API calls.
metadata | No | You can associate schema-less data with items by passing in an array of keys and values. To configure search and display of this data reach out to support@constructor.io.
