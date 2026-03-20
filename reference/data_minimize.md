# Remove monotonous columns from a data tibble

Remove monotonous columns from a data tibble

## Usage

``` r
data_minimize(data_df, remove_monotonous_data = TRUE)
```

## Arguments

- data_df:

  A tibble returned by
  [`get_data()`](https://lchansson.github.io/rpx/reference/get_data.md).

- remove_monotonous_data:

  Remove columns where all values are identical.

## Value

A tibble.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  d <- get_data(scb, "TAB638", Region = "0180", Tid = px_top(3))
  d |> data_minimize()
}# }
#> Warning: PX-Web API returned HTTP 400: {"type":"Parameter error","title":"Missing selection for mandantory variable","status":400}
#> NULL
```
