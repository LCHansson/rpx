# Client-side search on a table tibble

Filter an already-fetched table tibble by regex. Complements
`get_tables(query = ...)` which does server-side search. Use this for
further refinement on cached results.

## Usage

``` r
table_search(table_df, query, column = NULL)
```

## Arguments

- table_df:

  A tibble returned by
  [`get_tables()`](https://lchansson.github.io/pixieweb/reference/get_tables.md).

- query:

  Character vector of search terms (combined with OR).

- column:

  Column names to search. `NULL` searches all character columns.

## Value

A filtered tibble.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  tables <- get_tables(scb, query = "population")

  # Further filter by regex
  tables |> table_search("municipality")
}# }
#> # A tibble: 1 × 13
#>   id     title   description category updated first_period last_period time_unit
#>   <chr>  <chr>   <chr>       <chr>    <chr>   <chr>        <chr>       <chr>    
#> 1 TAB683 Popula… ""          public   2020-1… 2018         2018        Annual   
#> # ℹ 5 more variables: variables <list>, subject_code <chr>, subject_path <chr>,
#> #   source <chr>, discontinued <lgl>
```
