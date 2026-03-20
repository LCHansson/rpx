# Print human-readable codelist summaries

Print human-readable codelist summaries

## Usage

``` r
codelist_describe(cl_df, max_n = 5, format = "inline", heading_level = 2)
```

## Arguments

- cl_df:

  A tibble returned by
  [`get_codelists()`](https://lchansson.github.io/rpx/reference/get_codelists.md).

- max_n:

  Maximum codelists to describe.

- format:

  Output format: `"inline"` or `"md"`.

- heading_level:

  Heading level.

## Value

`cl_df` invisibly (for piping).

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  get_codelists(scb, "TAB638", "Region") |> codelist_describe()
}# }
#> ── agg_RegionA-region_2: A-regions ────────────────────────────────────────────── 
#>   Type: Aggregation 
#>   Values: 70 items 
#>   First: A-01 Stockholms/Södertälje A-region, A-02 Norrtälje A-region, A-03 Enköpings A-region, A-04 Uppsala A-region, A-05 Nyköpings A-region ... and 65 more 
#> 
#> ── agg_RegionLA1998: Local labour markets 1998 ────────────────────────────────── 
#>   Type: Aggregation 
#>   Values: 100 items 
#>   First: 01001LA Stockholm LA, 04001LA Nyköping-Oxelösund LA, 04002LA Katrineholm LA, 04003LA Eskilstuna LA, 05001LA Linköping LA ... and 95 more 
#> 
#> ── agg_RegionLA2003_1: Local labour markets 2003 ──────────────────────────────── 
#>   Type: Aggregation 
#>   Values: 87 items 
#>   First: LA0301 Stockholm LA, LA0302 Nyköping-Oxelösund LA, LA0303 Eskilstuna LA, LA0304 Linköping LA, LA0305 Norrköping LA ... and 82 more 
#> 
#> ── agg_RegionLA2008: Local labour markets 2008 ────────────────────────────────── 
#>   Type: Aggregation 
#>   Values: 75 items 
#>   First: LA0801 Stockholm-Solna, LA0802 Nyköping-Oxelösund, LA0803 Eskilstuna, LA0804 Linköping, LA0805 Norrköping ... and 70 more 
#> 
#> ── agg_RegionLA2013: Local labour markets 2013 ────────────────────────────────── 
#>   Type: Aggregation 
#>   Values: 73 items 
#>   First: LA1301 Stockholm-Solna, LA1302 Nyköping-Oxelösund, LA1303 Eskilstuna, LA1304 Linköping, LA1305 Norrköping ... and 68 more 
#> 
```
