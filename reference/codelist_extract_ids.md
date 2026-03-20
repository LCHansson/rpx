# Extract codelist IDs

Extract codelist IDs

## Usage

``` r
codelist_extract_ids(cl_df)
```

## Arguments

- cl_df:

  A tibble returned by
  [`get_codelists()`](https://lchansson.github.io/rpx/reference/get_codelists.md).

## Value

A character vector of codelist IDs.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  get_codelists(scb, "TAB638", "Region") |> codelist_extract_ids()
}# }
#>  [1] "agg_RegionA-region_2"         "agg_RegionLA1998"            
#>  [3] "agg_RegionLA2003_1"           "agg_RegionLA2008"            
#>  [5] "agg_RegionLA2013"             "agg_RegionLA2018"            
#>  [7] "agg_RegionStoromr-04_2"       "agg_RegionStoromr05-_1"      
#>  [9] "agg_RegionNUTS1_2008"         "agg_RegionNUTS2_2008"        
#> [11] "agg_RegionNUTS3_2008"         "agg_RegionKommungrupp2005-_1"
#> [13] "agg_RegionKommungrupp2011-"   "agg_RegionKommungrupp2017-"  
#> [15] "agg_RegionKommungrupp2023-"   "vs_RegionKommun07"           
#> [17] "vs_RegionLän07"               "vs_RegionRiket99"            
```
