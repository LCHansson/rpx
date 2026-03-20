# Check if a PX-Web API is reachable

Check if a PX-Web API is reachable

## Usage

``` r
px_available(api)
```

## Arguments

- api:

  A `<px_api>` object.

## Value

Logical: `TRUE` if the API responds, `FALSE` otherwise.

## Examples

``` r
# \donttest{
scb <- px_api("scb")
if (px_available(scb)) {
  px_available(scb)
}# }
#> [1] TRUE
```
