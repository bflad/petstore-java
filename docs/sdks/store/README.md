# Store
(*store()*)

## Overview

Access to Petstore orders

Find out more about our store
<http://swagger.io>

### Available Operations

* [getInventory](#getinventory) - Returns pet inventories by status
* [placeOrder](#placeorder) - Place an order for a pet
* [getOrderById](#getorderbyid) - Find purchase order by ID
* [deleteOrder](#deleteorder) - Delete purchase order by ID

## getInventory

Returns a map of status codes to quantities

### Example Usage

<!-- UsageSnippet language="java" operationID="getInventory" method="get" path="/store/inventory" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.ApiErrorNotFound;
import org.openapis.openapi.models.errors.ApiErrorUnauthorized;
import org.openapis.openapi.models.operations.GetInventoryResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        GetInventoryResponse res = sdk.store().getInventory()
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[GetInventoryResponse](../../models/operations/GetInventoryResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## placeOrder

Place a new order in the store

### Example Usage

<!-- UsageSnippet language="java" operationID="placeOrder" method="post" path="/store/order" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.components.Order;
import org.openapis.openapi.models.components.OrderStatus;
import org.openapis.openapi.models.errors.ApiErrorNotFound;
import org.openapis.openapi.models.errors.ApiErrorUnauthorized;
import org.openapis.openapi.models.operations.PlaceOrderResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        Order req = Order.builder()
                .id(10L)
                .petId(198772L)
                .quantity(7)
                .status(OrderStatus.APPROVED)
                .build();

        PlaceOrderResponse res = sdk.store().placeOrder()
                .request(req)
                .call();

        if (res.order().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [Order](../../models/shared/Order.md)      | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[PlaceOrderResponse](../../models/operations/PlaceOrderResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## getOrderById

For valid response try integer IDs with value <= 5 or > 10. Other values will generate exceptions.

### Example Usage

<!-- UsageSnippet language="java" operationID="getOrderById" method="get" path="/store/order/{orderId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetOrderByIdResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        GetOrderByIdResponse res = sdk.store().getOrderById()
                .orderId(728529L)
                .call();

        if (res.order().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `orderId`                            | *long*                               | :heavy_check_mark:                   | ID of order that needs to be fetched |

### Response

**[GetOrderByIdResponse](../../models/operations/GetOrderByIdResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## deleteOrder

For valid response try integer IDs with value < 1000. Anything above 1000 or nonintegers will generate API errors

### Example Usage

<!-- UsageSnippet language="java" operationID="deleteOrder" method="delete" path="/store/order/{orderId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeleteOrderResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        DeleteOrderResponse res = sdk.store().deleteOrder()
                .orderId(690575L)
                .call();

        if (res.order().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                | Type                                     | Required                                 | Description                              |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `orderId`                                | *long*                                   | :heavy_check_mark:                       | ID of the order that needs to be deleted |

### Response

**[DeleteOrderResponse](../../models/operations/DeleteOrderResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |