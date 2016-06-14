## Remove an Item

```shell
curl -X DELETE -H "Content-Type: application/json" -d '{"item_name":"power drill","autocomplete_section":"products_autocomplete"}' \
  -u "[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.remove(
  { item_name: "power drill", autocomplete_section: "Search Suggestions" },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);
```

```ruby
response = constructorio.remove(
  { item_name: "power drill", autocomplete_section: "Search Suggestions" }
);
```

```python
response = constructor_instance.remove(item_name="power drill", autocomplete_section="Search Suggestions")
```

```php
<?php
$response = $constructor->remove(
  "power drill", // item name
  "Search Suggestions" // autocomplete section name
);
```

```perl
my $response = $constructorio->remove(
  item_name => "power drill",
  autocomplete_section => "Search Suggestions"
);
```

```java
boolean success = constructorio.remove("power drill", "Search Suggestions");
// power drill is an item name
// Search Suggestions is an autocomplete section name
```

```csharp
ListItem item = new ListItem(
  Name: "Power drill",
  AutocompleteSection: "Products"
);

bool success = ConstructorIOAPI.Remove(item);

// "item" is a ListItem with the Name or ID for the item you'd like to remove
```

> The above command returns a 204 Success response on success.

To remove an item from your autocomplete index (if, for instance, a product has been discontinued), issue a `DELETE /item` call. Note: this will remove all meta-information such as keywords we currently have on the item. If your autocomplete has multiple sections (i.e. products, categories, and search suggestions), you must specify the name of the autocomplete section from which you're removing an item.

### HTTP Request

`DELETE https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ----------- | ----------
item_name | Yes | The name of the item, as it will appear in the autocomplete suggestions
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
id | No | An arbitrary ID you optionally specified when adding the item.  If passed in, you don't need to pass in item_name.
