# Client-side search on a variable tibble

Searches across variable codes, texts, and optionally nested value
texts.

## Usage

``` r
variable_search(var_df, query, column = NULL)
```

## Arguments

- var_df:

  A tibble returned by
  [`get_variables()`](https://lchansson.github.io/rpx/reference/get_variables.md).

- query:

  Character vector of search terms (combined with OR).

- column:

  Column names to search. `NULL` searches `code` and `text`.

## Value

A filtered tibble.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  vars <- get_variables(scb, "TAB638")
  vars |> variable_search("region")
}# }
#> # A tibble: 1 × 8
#>   code   text   n_values elimination time  values             codelists table_id
#>   <chr>  <chr>     <int> <lgl>       <lgl> <list>             <list>    <chr>   
#> 1 Region region      312 TRUE        FALSE <tibble [312 × 2]> <tibble>  TAB638  
```
