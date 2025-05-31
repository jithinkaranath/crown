# crown

project sample coding

## Task 1

- RequestParam to filter products based on availability status.
- Ensure that the filtering is optional and configurable for each request.
- Use Java Streams to filter the products based on availability.
- Ensure that if no availability filter is specified, all products are returned.
- Updated the API version to `/v1` to reflect the changes made in the filtering logic.
- Updated the Swagger documentation to reflect the new API version and functionality.

```
@ApiResponse(responseCode = "200", description = "Returns list of all products with availability filter", content = @Content(array = @ArraySchema(schema = @Schema(implementation = Product.class))))
    @GetMapping("/v1")
    public List<Product> listWithFilter(@RequestParam(value = "available", required = false) Boolean isAvailable) {
      return productService.getAll().stream()
                .filter(product -> isAvailable == null || product.isAvailable() == isAvailable)
                .collect(Collectors.toList());

    }

```

## Task 2

- Override equals and hashCode methods in the Product class to ensure proper comparison.
- Convert `List` to `Set` to eliminate duplicates, or use `distinct()` method in the stream processing.
- Updated the API version to `/v2` to reflect the changes made in the filtering logic.
- Updated the Swagger documentation to reflect the new API version and functionality.

```

Overrided equals and hashCode methods in Product class

```

```

@ApiResponse(responseCode = "200", description = "Returns list of all products with availability filter", content = @Content(array = @ArraySchema(schema = @Schema(implementation = Product.class))))
    @GetMapping("/v2")
    public List<Product> listWithFilterwithoutDuplicates(@RequestParam(value = "available", required = false) Boolean isAvailable) {
        return productService.getAll().stream()
                .filter(product -> isAvailable == null || product.isAvailable() == isAvailable)
                // .collect(Collectors.toSet())// can use Set to eliminate Duplicates
                .distinct() // can use for remove duplicates
                .collect(Collectors.toList());
    }

```

## Task 3

### Inventory Management Technical Suggestions

- Use Lombok to reduce boilerplate code, such as getters, setters, and constructors.
- use ResponseEntity for API responses to provide more control over the HTTP response, including status codes and headers.
- Implement Common Response Wrapper to standardize API responses across the application.
- Implement API versioning to manage changes in the API more effectively.
- Use tools like Spotless for code formatting, linting and Checkstyle for maintain code quality.
- Implement a health check endpoint using Spring Boot Actuator to monitor the application's health.
- Enhance logging by using SLF4J with Logback for better logging practices.
- Add unit tests for the new features to ensure functionality and reliability.
- Improve error handling to provide more meaningful error messages and responses.
