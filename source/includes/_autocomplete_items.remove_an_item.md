## Remove an Item

```shell
# remove by name
curl -X DELETE -H "Content-Type: application/json" \
  -d '{"item_name": "Golden Retriever", \
       "autocomplete_section": "Search Suggestions"}' \
  -u "[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"

# remove by ID
curl -X DELETE -H "Content-Type: application/json" -d '{"item_name":"power drill","autocomplete_section":"products_autocomplete"}' \
  -u "[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"
```

```javascript
// remove by name
constructorio.remove(
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

// remove by ID
constructorio.remove(
  {
    id: "D26",
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
# remove by name
response = constructorio.remove(
  {
    item_name: "Golden Retriever",
    autocomplete_section: "Search Suggestions"
  }
);

# remove by ID
response = constructorio.remove(
  {
    id: "D26",
    autocomplete_section: "Search Suggestions"
  }
);
```

```python
# remove by name
response = constructor_instance.remove(
  item_name="Golden Retriever",
  autocomplete_section="Search Suggestions")
```

```php
<?php
// remove by name
$response = $constructor->remove(
  "Golden Retriever", // item name
  "Search Suggestions" // autocomplete section name
);
```

```perl
# remove by name
my $response = $constructorio->remove(
  item_name => "Golden Retriever",
  autocomplete_section => "Search Suggestions"
);

# remove by ID
my $response = $constructorio->remove(
  id => "D26",
  autocomplete_section => "Search Suggestions"
);
```

```java
// remove by name
boolean success = constructorio.remove(
  "Golden Retriever", // item name
  "Search Suggestions" // autocomplete section
);
```

```csharp
// remove by name
ListItem itemByName = new ListItem(
  Name: "Golden Retriever",
  AutocompleteSection: "Search Suggestions"
);

bool success = ConstructorIOAPI.Remove(itemByName);

ListItem itemByID = new ListItem(
  ID: "D26",
  AutocompleteSection: "Search Suggestions"
);

bool success = ConstructorIOAPI.Remove(itemByID);
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
