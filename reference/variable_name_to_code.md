# Convert variable names to codes

Convert variable names to codes

## Usage

``` r
variable_name_to_code(var_df, name)
```

## Arguments

- var_df:

  A tibble returned by
  [`get_variables()`](https://lchansson.github.io/pixieweb/reference/get_variables.md).

- name:

  Character vector of human-readable variable names.

## Value

A named character vector: names are the input names, values are codes.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  vars <- get_variables(scb, "TAB638")
  variable_name_to_code(vars, "Region")
}# }
#>   Region 
#> "Region" 
```
