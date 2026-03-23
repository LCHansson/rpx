# Save a query on the server

Persists a set of variable selections server-side so the query can be
shared or re-used later.

## Usage

``` r
save_query(api, table_id, ..., .codelist = NULL, verbose = FALSE)
```

## Arguments

- api:

  A `<px_api>` object.

- table_id:

  Table ID (character).

- ...:

  Variable selections (same as
  [`get_data()`](https://lchansson.github.io/pixieweb/reference/get_data.md)).

- .codelist:

  Named list of codelist overrides.

- verbose:

  Print request details.

## Value

A character string: the saved query ID.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  query_id <- save_query(scb, "TAB638", Region = "0180", Tid = px_top(5))
}# }
#> Warning: PX-Web API returned HTTP 400: {"type":"Parameter error","title":"Missing selection for mandantory variable","status":400}
```
