# Clear rpx cache files

Removes cached API responses stored in the default or specified
location. Can selectively clear by entity type and/or API.

## Usage

``` r
rpx_clear_cache(entity = NULL, api = NULL, cache_location = rpx_cache_dir())
```

## Arguments

- entity:

  Character entity to clear (e.g. `"tables"`, `"enriched"`), or `NULL`
  (default) to clear all rpx cache files.

- api:

  A `<px_api>` object. If provided, only cache files for that API's
  alias are cleared. `NULL` (default) clears all APIs.

- cache_location:

  Directory to clear. Defaults to
  [`rpx_cache_dir()`](https://lchansson.github.io/rpx/reference/rpx_cache_dir.md).

## Value

`invisible(NULL)`

## Examples

``` r
# \donttest{
scb <- px_api("scb")
if (px_available(scb)) {
  rpx_clear_cache()
  rpx_clear_cache(entity = "tables")
  rpx_clear_cache(api = scb)
  rpx_clear_cache(entity = "enriched", api = scb)
}# }
#> No rpx cache files found.
#> No rpx cache files found.
#> No rpx cache files found.
#> No rpx cache files found.
```
