# Users
(*users*)

## Overview

### Available Operations

* [create_with_list](#create_with_list) - Creates list of users with given input array

## create_with_list

Creates list of users with given input array

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    res = petstore.users.create_with_list(request=[
        {
            "id": 10,
            "username": "theUser",
            "first_name": "John",
            "last_name": "James",
            "email": "john@email.com",
            "password": "12345",
            "phone": "12345",
            "user_status": 1,
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [List[models.User]](../../models/.md)                               | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| models.APIError | 4XX, 5XX        | \*/\*           |