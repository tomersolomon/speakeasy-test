# UserSDK
(*user*)

## Overview

Operations about user

### Available Operations

* [create](#create) - Create user
* [login](#login) - Logs user into the system
* [logout](#logout) - Logs out current logged in user session
* [get_by_name](#get_by_name) - Get user by user name
* [update](#update) - Update user
* [delete](#delete) - Delete user

## create

This can only be done by the logged in user.

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    res = petstore.user.create(request={
        "id": 10,
        "username": "theUser",
        "first_name": "John",
        "last_name": "James",
        "email": "john@email.com",
        "password": "12345",
        "phone": "12345",
        "user_status": 1,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.User](../../models/user.md)                                 | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| models.APIError | 4XX, 5XX        | \*/\*           |

## login

Logs user into the system

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    res = petstore.user.login()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | The user name for login                                             |
| `password`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | The password for login in clear text                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.LoginUserResponse](../../models/loginuserresponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models.APIErrorInvalidInput | 400                         | application/json            |
| models.APIErrorUnauthorized | 401                         | application/json            |
| models.APIErrorNotFound     | 404                         | application/json            |
| models.APIError             | 4XX, 5XX                    | \*/\*                       |

## logout

Logs out current logged in user session

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    petstore.user.logout()

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| models.APIError | 4XX, 5XX        | \*/\*           |

## get_by_name

Get user by user name

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    res = petstore.user.get_by_name(username="Zachery_Lubowitz15")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username`                                                          | *str*                                                               | :heavy_check_mark:                                                  | The name that needs to be fetched. Use user1 for testing.           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models.APIErrorInvalidInput | 400                         | application/json            |
| models.APIErrorUnauthorized | 401                         | application/json            |
| models.APIErrorNotFound     | 404                         | application/json            |
| models.APIError             | 4XX, 5XX                    | \*/\*                       |

## update

This can only be done by the logged in user.

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    petstore.user.update(username_param="<value>", id=10, username="theUser", first_name="John", last_name="James", email="john@email.com", password="12345", phone="12345", user_status=1)

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username_param`                                                    | *str*                                                               | :heavy_check_mark:                                                  | name that needs to be updated                                       |                                                                     |
| `id`                                                                | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 10                                                                  |
| `username`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | theUser                                                             |
| `first_name`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | John                                                                |
| `last_name`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | James                                                               |
| `email`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | john@email.com                                                      |
| `password`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 12345                                                               |
| `phone`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 12345                                                               |
| `user_status`                                                       | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | User Status                                                         | 1                                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| models.APIError | 4XX, 5XX        | \*/\*           |

## delete

This can only be done by the logged in user.

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    res = petstore.user.delete(username="Demetris_Schmitt")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username`                                                          | *str*                                                               | :heavy_check_mark:                                                  | The name that needs to be deleted                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models.APIErrorInvalidInput | 400                         | application/json            |
| models.APIErrorUnauthorized | 401                         | application/json            |
| models.APIErrorNotFound     | 404                         | application/json            |
| models.APIError             | 4XX, 5XX                    | \*/\*                       |