## Add or Update an Item

```shell
# search suggestion
curl -X PUT -H "Content-Type: application/json" \
  -d '{"item_name": "Golden Retriever", \
       "autocomplete_section": "Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"

# product
curl -X PUT -H "Content-Type: application/json" \
  -d '{"item_name": "Labradoodle", \
       "autocomplete_section":"Products", \
       "suggested_score": 360, \
       "keywords": ["poodle","labrador","retriever"],
       "url": "http://www.mydogs.com/labradoodle", \
       "image_url": "https://images.mydogs.com/labradoodle.jpg", \
       "description": "A crossbreed dog created by crossing the Labrador Retriever and the Poodle"}, \
       "metadata": { "animal": "dog" }'
  -u"[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"
```

```javascript
// search suggestion
constructorio.add_or_update(
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
constructorio.add_or_update(
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
response = constructorio.add_or_update(
  {
    item_name: "Golden Retriever",
    autocomplete_section: "Search Suggestions"
  }
);

# product
response = constructorio.add_or_update(
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
response = constructor_instance.add_or_update(
    item_name="Golden Retriever",
    autocomplete_section="Search Suggestions")

# product
response = constructor_instance.add_or_update(
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
$response = $constructorio->addOrUpdate(
  "Golden Retriever", // item name
  "Search Suggestions" // autocomplete section name
);

// product
$response = $constructorio->addOrUpdate(
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
my $response = $constructorio->add_or_update(
  item_name => "Golden Retriever",
  autocomplete_section => "Search Suggestions"
);

# product
my $response = $constructorio->add_or_update(
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
boolean success = constructorio.addOrUpdate("Golden Retriever", "Search Suggestions");
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

boolean success = constructorio.addOrUpdate(
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
bool success = ConstructorIOAPI.AddOrUpdate(item);

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
bool success = ConstructorIOAPI.AddOrUpdate(item);
```

 > The above commands return a 204 Success response on success.

An add or update operation (also known as an `UPSERT`) updates an item in your autocomplete index if it already exists, or adds the item to your index if it does not yet exist. 

To add or update an item in your autocomplete index, use the `PUT /item` call, with `?force=1`. Options are the same as for the standard `Add an Item` call: `item_name` and `autocomplete_section` are required and all other parameters are optional.

We determine whether an item already exists based on the optional `id` set for the item, or if not present, the `item_name` and `autocomplete_section`.

### HTTP Request

`PUT https://ac.cnstrc.com/v1/item?force=1&autocomplete_key=[your autocomplete key]`

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
