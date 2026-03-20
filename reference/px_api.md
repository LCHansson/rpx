# Connect to a PX-Web API

Creates a `<px_api>` connection object used by all other rpx functions.
You can pass a known alias (e.g. `"scb"`, `"ssb"`) or a full base URL.

## Usage

``` r
px_api(x, lang = NULL, version = "v2", verbose = FALSE)

# S3 method for class 'px_api'
print(x, ...)

# S3 method for class 'px_api'
format(x, ...)
```

## Arguments

- x:

  A `<px_api>` object.

- lang:

  Language code (e.g. `"sv"`, `"en"`). `NULL` uses the API default.

- version:

  API version: `"v2"` (default) or `"v1"`.

- verbose:

  Print connection details.

- ...:

  Ignored.

## Value

A `<px_api>` object.

## Examples

``` r
# \donttest{
if (px_available(px_api("scb"))) {
  scb <- px_api("scb", lang = "en")
  ssb <- px_api("ssb", lang = "no")
  custom <- px_api("https://my.statbank.example/api/v2/", lang = "en")
}# }
#> Warning: Could not connect to PX-Web API: Failed to perform HTTP request.
#> Caused by error in `curl::curl_fetch_memory()`:
#> ! Couldn't resolve host name [my.statbank.example]:
#> Could not resolve host: my.statbank.example
```
