# Extract table IDs from a table tibble

Extract table IDs from a table tibble

## Usage

``` r
table_extract_ids(table_df)
```

## Arguments

- table_df:

  A tibble returned by
  [`get_tables()`](https://lchansson.github.io/pixieweb/reference/get_tables.md).

## Value

A character vector of table IDs.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {
  get_tables(scb, query = "population") |> table_extract_ids()
}# }
#>   [1] "TAB1743" "TAB934"  "TAB4552" "TAB6473" "TAB1625" "TAB6481" "TAB5169"
#>   [8] "TAB4562" "TAB938"  "TAB4951" "TAB4560" "TAB4704" "TAB3732" "TAB4422"
#>  [15] "TAB3791" "TAB3731" "TAB3733" "TAB3730" "TAB4365" "TAB5328" "TAB4161"
#>  [22] "TAB4481" "TAB5609" "TAB5947" "TAB646"  "TAB5329" "TAB2900" "TAB4228"
#>  [29] "TAB706"  "TAB703"  "TAB1615" "TAB5326" "TAB4420" "TAB5589" "TAB4211"
#>  [36] "TAB4869" "TAB4235" "TAB3455" "TAB3454" "TAB3453" "TAB5591" "TAB3182"
#>  [43] "TAB3490" "TAB3488" "TAB6667" "TAB726"  "TAB5958" "TAB3181" "TAB628" 
#>  [50] "TAB694"  "TAB732"  "TAB5965" "TAB5953" "TAB3000" "TAB645"  "TAB644" 
#>  [57] "TAB641"  "TAB6752" "TAB5946" "TAB643"  "TAB5381" "TAB2895" "TAB4226"
#>  [64] "TAB716"  "TAB713"  "TAB1612" "TAB5337" "TAB340"  "TAB5721" "TAB5890"
#>  [71] "TAB6642" "TAB6646" "TAB5611" "TAB6514" "TAB6300" "TAB5999" "TAB695" 
#>  [78] "TAB648"  "TAB6744" "TAB1616" "TAB638"  "TAB5777" "TAB730"  "TAB6063"
#>  [85] "TAB5557" "TAB6387" "TAB6516" "TAB4644" "TAB6471" "TAB2819" "TAB6759"
#>  [92] "TAB6512" "TAB6528" "TAB6529" "TAB709"  "TAB683"  "TAB1145" "TAB339" 
#>  [99] "TAB6069" "TAB3869"
```
