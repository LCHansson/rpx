# Extract values for a specific variable

Extract values for a specific variable

## Usage

``` r
variable_values(var_df, variable_code)
```

## Arguments

- var_df:

  A tibble returned by
  [`get_variables()`](https://lchansson.github.io/pixieweb/reference/get_variables.md).

- variable_code:

  Variable code (character).

## Value

A tibble with columns `code` and `text`.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  vars <- get_variables(scb, "TAB638")
  vars |> variable_values("Kon")
}# }
#> # A tibble: 2 × 2
#>   code  text 
#>   <chr> <chr>
#> 1 1     men  
#> 2 2     women
```
