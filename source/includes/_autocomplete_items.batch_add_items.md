## Batch Add Items

```shell
curl -X POST -H "Content-Type: application/json" \
  -d '{"items": [ {"item_name": "power drill"}, {"item_name": "hammer"} ],
    "autocomplete_section":"Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.add_batch(
  {
    items: [
      { item_name: "power drill" },
      { item_name: "hammer" }
    ],
    autocomplete_section: "Search Suggestions"
  },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);
```

```ruby
response = constructorio.add_batch(
  {
    items: [
      { item_name: "power drill" },
      { item_name: "hammer" }
    ],
    autocomplete_section: "Search Suggestions"
  }
);
```

```python
items = [
  {"item_name": "power drill"},
  {"item_name": "hammer"}
]
response = constructor_instance.add_batch(
  items=items,
  autocomplete_section="Search Suggestions"
)

toolBox = [
  {"item_name": "power drill 1000", "url": "/products/power-drill-1000", "id": "42"},
  {"item_name": "hammer of thor", "url": "/products/hammer-of-thor"}
]
response = constructor_instance.add_batch(
    items=toolBox,
    autocomplete_section="Products"
)
```

```php
<?php
$response = $constructor->addBatch(
  array("power drill", "hammer"),
  "Search Suggestions"
);

$toolBox = array(
   array("item_name" => "power drill", "url" => "/products/power-drill", "image_url" => "/images/power-drill.jpg"),
   array("item_name" => "hammer", "url" => "/products/hammer", "image_url" => "/images/hammer.jpg")
);
$response = $constructor->addBatch($toolBox, "Products");
```

```perl
my $response = $constructorio->add_batch(
  items => [ { item_name => "power drill" }, { item_name => "hammer" } ],
  autocomplete_section => "Search Suggestions"
);
```

```java
boolean success = constructorio.addBatch("Search Suggestions", "power drill", "hammer");
// "Search Suggestions" is an autocomplete section name
// power drill is an item name
// hammer is an item name
```

```csharp
List<ListItem> itemList = new List<ListItem>();

itemList.Add(new ListItem(
  Name: "Power drill",
  Description: "Like a drill, with power.",
  URL: "http://constructor.io/power-drill",
  ImageURL: "http://constructor.io/power-drill.jpg"
));

itemList.Add(new ListItem(
  Name: "Hammer",
  Description: "When everything looks like a nail.",
  URL: "http://constructor.io/hammer"
));

bool success = ConstructorIOAPI.AddBatch(itemList, "Products");

// itemList is a List<ListItem> composed of key / value pairs as specified in parameters below.
// "Products" is the  autocomplete section to which you'd like to add the items contained in itemList
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