# Autocomplete Queries

```shell
curl -X GET -H "Content-Type: application/json" \
"https://ac.cnstrc.com/autocomplete/[query]?autocomplete_key=[your autocomplete key]"

curl -X GET -H "Content-Type: application/json" \
"https://ac.cnstrc.com/autocomplete/australian?autocomplete_key=pAFl6rReRSI0uXckcxZS&num_results_Search%20Suggestions=3"
```

```javascript
// The autocomplete query endpoint is not implemented for backend libraries.
// Please refer to shell documentation or our Javascript (front-end) client. 
```

```ruby
# The autocomplete query endpoint is not implemented for backend libraries. 
# Please refer to shell documentation or our Javascript (front-end) client.
```

```python
# The autocomplete query endpoint is not implemented for backend libraries.
# Please refer to shell documentation or our Javascript (front-end) client.
```

```php
<?php
// The autocomplete query endpoint is not implemented for backend libraries. 
// Please refer to shell documentation or our Javascript (front-end) client. 
```

```perl
# The autocomplete query endpoint is not implemented for backend libraries.
# Please refer to shell documentation or our Javascript (front-end) client. 
```

```java
// The autocomplete query endpoint is not implemented for backend libraries. 
// Please refer to shell documentation or our Javascript (front-end) client. 
```

```csharp
// The autocomplete query endpoint is not implemented for backend libraries.
// Please refer to shell documentation or our Javascript (front-end) client. 
```

> The above command returns a 200 Success response on success.


> Refer [here](?shell#query-items) for shell documentation, and [here](#javascript-client) for instructions on installing our Javascript (front-end) client.

You can try out an autocomplete query on your dataset by typing the following URL into a web browser: `https://ac.cnstrc.com/autocomplete/[query]?autocomplete_key=[your autocomplete key]`, replacing `[query]` with the query you'd like to make, and `[your autocomplete key]` with your autocomplete key.

Want to try it right now? You can search for `labrador` from our demo list of dog breeds [here](https://ac.cnstrc.com/autocomplete/australian?autocomplete_key=pAFl6rReRSI0uXckcxZS).

When implementing our autocomplete on a website, we recommend most customers use our [Javascript (front-end) client](#javascript-client). For other uses, such as within native or mobile apps, we recommend customers issue HTTP requests to our API.

### HTTP Request

`GET  https://ac.cnstrc.com/autocomplete/[query]?autocomplete_key=[your autocomplete key]`

### JSON Parameters

Parameter | Required? | Description
--------- | ----------- | ----------
query | Yes | The URL-encoded autocomplete query.
autocomplete_key | Yes | The key for the autocomplete you would like to query.
num_results | No | The number of results to return across all sections in the autocomplete (rounded down if `num_results` isn't divisible by the number of autocomplete sections).
num_results_[section_name] | No | The number of results to return from autocomplete section `section_name`. `section_name` is URL encoded, so 3 results from section `Dog Breeds` would be `num_results_Dog%20Breeds=3`. A single request can include several of these parameters to specify the number of results to return from multiple sections.