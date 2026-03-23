# Prepare a data query with smart defaults

Bridges the gap between table/variable exploration and data fetching.
Fetches variable metadata, applies sensible defaults for variable
selections, and returns a query object that can be passed to
[`get_data()`](https://lchansson.github.io/pixieweb/reference/get_data.md).

## Usage

``` r
prepare_query(
  api,
  table_id,
  ...,
  .codelist = NULL,
  max_default_values = 22,
  maximize_selection = FALSE,
  verbose = FALSE
)

# S3 method for class 'px_query'
print(x, ...)
```

## Arguments

- api:

  A `<px_api>` object.

- table_id:

  A single table ID (character).

- ...:

  Ignored.

- .codelist:

  Named list of codelist overrides.

- max_default_values:

  Maximum number of values for a variable to receive a wildcard default.
  Defaults to `22` (covers e.g. Swedish län).

- maximize_selection:

  If `TRUE`, expand unspecified variables to include as many values as
  possible while staying under the API cell limit.

- verbose:

  Print request details.

- x:

  A `<px_query>` object.

## Value

A `<px_query>` object. Pass to
[`get_data()`](https://lchansson.github.io/pixieweb/reference/get_data.md)
via the `query` parameter.

## Details

Default selection strategy:

- **ContentsCode**: all values (`"*"`)

- **Time variable**: most recent 10 periods (`px_top(10)`)

- **Eliminable variables**: omitted (API aggregates automatically)

- **Small mandatory variables** (\<= `max_default_values` values): all
  (`"*"`)

- **Large mandatory variables**: first value only (`px_top(1)`)

When `maximize_selection = TRUE`, the function expands selections to use
as much of the API's cell limit as possible. Expansion order: smallest
eliminable variables first, then smallest mandatory, then time last.

The returned query object prints a human-readable summary showing what
was selected for each variable and why. Modify selections before passing
to
[`get_data()`](https://lchansson.github.io/pixieweb/reference/get_data.md)
by assigning to the `$selections` list.

## Examples

``` r
# \donttest{
scb <- px_api("scb", lang = "en")
if (px_available(scb)) {

  # Prepare with defaults
  q <- prepare_query(scb, "TAB638")
  q

  # Override specific variables, let defaults handle the rest
  q <- prepare_query(scb, "TAB638", Region = c("0180", "1480"))

  # Maximize data within API limits
  q <- prepare_query(scb, "TAB638", maximize_selection = TRUE)

  # Fetch data from a prepared query
  get_data(scb, query = q)
}# }
#> ── Query: TAB638 ──────────────────────────────────────────────────────────────── 
#>   Estimated cells: 20 / 150000 (0% of limit)
#> 
#>   Region = <eliminated>
#>     eliminated (312 values available)
#>   Civilstand = <eliminated>
#>     eliminated (4 values available)
#>   Alder = <eliminated>
#>     eliminated (102 values available)
#>   Kon = <eliminated>
#>     eliminated (2 values available)
#>   ContentsCode = "*"
#>     all 2 content variable(s)
#>   Tid = px_top(10)
#>     latest 10 of 57 periods
#> ── Query: TAB638 ──────────────────────────────────────────────────────────────── 
#>   Estimated cells: 40 / 150000 (0% of limit)
#> 
#>   Region = c("0180", "1480")
#>     user override
#>   Civilstand = <eliminated>
#>     eliminated (4 values available)
#>   Alder = <eliminated>
#>     eliminated (102 values available)
#>   Kon = <eliminated>
#>     eliminated (2 values available)
#>   ContentsCode = "*"
#>     all 2 content variable(s)
#>   Tid = px_top(10)
#>     latest 10 of 57 periods
#> ── Query: TAB638 ──────────────────────────────────────────────────────────────── 
#>   Estimated cells: 93024 / 150000 (62% of limit)
#> 
#>   Region = <eliminated>
#>     eliminated (312 values available)
#>   Civilstand = "*"
#>     all 4 values (expanded by maximize_selection)
#>   Alder = "*"
#>     all 102 values (expanded by maximize_selection)
#>   Kon = "*"
#>     all 2 values (expanded by maximize_selection)
#>   ContentsCode = "*"
#>     all 2 content variable(s)
#>   Tid = "*"
#>     all 57 values (expanded by maximize_selection)
#> # A tibble: 93,024 × 12
#>    table_id Civilstand Civilstand_text Alder Alder_text Kon   Kon_text
#>    <chr>    <chr>      <chr>           <chr> <chr>      <chr> <chr>   
#>  1 TAB638   OG         single          0     0 years    1     men     
#>  2 TAB638   OG         single          0     0 years    1     men     
#>  3 TAB638   OG         single          0     0 years    1     men     
#>  4 TAB638   OG         single          0     0 years    1     men     
#>  5 TAB638   OG         single          0     0 years    1     men     
#>  6 TAB638   OG         single          0     0 years    1     men     
#>  7 TAB638   OG         single          0     0 years    1     men     
#>  8 TAB638   OG         single          0     0 years    1     men     
#>  9 TAB638   OG         single          0     0 years    1     men     
#> 10 TAB638   OG         single          0     0 years    1     men     
#> # ℹ 93,014 more rows
#> # ℹ 5 more variables: ContentsCode <chr>, ContentsCode_text <chr>, Tid <chr>,
#> #   Tid_text <chr>, value <dbl>
```
