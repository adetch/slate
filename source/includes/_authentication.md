# Authentication

## API Token

> To authorize, use this code:

```shell
# with curl, there's no need to authorize separately -- just pass your API token in with every call
curl -X POST -H "Content-Type: application/json" \
  -d '{"item_name":"xyz","keywords":["k1","k2"]}' \
  -u "[your API token]:" https://ac.cnstrc.com/v1/item
```

```javascript
var ConstructorIO = require('constructorio');
var constructorio = new ConstructorIO({
  apiToken: "[your API token]",
  autocompleteKey: "[your autocomplete key]",
});

```

```ruby
require('constructorio')
ConstructorIO.configure do |config|
  config.api_token = "[your API token]"
  config.autocomplete_key = "[your autocomplete key]"
end
constructorio = ConstructorIO::Client.new
```

```python
from constructor_io import ConstructorIO
constructor_instance = ConstructorIO(
    api_token="[your api token]",
    autocomplete_key="[your autocomplete key]")
```

```php
<?php
// if using Composer autoloading:
// require_once "vendor/autoload.php";
use ConstructorIO\ConstructorIO;
$constructorio = new ConstructorIO("[your API token]","[your autocomplete key]");
```

```perl
use WebService::ConstructorIO;
my $constructorio = new WebService::ConstructorIO->new(
  api_token => "[your API token]",
  autocomplete_key => "[your autocomplete key]"
);
```

```java
import com.cnstrc.client.ConstructorIO;
ConstructorIO constructorClient = new ConstructorIO("[your API token]", "[your autocomplete key]", true, null);
```

```csharp
using ConstructorIO;
var ConstructorIOAPI = new ConstructorIOAPI("[your API token]", "[your autocomplete key]");
```

> Make sure to replace `[your API token]` with your API token from [your dashboard](/dashboard).

You authenticate to the REST API by providing your API token, which you can obtain from [your dashboard](/dashboard).

Authentication is done using [HTTP Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication). Provide your API token as the basic auth username in every request. You do not need to provide a password. All API requests must be made over HTTPS.

## Verification

```shell
curl -u "[your API token]:" "https://ac.cnstrc.com/v1/verify?autocomplete_key=[your autocomplete key]"
```

```javascript
constructorio.verify(function(error, response) {
  if (error) {
    console.log("Error: ", error);
  } else {
    console.log("Response: ", response);
  }
});
```

```ruby
response = constructorio.verify
```

```python
response = constructor_instance.verify()
```

```php
<?php
$response = $constructor->verify();
```

```perl
my $response = $constructorio->verify();
```

```java
boolean isValid = constructorio.verify();
```

```csharp
bool isValid = ConstructorIOAPI.Verify();
```

You can verify that authentication works correctly by issuing a simple verification request.

### HTTP Request

`GET https://ac.cnstrc.com/v1/verify?autocomplete_key=[your autocomplete key]`

