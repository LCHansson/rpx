# Get codelists for a variable in a table

Codelists provide alternative groupings of variable values (e.g.
municipalities grouped into counties).

## Usage

``` r
get_codelists(api, table_id, variable_code, verbose = FALSE)
```

## Arguments

- api:

  A `<px_api>` object.

- table_id:

  Table ID (character).

- variable_code:

  Variable code (character).

- verbose:

  Print request details.

## Value

A tibble with columns: `id`, `text`, `type`, `values`.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  get_codelists(scb, "TAB638", "Region")
}# }
#> # A tibble: 18 × 4
#>    id                           text                         type       values  
#>    <chr>                        <chr>                        <chr>      <list>  
#>  1 agg_RegionA-region_2         A-regions                    Aggregati… <tibble>
#>  2 agg_RegionLA1998             Local labour markets 1998    Aggregati… <tibble>
#>  3 agg_RegionLA2003_1           Local labour markets 2003    Aggregati… <tibble>
#>  4 agg_RegionLA2008             Local labour markets 2008    Aggregati… <tibble>
#>  5 agg_RegionLA2013             Local labour markets 2013    Aggregati… <tibble>
#>  6 agg_RegionLA2018             Local labour markets 2018    Aggregati… <tibble>
#>  7 agg_RegionStoromr-04_2       Metropolitan areas -2004     Aggregati… <tibble>
#>  8 agg_RegionStoromr05-_1       Metropolitan areas 2005-     Aggregati… <tibble>
#>  9 agg_RegionNUTS1_2008         NUTS 1 level 2008-           Aggregati… <tibble>
#> 10 agg_RegionNUTS2_2008         NUTS 2 level 2008-           Aggregati… <tibble>
#> 11 agg_RegionNUTS3_2008         NUTS 3 level 2008-           Aggregati… <tibble>
#> 12 agg_RegionKommungrupp2005-_1 Types of municipalities 2005 Aggregati… <tibble>
#> 13 agg_RegionKommungrupp2011-   Types of municipalities 2011 Aggregati… <tibble>
#> 14 agg_RegionKommungrupp2017-   Types of municipalities 2017 Aggregati… <tibble>
#> 15 agg_RegionKommungrupp2023-   Types of municipalities 2023 Aggregati… <tibble>
#> 16 vs_RegionKommun07            Municipalities               Valueset   <tibble>
#> 17 vs_RegionLän07               County                       Valueset   <tibble>
#> 18 vs_RegionRiket99             Sweden                       Valueset   <tibble>
```
