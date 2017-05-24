## Batch Add or Update Items

```shell
curl -X PUT -H "Content-Type: application/json" \
  -d '{"items": [ {"item_name": "Golden Retriever"}, {"item_name": "Poodle"} ], \
    "autocomplete_section":"Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/batch_items?force=1&autocomplete_key=[your autocomplete key]"

# products
curl -X PUT -H "Content-Type: application/json" \
  -d '{ \
        "autocomplete_section":"Products", \
        "items": [ \
          { \
            "item_name": "Labradoodle", \
            "suggested_score": 360, \
            "keywords": ["poodle","labrador","retriever"], \
            "url": "http://www.mydogs.com/labradoodle", \
            "image_url": "https://images.mydogs.com/labradoodle.jpg", \
            "description": "A crossbreed dog created by crossing the Labrador Retriever and the Poodle", \
            "metadata": { "animal": "dog" } \
          }, \
            "item_name": "Australian Shepherd", \
            "suggested_score": 130, \
            "keywords": ["aussie"], \
            "url": "http://www.mydogs.com/australian_shepherd", \
            "image_url": "https://images.mydogs.com/australian_shepherd.jpg", \
            "description": "A medium-sized breed of dog developed on ranches in the Western United States", \
            "metadata": { "animal": "dog" } \
          }, \
        ] \
      }' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/batch_items?force=1&autocomplete_key=[your autocomplete key]"
```

```javascript
// search suggestions
constructorio.add_or_update_batch(
  {
    autocomplete_section: "Search Suggestions",
    items: [
      { item_name: "Golden Retriever" },
      { item_name: "Poodle" }
    ]
  },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);

// products
constructorio.add_or_update_batch(
  {
    autocomplete_section: "Products",
    items: [
      {
        item_name: "Labradoodle",
        suggested_score: 360,
        keywords: ["poodle","labrador","retriever"],
        url: "http://www.mydogs.com/labradoodle",
        image_url: "https://images.mydogs.com/labradoodle.jpg",
        description: "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
        metadata: { "animal": "dog" }
      },
      {
        item_name: "Australian Shepherd",
        suggested_score: 130,
        keywords: ["aussie"],
        url: "http://www.mydogs.com/australian_shepherd",
        image_url: "https://images.mydogs.com/australian_shepherd.jpg",
        description: "A medium-sized breed of dog developed on ranches in the Western United States",
        metadata: { "animal": "dog" }
      }
    ]
  },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);
```

```ruby
# search suggestions
response = constructorio.add_or_update_batch(
  {
    autocomplete_section: "Search Suggestions",
    items: [
      { item_name: "Golden Retriever" },
      { item_name: "Poodle" }
    ],
  }
);

# products
response = constructorio.add_or_update_batch(
  {
    autocomplete_section: "Products",
    items: [
      {
        item_name: "Labradoodle",
        suggested_score: 360,
        keywords: ["poodle","labrador","retriever"],
        url: "http://www.mydogs.com/labradoodle",
        image_url: "https://images.mydogs.com/labradoodle.jpg",
        description: "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
        metadata: { animal: "dog" }
      },
      {
        item_name: "Australian Shepherd",
        suggested_score: 130,
        keywords: ["aussie"],
        url: "http://www.mydogs.com/australian_shepherd",
        image_url: "https://images.mydogs.com/australian_shepherd.jpg",
        description: "A medium-sized breed of dog developed on ranches in the Western United States",
        metadata: { animal: "dog" }
      }
    ]
  }
)
```

```python
# search suggestions
items = response = constructor_instance.add_or_update_batch(
  autocomplete_section="Search Suggestions",
  items=[
    {"item_name": "Golden Retriever"},
    {"item_name": "Poodle"}
  ]
)

# products
response = constructor_instance.add_or_update_batch(
    autocomplete_section="Products",
    items=[
      {
        "item_name": "Labradoodle",
        "suggested_score": 360,
        "keywords": ["poodle","labrador","retriever"],
        "url": "http://www.mydogs.com/labradoodle",
        "image_url": "https://images.mydogs.com/labradoodle.jpg",
        "description": "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
        "metadata": { "animal": "dog" }
      },
      {
        "item_name": "Australian Shepherd",
        "suggested_score": 130,
        "keywords": ["aussie"],
        "url": "http://www.mydogs.com/australian_shepherd",
        "image_url": "https://images.mydogs.com/australian_shepherd.jpg",
        "description": "A medium-sized breed of dog developed on ranches in the Western United States",
        "metadata": { "animal": "dog" }
      }
    ]
)
```

```php
<?php
$response = $constructor->addOrUpdateBatch(
  array("Golden Retriever", "Poodle"),
  "Search Suggestions"
);

// products
$response = $constructor->addOrUpdateBatch(
  array(
     array(
      "item_name" => "Labradoodle",
      "suggested_score" => 360,
      "keywords" => ["poodle","labrador","retriever"],
      "url" => "http://www.mydogs.com/labradoodle",
      "image_url" => "https://images.mydogs.com/labradoodle.jpg",
      "description" => "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
      "metadata" => array( "animal" => "dog" )
     ),
     array(
      "item_name" => "Australian Shepherd",
      "suggested_score" => 130,
      "keywords" => ["aussie"],
      "url" => "http://www.mydogs.com/australian_shepherd",
      "image_url" => "https://images.mydogs.com/australian_shepherd.jpg",
      "description" => "A medium-sized breed of dog developed on ranches in the Western United States",
      "metadata" => array( "animal" => "dog" )
     )
  )
  , "Products");
```

```perl
# search suggestions
my $response = $constructorio->add_or_update_batch(
  autocomplete_section => "Search Suggestions",
  items => [
    { item_name => "Golden Retriever" },
    { item_name => "Poodle" }
  ]
);

# products
my $response = $constructorio->add_or_update_batch(
  autocomplete_section: "Products",
  items: [
    {
      item_name => "Labradoodle",
      suggested_score => 360,
      keywords => ["poodle","labrador","retriever"],
      url => "http://www.mydogs.com/labradoodle",
      image_url => "https://images.mydogs.com/labradoodle.jpg",
      description => "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
      metadata => { animal => "dog" }
    },
    {
      item_name => "Australian Shepherd",
      suggested_score => 130,
      keywords => ["aussie"],
      url => "http://www.mydogs.com/australian_shepherd",
      image_url => "https://images.mydogs.com/australian_shepherd.jpg",
      description => "A medium-sized breed of dog developed on ranches in the Western United States",
      metadata => { animal => "dog" }
    }
  ]
)
```

```java
// search suggestions
ConstructorItem[] items = {
  new ConstructorItem("Golden Retriever"),
  new ConstructorItem("Poodle")
}
boolean success = constructorio.addOrUpdateBatch(items, "Search Suggestions")

// products
HashMap<String, Object> item1params = new HashMap<String, Object>();
item1params.put("url", "http://www.mydogs.com/labradoodle");
item1params.put("image_url", "https://images.mydogs.com/labradoodle.jpg");
item1paramas.put("description", "A crossbreed dog created by crossing the Labrador Retriever and the Poodle");
ConstructorItem item1 = new ConstructorItem("Labradoodle", item1params)
    .setSuggestedScore(360)
    .setKeywords("poodle","labrador","retriever");

HashMap<String, Object> item2params = new HashMap<String, Object>();
item2params.put("url", "http://www.mydogs.com/australian_shepherd");
item2params.put("image_url", "https://images.mydogs.com/australian_shepherd.jpg");
item2paramas.put("description", "A medium-sized breed of dog developed on ranches in the Western United States");
ConstructorItem item2 = new ConstructorItem("Australian Shepherd", item2params)
    .setSuggestedScore(130)
    .setKeywords("aussie")

ConstructorItem[] items = { item1, item2 };
boolean success = constructorio.addOrUpdateBatch(items, "Products")
```

```csharp
// search suggestions
List<ListItem> itemList = new List<ListItem>();
itemList.Add(new ListItem(
  Name: "Golden Retriever"
)
itemList.Add(new ListItem(
  Name: "Poodle"
)
bool success = ConstructorIOAPI.AddOrUpdateBatch(itemList, "Search Suggestions");

// products
List<ListItem> itemList = new List<ListItem>();

itemList.Add(new ListItem(
  Name: "Labradoodle",
  SuggestedScore: 360,
  Keywords: new string[]
  {
    "poodle",
    "labrador",
    "retriever"
  },
  URL: "http://www.mydogs.com/labradoodle",
  ImageUrl => "https://images.mydogs.com/labradoodle.jpg",
  Description: "A crossbreed dog created by crossing the Labrador Retriever and the Poodle",
  Metadata: new Dictionary<string, string>
  {
    { "animal", "dog" }
  }
));

itemList.Add(new ListItem(
  Name: "Australian Shepherd",
  SuggestedScore: 130,
  Keywords: new string[]
  {
    "aussie,
  },
  URL: "http://www.mydogs.com/australian_shepherd",
  ImageUrl => "https://images.mydogs.com/australian_shepherd.jpg",
  Description: "A medium-sized breed of dog developed on ranches in the Western United States",
  Metadata: new Dictionary<string, string>
  {
    { "animal", "dog" }
  }
));

bool success = ConstructorIOAPI.AddOrUpdateBatch(itemList, "Products");
```

> The above command(s) return a 204 Success response on success.

A batch add or update allows you to add a group of items to your autocomplete without first checking to make sure no item in the batch already exists.

Any items that don't already exist are created, and any items that already exist are updated. This is also known as an `UPSERT` operation.

To add or update a batch of items to your autocomplete index, use the `PUT /batch_items` call, with `?force=1`. Options are the same as for the standard `Batch Add Items` call: `item_name` and `autocomplete_section` are required and all other parameters are optional.

We determine whether items already exist based on the `item_name` and `autocomplete_section` set for each item. However, if the optional `id` parameter is set for the items, we determine whether items already exist using this parameter.

### HTTP Request

`PUT https://ac.cnstrc.com/v1/batch_items?force=1&autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ------- | -----------
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
items | Yes | A list of items with the same attributes as defined in the [Add an Item](#add-an-item) resource
