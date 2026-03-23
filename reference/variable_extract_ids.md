# Extract variable codes from a variable tibble

Extract variable codes from a variable tibble

## Usage

``` r
variable_extract_ids(var_df)
```

## Arguments

- var_df:

  A tibble returned by
  [`get_variables()`](https://lchansson.github.io/pixieweb/reference/get_variables.md).

## Value

A character vector of variable codes.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  get_variables(scb, "TAB638") |> variable_extract_ids()
}# }
#> [1] "Region"       "Civilstand"   "Alder"        "Kon"          "ContentsCode"
#> [6] "Tid"         
```
