## Batch Add Items

```shell
# search suggestions
curl -X POST -H "Content-Type: application/json" \
  -d '{"items": [ {"item_name": "Golden Retriever"}, {"item_name": "Poodle"} ], \
    "autocomplete_section":"Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]"

# products
curl -X POST -H "Content-Type: application/json" \
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
  -u"[your token]:" "https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]"
```

```javascript
// search suggestions
constructorio.add_batch(
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
constructorio.add_batch(
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
response = constructorio.add_batch(
  {
    autocomplete_section: "Search Suggestions",
    items: [
      { item_name: "Golden Retriever" },
      { item_name: "Poodle" }
    ],
  }
)

# products
response = constructorio.add_batch(
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
items = response = constructor_instance.add_batch(
  autocomplete_section="Search Suggestions",
  items=[
    {"item_name": "Golden Retriever"},
    {"item_name": "Poodle"}
  ]
)

# products
response = constructor_instance.add_batch(
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
// search suggestions
$response = $constructor->addBatch(
  array("Golden Retriever", "Poodle"),
  "Search Suggestions"
);

// products
$response = $constructor->addBatch(
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
my $response = $constructorio->add_batch(
  autocomplete_section => "Search Suggestions",
  items => [
    { item_name => "Golden Retriever" },
    { item_name => "Poodle" }
  ]
);

# products
my $response = $constructorio->add_batch(
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
boolean success = constructorio.addBatch(items, "Search Suggestions")

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
boolean success = constructorio.addBatch(items, "Products")
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
bool success = ConstructorIOAPI.AddBatch(itemList, "Search Suggestions");

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

bool success = ConstructorIOAPI.AddBatch(itemList, "Products");

```

> The above command(s) return a 204 Success response on success.

To add multiple items to your autocomplete index as a batch, use the `POST /batch_items` call. The `items` parameter is required and is a list of items with the same attributes as defined in the [Add an Item](#add-an-item) resource.  Because your autocomplete can have multiple sections, like categories, search suggestions, and direct links to products, you must specify which section you are adding an item to. You can do this with the `autocomplete_section` parameter.

### HTTP Request

`POST https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ------- | -----------
items | Yes | A list of items with the same attributes as defined in the [Add an Item](#add-an-item) resource
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
