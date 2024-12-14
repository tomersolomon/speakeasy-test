# Pets
(*pets*)

## Overview

### Available Operations

* [update](#update) - Update an existing pet

## update

Update an existing pet by Id

### Example Usage

```python
import os
from petstore import Petstore

with Petstore(
    api_key=os.getenv("PETSTORE_API_KEY", ""),
) as petstore:

    res = petstore.pets.update(name="doggie", photo_urls=[
        "<value>",
        "<value>",
    ], id=10, category={
        "id": 1,
        "name": "Dogs",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | doggie                                                              |
| `photo_urls`                                                        | List[*str*]                                                         | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `id`                                                                | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 10                                                                  |
| `category`                                                          | [Optional[models.Category]](../../models/category.md)               | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `tags`                                                              | List[[models.Tag](../../models/tag.md)]                             | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `status`                                                            | [Optional[models.Status]](../../models/status.md)                   | :heavy_minus_sign:                                                  | pet status in the store                                             |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Pet](../../models/pet.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models.APIErrorInvalidInput | 400                         | application/json            |
| models.APIErrorUnauthorized | 401                         | application/json            |
| models.APIErrorNotFound     | 404                         | application/json            |
| models.APIError             | 4XX, 5XX                    | \*/\*                       |