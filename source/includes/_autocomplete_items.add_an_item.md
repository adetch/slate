## Add an Item

```shell
curl -X POST -H "Content-Type: application/json" \
  -d '{"item_name":"power drill","keywords":["battery-powered","drills","drywall"],
  "suggested_score":36,"url":"http://www.mysite.com/power_drill","autocomplete_section":"Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.add(
  { item_name: "power drill", autocomplete_section: "Search Suggestions" },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);
```

```ruby
response = constructorio.add(
  { item_name: "power drill", autocomplete_section: "Search Suggestions" }
);
```

```python
response = constructor_instance.add(
    item_name="power drill",
    autocomplete_section="Search Suggestions")
```

```php
<?php
$response = $constructor->add(
  "power drill", // item name
  "Search Suggestions" // autocomplete section name
);
```

```perl
my $response = $constructorio->add(
  item_name => "power drill",
  autocomplete_section => "Search Suggestions"
);
```

```java
boolean success = constructorio.add("power drill", "Search Suggestions");
// power drill is an item name
// Search Suggestions is an autocomplete section name
```

```csharp
ListItem item = new ListItem(
  Name: "Power drill",
  Description: "Like a drill, with power.",
  URL: "http://constructor.io/power-drill",
  ImageURL: "http://constructor.io/power-drill.jpg",
  AutocompleteSection: "Products"
);

bool success = ConstructorIOAPI.Add(item);

// "item" is a ListItem containing key / value pairs as specified in parameters below.
```

> The above command returns a 204 Success response on success.

To add an item to your autocomplete index, use the `POST /item` call. The `item_name` is required. You can also pass in an optional `suggested_score` between 1-100, which will influence the item's initial ranking relative to other item scores (the higher the score, the higher in the list of suggestions the item will appear). You can also optionally pass in the item's `keywords` to give us more meta information and help us better determine how and where to display the item when autocompleting. If you would like to add an item that points to a direct link, just pass in that link as a `url`. Finally, because your autocomplete can have multiple sections, like categories, search suggestions, and direct links to products, you must specify which section you are adding an item to. You can do this with the `autocomplete_section` parameter.

### HTTP Request

`POST https://ac.cnstrc.com/v1/item?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ------- | -----------
item_name | Yes | The name of the item, as it will appear in the autocomplete suggestions
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
suggested_score | No | A number between 1-100 that will influence the item's initial ranking relative to other item scores (the higher the score, the higher in the list of suggestions the item will appear)
keywords | No | An array of keywords for this item.  Keywords are useful if you want a product name to appear when a user enters a searchterm that isn't in the product name iteslf.
url | No | A URL to directly send the user after selecting the item
image_url | No | A URL that points to an image you'd like displayed next to some item (only applicable when url is supplied)
description | No | A description for some item (only applicable when url is supplied)
id | No | An arbitrary ID you would like associated with this item.  You can use this field to store your own IDs of the items to more easily access them in other API calls.