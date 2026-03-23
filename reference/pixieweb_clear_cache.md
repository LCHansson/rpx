# Clear pixieweb cache files

Removes cached API responses stored in the default or specified
location. Can selectively clear by entity type and/or API.

## Usage

``` r
pixieweb_clear_cache(
  entity = NULL,
  api = NULL,
  cache_location = pixieweb_cache_dir()
)
```

## Arguments

- entity:

  Character entity to clear (e.g. `"tables"`, `"enriched"`), or `NULL`
  (default) to clear all pixieweb cache files.

- api:

  A `<px_api>` object. If provided, only cache files for that API's
  alias are cleared. `NULL` (default) clears all APIs.

- cache_location:

  Directory to clear. Defaults to
  [`pixieweb_cache_dir()`](https://lchansson.github.io/pixieweb/reference/pixieweb_cache_dir.md).

## Value

`invisible(NULL)`

## Examples

``` r
# \donttest{
scb <- px_api("scb")
if (px_available(scb)) {
  pixieweb_clear_cache()
  pixieweb_clear_cache(entity = "tables")
  pixieweb_clear_cache(api = scb)
  pixieweb_clear_cache(entity = "enriched", api = scb)
}# }
#> No pixieweb cache files found.
#> No pixieweb cache files found.
#> No pixieweb cache files found.
#> No pixieweb cache files found.
```
