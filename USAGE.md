<!-- Start SDK Example Usage [usage] -->
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
<!-- End SDK Example Usage [usage] -->