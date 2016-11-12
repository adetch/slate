## Add or Update an Item

```shell
curl -X PUT -H "Content-Type: application/json" \
  -d '{"item_name":"power drill","keywords":["battery-powered","drills","drywall"],
  "suggested_score":36,"url":"http://www.mysite.com/power_drill","autocomplete_section":"Search Suggestions"}' \
  -u"[your token]:" "https://ac.cnstrc.com/v1/item?force=1&autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.add_or_update(
  { item_name: "power drill", autocomplete_section: "Search Suggestions" },
  function(error, response) {
    if (error) {
      console.log(error);
    }
  }
);
```

```ruby
response = constructorio.add_or_update(
  { item_name: "power drill", autocomplete_section: "Search Suggestions" }
);
```

```python
response = constructor_instance.add_or_update(
    item_name="power drill",
    autocomplete_section="Search Suggestions")
```

```php
<?php
$response = $constructor->addOrUpdate(
  "power drill", // item name
  "Search Suggestions" // autocomplete section name
);
```

```perl
my $response = $constructorio->add_or_update(
  item_name => "power drill",
  autocomplete_section => "Search Suggestions"
);
```

```java
boolean success = constructorio.addOrUpdate("power drill", "Search Suggestions");
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

bool success = ConstructorIOAPI.AddOrUpdate(item);

// "item" is a ListItem containing key / value pairs as specified in parameters below. If an item with the name "Power drill" already exists, its Description, Url and ImageUrl will be updated as indicated. Otherwise a new item will be created with these values.
```


 > The above commands return a 204 Success response on success.

An add or update operation (also known as an `UPSERT`) updates an item in your autocomplete index if it already exists, or adds the item to your index if it does not yet exist. 

To add or update an item in your autocomplete index, use the `PUT /item` call, with `?force=1`. Options are the same as for the standard `Add an Item` call: `item_name` and `autocomplete_section` are required and all other parameters are optional.

We determine whether an item already exists based on the optional `id` set for the item, or if not present, the `item_name` and `autocomplete_section`.

### HTTP Request

`PUT https://ac.cnstrc.com/v1/item?force=1&autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ------- | -----------
item_name | Yes | The name of the item, as it will appear in the autocomplete suggestions
autocomplete_section | Yes | Your autocomplete suggestions can have multiple sections like "Products" and "Search Suggestions".  This indicates which section this item is for.  See [your dashboard](/dashboard) for the section names to use.
suggested_score | No | A number between 1 and 100 million that will influence the item's initial ranking relative to other item scores (the higher the score, the higher in the list of suggestions the item will appear)
keywords | No | An array of keywords for this item.  Keywords are useful if you want a product name to appear when a user enters a searchterm that isn't in the product name iteslf.
url | No | A URL to directly send the user after selecting the item
image_url | No | A URL that points to an image you'd like displayed next to some item (only applicable when url is supplied)
description | No | A description for some item (only applicable when url is supplied)
id | No | An arbitrary ID you would like associated with this item.  You can use this field to store your own IDs of the items to more easily access them in other API calls.
