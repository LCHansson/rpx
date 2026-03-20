# Extract comments from data

Extract comments from data

## Usage

``` r
data_comments(data_df)
```

## Arguments

- data_df:

  A tibble returned by
  [`get_data()`](https://lchansson.github.io/rpx/reference/get_data.md)
  with `.comments = TRUE`.

## Value

A tibble with columns `variable`, `value`, `comment`, or `NULL`.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  d <- get_data(scb, "TAB638", Region = "0180", Tid = px_top(3), .comments = TRUE)
  data_comments(d)
}# }
#> Warning: PX-Web API returned HTTP 400: {"type":"Parameter error","title":"Missing selection for mandantory variable","status":400}
#> NULL
```
