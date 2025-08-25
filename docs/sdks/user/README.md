# User
(*user()*)

## Overview

Operations about user

### Available Operations

* [createUser](#createuser) - Create user
* [createUsersWithListInput](#createuserswithlistinput) - Creates list of users with given input array
* [loginUser](#loginuser) - Logs user into the system
* [logoutUser](#logoutuser) - Logs out current logged in user session
* [getUserByName](#getuserbyname) - Get user by user name
* [updateUser](#updateuser) - Update user
* [deleteUser](#deleteuser) - Delete user

## createUser

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="java" operationID="createUser" method="post" path="/user" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.components.User;
import org.openapis.openapi.models.operations.CreateUserResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        User req = User.builder()
                .id(10L)
                .username("theUser")
                .firstName("John")
                .lastName("James")
                .email("john@email.com")
                .password("12345")
                .phone("12345")
                .userStatus(1)
                .build();

        CreateUserResponse res = sdk.user().createUser()
                .request(req)
                .call();

        if (res.user().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [User](../../models/shared/User.md)        | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[CreateUserResponse](../../models/operations/CreateUserResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## createUsersWithListInput

Creates list of users with given input array

### Example Usage

<!-- UsageSnippet language="java" operationID="createUsersWithListInput" method="post" path="/user/createWithList" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.components.User;
import org.openapis.openapi.models.operations.CreateUsersWithListInputResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        List<User> req = List.of(
                User.builder()
                    .id(10L)
                    .username("theUser")
                    .firstName("John")
                    .lastName("James")
                    .email("john@email.com")
                    .password("12345")
                    .phone("12345")
                    .userStatus(1)
                    .build());

        CreateUsersWithListInputResponse res = sdk.user().createUsersWithListInput()
                .request(req)
                .call();

        if (res.user().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [List<User>](../../models//.md)            | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[CreateUsersWithListInputResponse](../../models/operations/CreateUsersWithListInputResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## loginUser

Logs user into the system

### Example Usage

<!-- UsageSnippet language="java" operationID="loginUser" method="get" path="/user/login" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.LoginUserResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        LoginUserResponse res = sdk.user().loginUser()
                .call();

        if (res.string().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `username`                           | *Optional\<String>*                  | :heavy_minus_sign:                   | The user name for login              |
| `password`                           | *Optional\<String>*                  | :heavy_minus_sign:                   | The password for login in clear text |

### Response

**[LoginUserResponse](../../models/operations/LoginUserResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## logoutUser

Logs out current logged in user session

### Example Usage

<!-- UsageSnippet language="java" operationID="logoutUser" method="get" path="/user/logout" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.operations.LogoutUserResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        LogoutUserResponse res = sdk.user().logoutUser()
                .call();

        // handle response
    }
}
```

### Response

**[LogoutUserResponse](../../models/operations/LogoutUserResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getUserByName

Get user by user name

### Example Usage

<!-- UsageSnippet language="java" operationID="getUserByName" method="get" path="/user/{username}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetUserByNameResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        GetUserByNameResponse res = sdk.user().getUserByName()
                .username("Edyth10")
                .call();

        if (res.user().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                  | Type                                                       | Required                                                   | Description                                                |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `username`                                                 | *String*                                                   | :heavy_check_mark:                                         | The name that needs to be fetched. Use user1 for testing.  |

### Response

**[GetUserByNameResponse](../../models/operations/GetUserByNameResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |

## updateUser

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="java" operationID="updateUser" method="put" path="/user/{username}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.components.User;
import org.openapis.openapi.models.operations.UpdateUserResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        UpdateUserResponse res = sdk.user().updateUser()
                .username("Alison.Cassin")
                .user(User.builder()
                    .id(10L)
                    .username("theUser")
                    .firstName("John")
                    .lastName("James")
                    .email("john@email.com")
                    .password("12345")
                    .phone("12345")
                    .userStatus(1)
                    .build())
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                                          | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `username`                                         | *String*                                           | :heavy_check_mark:                                 | name that needs to be updated                      |
| `user`                                             | [Optional\<User>](../../models/components/User.md) | :heavy_minus_sign:                                 | Update an existent user in the store               |

### Response

**[UpdateUserResponse](../../models/operations/UpdateUserResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## deleteUser

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="java" operationID="deleteUser" method="delete" path="/user/{username}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Petstore;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeleteUserResponse;

public class Application {

    public static void main(String[] args) throws ApiErrorInvalidInput, ApiErrorUnauthorized, ApiErrorNotFound, Exception {

        Petstore sdk = Petstore.builder()
                .apiKey(System.getenv().getOrDefault("API_KEY", ""))
            .build();

        DeleteUserResponse res = sdk.user().deleteUser()
                .username("Rita_Schuppe")
                .call();

        if (res.user().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `username`                        | *String*                          | :heavy_check_mark:                | The name that needs to be deleted |

### Response

**[DeleteUserResponse](../../models/operations/DeleteUserResponse.md)**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| models/errors/ApiErrorInvalidInput | 400                                | application/json                   |
| models/errors/ApiErrorUnauthorized | 401                                | application/json                   |
| models/errors/ApiErrorNotFound     | 404                                | application/json                   |
| models/errors/APIException         | 4XX, 5XX                           | \*/\*                              |