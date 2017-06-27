# Beta: Search

```shell
curl -X GET -H "Content-Type: application/json" \
"https://ac.cnstrc.com/search/[query]?autocomplete_key=[your autocomplete key]"

# for the demo list of dog breeds on our homepage
curl -X GET -H "Content-Type: application/json" \
"https://ac.cnstrc.com/search/sheep?autocomplete_key=pAFl6rReRSI0uXckcxZS&page=3"
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

Constructor.io is working on a full search platform, now released publicly for beta use.

The platform leverages the advanced re-ranking and optimization of our autocomplete service
to deliver a lightning-fast search service that learns automatically from your users' behavior.

### HTTP Request

`GET  https://ac.cnstrc.com/search/[query]?autocomplete_key=[your autocomplete key]`


Option | Default | Description
------------- | --- | ----------
page|1|The page number of the results
num_results_per_page|20|The number of results per page to return
num_results_per_page_[section]|n/a|The number of results per page for a given section (when a dataset has multiple  autocomplete sections).  Results from sections that were not included in the request will not be returned at all.

