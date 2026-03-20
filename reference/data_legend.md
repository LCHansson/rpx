# Generate a plot legend from variable metadata

Generate a plot legend from variable metadata

## Usage

``` r
data_legend(data_df, var_df)
```

## Arguments

- data_df:

  A tibble returned by
  [`get_data()`](https://lchansson.github.io/rpx/reference/get_data.md).

- var_df:

  A tibble returned by
  [`get_variables()`](https://lchansson.github.io/rpx/reference/get_variables.md).

## Value

A character string suitable for plot captions.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  vars <- get_variables(scb, "TAB638")
  d <- get_data(scb, "TAB638", Region = "0180", Tid = px_top(3))
  data_legend(d, vars)
}# }
#> Warning: PX-Web API returned HTTP 400: {"type":"Parameter error","title":"Missing selection for mandantory variable","status":400}
#> [1] "region (Region) | marital status (Civilstand) | age (Alder) | sex (Kon) | observations (ContentsCode) | year (Tid)\n"
```
