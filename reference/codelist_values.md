# Extract values for a specific codelist

Extract values for a specific codelist

## Usage

``` r
codelist_values(cl_df, codelist_id)
```

## Arguments

- cl_df:

  A tibble returned by
  [`get_codelists()`](https://lchansson.github.io/rpx/reference/get_codelists.md).

- codelist_id:

  Codelist ID (character).

## Value

A tibble with columns `code` and `text`.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  cls <- get_codelists(scb, "TAB638", "Region")
  codelist_values(cls, cls$id[1])
}# }
#> # A tibble: 70 × 2
#>    code  text                          
#>    <chr> <chr>                         
#>  1 A-01  Stockholms/Södertälje A-region
#>  2 A-02  Norrtälje A-region            
#>  3 A-03  Enköpings A-region            
#>  4 A-04  Uppsala A-region              
#>  5 A-05  Nyköpings A-region            
#>  6 A-06  Katrineholms A-region         
#>  7 A-07  Eskilstuna A-region           
#>  8 A-08  Mjölby/Motala A-region        
#>  9 A-09  Linköpings A-region           
#> 10 A-10  Norrköpings A-region          
#> # ℹ 60 more rows
```
