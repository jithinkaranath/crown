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
