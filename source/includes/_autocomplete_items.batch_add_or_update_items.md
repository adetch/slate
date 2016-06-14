## Batch Add or Update Items

```shell
curl -X PUT -H "Content-Type: application/json" \
  -d '{"items": [ {"item_name": "power drill"}, {"item_name": "hammer"} ],
    "autocomplete_section":"Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/batch_items?force=1&autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.add_or_update_batch(
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
response = constructorio.add_or_update_batch(
  {
    items: [
      { item_name: "power drill" },
      { item_name: "hammer" }
    ],
    autocomplete_section: "Search Suggestions"
  }
);
```

```php
<?php
$response = $constructor->addOrUpdateBatch(
  array("power drill", "hammer"),
  "Search Suggestions"
);

$toolBox = array(
   array("item_name" => "power drill", "url" => "/products/power-drill", "image_url" => "/images/power-drill.jpg"),
   array("item_name" => "hammer", "url" => "/products/hammer", "image_url" => "/images/hammer.jpg")
);
$response = $constructor->addOrUpdateBatch($toolBox, "Products");
```

```perl
my $response = $constructorio->add_or_update_batch(
  items => [ { item_name => "power drill" }, { item_name => "hammer" } ],
  autocomplete_section => "Search Suggestions"
);
```

```java
boolean success = constructorio.addOrUpdateBatch("Search Suggestions", "power drill", "hammer");
// power drill is an item name
// hammer is an item name
// Search Suggestions is an autocomplete section name
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

bool success = ConstructorIOAPI.AddOrUpdateBatch(itemList, "Products");

// itemList is a List<ListItem> composed of key / value pairs as specified in parameters below. If "Power drill" or "Hammer" already exist, their metadata will be updated as above. Otherwise new items will be created with these values.
// "Products" is the  autocomplete section to which you'd like to add the items contained in itemList
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