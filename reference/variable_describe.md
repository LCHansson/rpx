# Print human-readable variable summaries

Print human-readable variable summaries

## Usage

``` r
variable_describe(var_df, max_n = 10, format = "inline", heading_level = 2)
```

## Arguments

- var_df:

  A tibble returned by
  [`get_variables()`](https://lchansson.github.io/rpx/reference/get_variables.md).

- max_n:

  Maximum number of variables to describe.

- format:

  Output format: `"inline"` or `"md"`.

- heading_level:

  Heading level.

## Value

`var_df` invisibly (for piping).

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  get_variables(scb, "TAB638") |> variable_describe()
}# }
#> ── Region (region) ────────────────────────────────────────────────────────────── 
#>   Values: 312, optional (elimination) 
#>   First values: 00 Sweden, 01 Stockholm county, 0114 Upplands Väsby, 0115 Vallentuna, 0117 Österåker ... and 307 more 
#>   Codelists: agg_RegionA-region_2 A-regions, agg_RegionLA1998 Local labour markets 1998, agg_RegionLA2003_1 Local labour markets 2003 ... and 15 more 
#> 
#> ── Civilstand (marital status) ────────────────────────────────────────────────── 
#>   Values: 4, optional (elimination) 
#>   First values: OG single, G married, ÄNKL widowers/widows, SK divorced 
#> 
#> ── Alder (age) ────────────────────────────────────────────────────────────────── 
#>   Values: 102, optional (elimination) 
#>   First values: 0 0 years, 1 1 year, 2 2 years, 3 3 years, 4 4 years ... and 97 more 
#>   Codelists: agg_Ålder10årJ ´10-year intervals, agg_Ålder5år 5-year intervals, vs_Ålder1årA Age, 1 year age classes ... and 1 more 
#> 
#> ── Kon (sex) ──────────────────────────────────────────────────────────────────── 
#>   Values: 2, optional (elimination) 
#>   First values: 1 men, 2 women 
#> 
#> ── ContentsCode (observations) ────────────────────────────────────────────────── 
#>   Values: 2, mandatory 
#>   First values: BE0101N1 Population, BE0101N2 Population growth 
#> 
#> ── Tid (year) ─────────────────────────────────────────────────────────────────── 
#>   Values: 57, mandatory 
#>   Time variable: Yes
#>   First values: 1968 1968, 1969 1969, 1970 1970, 1971 1971, 1972 1972 ... and 52 more 
#> 
```
