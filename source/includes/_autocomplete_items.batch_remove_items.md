## Batch Remove Items

```shell
curl -X DELETE -H "Content-Type: application/json" \
  -d '{"items": [ {"item_name": "Labradoodle"}, {"id": "D26"} ], \
    "autocomplete_section":"Products"}' \
  -u "[your token]:" "https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.remove_batch(
  {
    autocomplete_section: "Products",
    items: [
      { item_name: "Labradoodle" },
      { id: "D26" }
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
response = constructorio.remove_batch(
  {
    autocomplete_section: "Products",
    items: [
      { item_name: "Products" },
      { id: "D26" }
    ],
  }
);
```

```python
response = constructor_instance.remove_batch(
  autocomplete_section="Products",
  items=[
    {"item_name": "Labradoodle"},
    {"id": "D26"}
  ]
)
```

```php
<?php
// This method is not currently supported in our php client.
```

```perl
# This method is not currently supported in our perl client.
```

```java
ConstructorItem[] items = {
  new ConstructorItem("Labradoodle"),
  new ConstructorItem("Poodle")
}
boolean success = constructorio.removeBatch(items, "Products")
```

```csharp
List<ListItem> itemList = new List<ListItem>();
itemList.Add(new ListItem(
  Name: "Labradoodle")
);
itemList.Add(new ListItem(
  ID: "D26")
);
bool success = ConstructorIOAPI.RemoveBatch(itemList, "Products");
```
> The above command returns a 204 Success response on success.

To remove multiple items from your autocomplete index as a batch, use the `DELETE /batch_items` call. Note: this will remove all meta-information such as keywords we currently store on the items.

The `items` parameter is required and is a list of items with the same attributes as defined in the [Remove an Item](#remove-an-item) resource. If your autocomplete has multiple sections (i.e. products, categories, and search suggestions), you must specify the name of the autocomplete section from which you're removing the items.

There is a limit of 1,000 items per batch request.

### HTTP Request

`DELETE https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ----------- | ----------
items | Yes | A list of items with the same attributes as defined in the [Remove an Item](#remove-an-item) resource.
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
