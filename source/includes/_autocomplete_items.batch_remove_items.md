## Batch Remove Items

```shell
curl -X DELETE -H "Content-Type: application/json" -d {"items": [ {"item_name": "power drill"}, {"item_name": "hammer"} ],
    "autocomplete_section":"Search Suggestions"}' \
  -u "[your token]:" "https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]"
```

```javascript
// This method is not currently supported in our javascript client.
```

```ruby
response = constructorio.remove_batch(
  {
    items: [
      { item_name: "power drill" },
      { item_name: "hammer" },
      { id: "3" }
    ],
    autocomplete_section: "Products"
  }
);

# Here we've removed a batch of items by item_name and id.
```

```python
items = [
  {"item_name": "power drill"},
  {"item_name": "hammer"}
]
response = constructor_instance.remove_batch(
  items=items,
  autocomplete_section="Search Suggestions"
)

toolBox = [
  {"item_name": "power drill 1000"},
  {"id": "132"}
]
response = constructor_instance.remove_batch(
    items=toolBox,
    autocomplete_section="Products"
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
// This method is not currently supported in our java client.
```

```csharp
List<ListItem> itemList = new List<ListItem>();

itemList.Add(new ListItem(Name: "Power drill"));
itemList.Add(new ListItem(ID: "245"));

bool success = ConstructorIOAPI.RemoveBatch(itemList, "Products");

// itemList is a List<ListItem> with the IDs and/or Names of the items you'd like to remove.
// "Products" is an autocomplete section name.
```
> The above command returns a 204 Success response on success.

To remove multiple items from your autocomplete index as a batch, use the `DELETE /batch_items` call. Note: this will remove all meta-information such as keywords we currently store on the items.

The `items` parameter is required and is a list of items with the same attributes as defined in the [Remove an Item](#remove-an-item) resource. If your autocomplete has multiple sections (i.e. products, categories, and search suggestions), you must specify the name of the autocomplete section from which you're removing the items.

### HTTP Request

`DELETE https://ac.cnstrc.com/v1/batch_items?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ----------- | ----------
items | Yes | A list of items with the same attributes as defined in the [Remove an Item](#remove-an-item) resource.
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.