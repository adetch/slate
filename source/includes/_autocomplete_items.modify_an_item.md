## Modify an Item

```shell
curl -X PUT -H "Content-Type: application/json" -d '{"item_name":"power drill","new_item_name":"super power drill","keywords":["concrete","power tools","drills","drywall"],"suggested_score":20,"url":"http://www.mysite.com/power_drill","autocomplete_section":"products_autocomplete"}' \
  -u "[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.modify(
  {
    item_name: "power drill",
    new_item_name: "super power drill",
    autocomplete_section: "Search Suggestions",
    url: "http://www.mysite.com/power_drill",
  },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);
```

```ruby
response = constructorio.modify(
  {
    item_name: "power drill",
    new_item_name: "super power drill",
    autocomplete_section: "Search Suggestions",
    url: "http://www.mysite.com/power_drill",
  }
);
```

```python
response = constructor_instance.modify(
    item_name="power drill",
    new_item_name="better power drill",
    autocomplete_section="Search Suggestions",
    url="http://www.mysite.com/power_drill")
```

```php
<?php
$response = $constructor->modify(
  "power drill", // item name
  "super power drill", // new item name (this is required)
  "Search Suggestions", // autocomplete section name
  array("suggested_score" => 100) // array of item properties to modify
);
```

```perl
my $response = $constructorio->modify(
  item_name => "power drill",
  new_item_name => "super power drill",
  autocomplete_section => "Search Suggestions",
  url => "http://www.mysite.com/power_drill"
);
```

```java
boolean success = constructorio.modify("power drill", "super power drill", "Search Suggestions", paramMap);
// power drill is an item name
// super power drill is an item name
// Search Suggestions is an autocomplete section name
// paramMap is a Map<String, Object> you filled beforehand with the other properties you want to modify. Optional.
```

```csharp
ListItem item = new ListItem(
  Name: "Drill",
  URL: "http://constructor.io/drill",
  AutocompleteSection: "Products"
);

item.Name = "Power drill";
item.Description = "Like a drill, with power."

bool success = ConstructorIOAPI.Modify(item);
// "Drill" is the original item name as you previously saved it in our system
// "Power drill" is the new item name
// "Description" is a new description to add for the item
```

> The above command returns a 204 Success response on success.

To modify an item already in your autocomplete index, use the `PUT /item` call. The `item_name` is required. You can also pass in an optional `suggested_score` between 1-100, which will influence the item's initial ranking relative to other item scores (the higher the score, the higher in the list of suggestions the item will appear). You can also optionally pass in the item's `keywords` to give us more meta information and help us better determine how and where to display the item when autocompleting. If the item should point to a direct link, just pass in that link as a `url`. Finally, because your autocomplete can have multiple sections, like categories, search suggestions, and direct links to products, you must specify in which section you are modifying an item. You can do this with the `autocomplete_section` parameter.

Note: modifying an item replaces all meta information, such as keywords, we previously had on the item, but does not update the score unless you provide a new suggested_score.

### HTTP Request

`PUT https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ----------- | ----------
item_name | Yes | The name of the item, as it currently appears in the autocomplete suggestions
new_item_name | Yes | The name of the item, as it you'd like it to appear in the autocomplete suggestions
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
suggested_score | No | A number between 1 and 100 million that will influence the item's initial ranking relative to other item scores (the higher the score, the higher in the list of suggestions the item will appear)
keywords | No | An array of keywords for this item.  Keywords are useful if you want a product name to appear when a user enters a searchterm that isn't in the product name iteslf.
url | No | A URL to directly send the user after selecting the item
image_url | No | A URL that points to an image you'd like displayed next to some item (only applicable when url is supplied)
description | No | A description for some item (only applicable when url is supplied)
id | No | An arbitrary ID you optionally specified when adding the item.  If passed in, you don't need to pass in item_name.