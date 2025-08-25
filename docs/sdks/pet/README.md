# Pet
(*pet()*)

## Overview

Everything about your Pets

Find out more
<http://swagger.io>

### Available Operations

* [updatePet](#updatepet) - Update an existing pet
* [addPet](#addpet) - Add a new pet to the store
* [findPetsByStatus](#findpetsbystatus) - Finds Pets by status
* [findPetsByTags](#findpetsbytags) - Finds Pets by tags
* [getPetById](#getpetbyid) - Find pet by ID
* [deletePet](#deletepet) - Deletes a pet
* [uploadFile](#uploadfile) - uploads an image

## updatePet

Update an existing pet by Id

### Example Usage

<!-- UsageSnippet language="java" operationID="updatePet" method="put" path="/pet" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.components.Category;
import org.openapis.openapi.models.components.Pet;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.UpdatePetResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        Pet req = Pet.builder()
                .name("doggie")
                .photoUrls(List.of(
                    "<value 1>"))
                .id(10L)
                .category(Category.builder()
                    .id(1L)
                    .name("Dogs")
                    .build())
                .build();

        UpdatePetResponse res = sdk.pet().updatePet()
                .request(req)
                .call();

        if (res.pet().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [Pet](../../models/shared/Pet.md)          | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[UpdatePetResponse](../../models/operations/UpdatePetResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## addPet

Add a new pet to the store

### Example Usage

<!-- UsageSnippet language="java" operationID="addPet" method="post" path="/pet" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.components.Category;
import org.openapis.openapi.models.components.Pet;
import org.openapis.openapi.models.operations.AddPetResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        Pet req = Pet.builder()
                .name("doggie")
                .photoUrls(List.of(
                    "<value 1>",
                    "<value 2>",
                    "<value 3>"))
                .id(10L)
                .category(Category.builder()
                    .id(1L)
                    .name("Dogs")
                    .build())
                .build();

        AddPetResponse res = sdk.pet().addPet()
                .request(req)
                .call();

        if (res.pet().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [Pet](../../models/shared/Pet.md)          | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[AddPetResponse](../../models/operations/AddPetResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## findPetsByStatus

Multiple status values can be provided with comma separated strings

### Example Usage

<!-- UsageSnippet language="java" operationID="findPetsByStatus" method="get" path="/pet/findByStatus" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.FindPetsByStatusResponse;
import org.openapis.openapi.models.operations.Status;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        FindPetsByStatusResponse res = sdk.pet().findPetsByStatus()
                .status(Status.AVAILABLE)
                .call();

        if (res.pets().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                              | Type                                                   | Required                                               | Description                                            |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `status`                                               | [Optional\<Status>](../../models/operations/Status.md) | :heavy_minus_sign:                                     | Status values that need to be considered for filter    |

### Response

**[FindPetsByStatusResponse](../../models/operations/FindPetsByStatusResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## findPetsByTags

Multiple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.

### Example Usage

<!-- UsageSnippet language="java" operationID="findPetsByTags" method="get" path="/pet/findByTags" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.FindPetsByTagsResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        FindPetsByTagsResponse res = sdk.pet().findPetsByTags()
                .call();

        if (res.pets().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `tags`             | List\<*String*>    | :heavy_minus_sign: | Tags to filter by  |

### Response

**[FindPetsByTagsResponse](../../models/operations/FindPetsByTagsResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## getPetById

Returns a single pet

### Example Usage

<!-- UsageSnippet language="java" operationID="getPetById" method="get" path="/pet/{petId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetPetByIdResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        GetPetByIdResponse res = sdk.pet().getPetById()
                .petId(311674L)
                .call();

        if (res.pet().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter           | Type                | Required            | Description         |
| ------------------- | ------------------- | ------------------- | ------------------- |
| `petId`             | *long*              | :heavy_check_mark:  | ID of pet to return |

### Response

**[GetPetByIdResponse](../../models/operations/GetPetByIdResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## deletePet

Deletes a pet

### Example Usage

<!-- UsageSnippet language="java" operationID="deletePet" method="delete" path="/pet/{petId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeletePetResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        DeletePetResponse res = sdk.pet().deletePet()
                .petId(818965L)
                .call();

        if (res.pet().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter           | Type                | Required            | Description         |
| ------------------- | ------------------- | ------------------- | ------------------- |
| `apiKey`            | *Optional\<String>* | :heavy_minus_sign:  | N/A                 |
| `petId`             | *long*              | :heavy_check_mark:  | Pet id to delete    |

### Response

**[DeletePetResponse](../../models/operations/DeletePetResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## uploadFile

uploads an image

### Example Usage

<!-- UsageSnippet language="java" operationID="uploadFile" method="post" path="/pet/{petId}/uploadImage" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.operations.UploadFileResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        UploadFileResponse res = sdk.pet().uploadFile()
                .petId(150516L)
                .call();

        if (res.apiResponse().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter            | Type                 | Required             | Description          |
| -------------------- | -------------------- | -------------------- | -------------------- |
| `petId`              | *long*               | :heavy_check_mark:   | ID of pet to update  |
| `additionalMetadata` | *Optional\<String>*  | :heavy_minus_sign:   | Additional Metadata  |
| `requestBody`        | *Optional\<byte[]>*  | :heavy_minus_sign:   | N/A                  |

### Response

**[UploadFileResponse](../../models/operations/UploadFileResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |