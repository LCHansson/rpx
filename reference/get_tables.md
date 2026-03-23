# Get tables from a PX-Web API

Search for and list statistical tables available on a PX-Web instance.

## Usage

``` r
get_tables(
  api,
  query = NULL,
  id = NULL,
  updated_since = NULL,
  max_results = NULL,
  .timeout = 15,
  cache = FALSE,
  cache_location = pixieweb_cache_dir,
  verbose = FALSE
)
```

## Arguments

- api:

  A `<px_api>` object.

- query:

  Free-text search string (sent to API as server-side search).

- id:

  Character vector of specific table IDs to retrieve.

- updated_since:

  Only return tables updated in the last N days (integer).

- max_results:

  Maximum number of tables to return.

- .timeout:

  Maximum seconds to spend on v1 hierarchy tree walks (default 15). Only
  relevant when a v1 API lacks a `?query=` search endpoint and must fall
  back to walking the folder tree. Increase for exhaustive searches on
  large APIs. Has no effect on v2 APIs (which have native search).

- cache:

  Logical, cache results locally.

- cache_location:

  Cache directory. Defaults to
  [`pixieweb_cache_dir()`](https://lchansson.github.io/pixieweb/reference/pixieweb_cache_dir.md).

- verbose:

  Print request details.

## Value

A tibble with columns: `id`, `title`, `description`, `category`,
`updated`, `first_period`, `last_period`, `time_unit`, `variables`,
`subject_code`, `subject_path`, `source`, `discontinued`.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {

  # Server-side search
  get_tables(scb, query = "population")

  # Fetch specific tables by ID
  get_tables(scb, id = c("TAB638", "TAB1278"))

  # Tables updated in the last 30 days
  get_tables(scb, updated_since = 30)
}# }
#> # A tibble: 100 × 13
#>    id      title description category updated first_period last_period time_unit
#>    <chr>   <chr> <chr>       <chr>    <chr>   <chr>        <chr>       <chr>    
#>  1 TAB1391 Corp… ""          public   2026-0… 1998K2       2025K4      Quarterly
#>  2 TAB6726 Ente… ""          public   2026-0… 2025         2025        Annual   
#>  3 TAB1872 Indu… ""          public   2026-0… 2000M01      2026M01     Monthly  
#>  4 TAB1411 Corp… ""          public   2026-0… 1997K1       2025K4      Quarterly
#>  5 TAB1710 Orde… ""          public   2026-0… 2000M01      2026M01     Monthly  
#>  6 TAB1693 Turn… ""          public   2026-0… 2000M01      2026M01     Monthly  
#>  7 TAB4894 Prod… ""          public   2026-0… 2010M01      2026M01     Monthly  
#>  8 TAB4810 Prod… ""          public   2026-0… 2010K1       2025K4      Quarterly
#>  9 TAB6343 Priv… ""          public   2026-0… 2022K1       2025K4      Quarterly
#> 10 TAB6587 Priv… ""          public   2026-0… 2022K1       2025K4      Quarterly
#> # ℹ 90 more rows
#> # ℹ 5 more variables: variables <list>, subject_code <chr>, subject_path <chr>,
#> #   source <chr>, discontinued <lgl>
```
