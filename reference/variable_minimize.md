# Remove nested columns for a compact variable overview

Remove nested columns for a compact variable overview

## Usage

``` r
variable_minimize(var_df)
```

## Arguments

- var_df:

  A tibble returned by
  [`get_variables()`](https://lchansson.github.io/pixieweb/reference/get_variables.md).

## Value

A tibble without `values` and `codelists` columns.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  get_variables(scb, "TAB638") |> variable_minimize()
}# }
#> # A tibble: 6 × 6
#>   code         text           n_values elimination time  table_id
#>   <chr>        <chr>             <int> <lgl>       <lgl> <chr>   
#> 1 Region       region              312 TRUE        FALSE TAB638  
#> 2 Civilstand   marital status        4 TRUE        FALSE TAB638  
#> 3 Alder        age                 102 TRUE        FALSE TAB638  
#> 4 Kon          sex                   2 TRUE        FALSE TAB638  
#> 5 ContentsCode observations          2 FALSE       FALSE TAB638  
#> 6 Tid          year                 57 FALSE       TRUE  TAB638  
```
