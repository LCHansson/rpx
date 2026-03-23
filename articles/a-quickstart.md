# Quick start guide to pixieweb

pixieweb makes it easy to download open statistical data from PX-Web
APIs — the platform used by Statistics Sweden (SCB), Statistics Norway
(SSB), Statistics Finland, and many others. This vignette walks you from
zero to a tidy tibble in five steps.

## Step 1: Connect to an API

``` r
library(pixieweb)

scb <- px_api("scb", lang = "en")
scb
```

[`px_api()`](https://lchansson.github.io/pixieweb/reference/px_api.md)
accepts a short alias (`"scb"`, `"ssb"`, `"statfi"`) or a full URL. Use
[`px_api_catalogue()`](https://lchansson.github.io/pixieweb/reference/px_api_catalogue.md)
to list known instances.

## Step 2: Find a table

PX-Web organises data into **tables**. Each table holds a data cube with
one or more dimensions (called **variables**). Use
[`get_tables()`](https://lchansson.github.io/pixieweb/reference/get_tables.md)
to search:

``` r
tables <- get_tables(scb, query = "population")
tables
```

The result is a tibble. You can narrow it further on the client side
with
[`table_search()`](https://lchansson.github.io/pixieweb/reference/table_search.md),
and inspect tables with
[`table_describe()`](https://lchansson.github.io/pixieweb/reference/table_describe.md):

``` r
tables |>
  table_search("municipal") |>
  table_describe(max_n = 3, format = "md")
```

[`table_describe()`](https://lchansson.github.io/pixieweb/reference/table_describe.md)
now shows the subject path, time period range, and data source alongside
the title — making it much easier to pick the right table.

## Step 3: Explore variables

Once you have a table ID, inspect what variables (dimensions) it has:

``` r
vars <- get_variables(scb, "TAB683")
vars |> variable_describe()
```

Each variable has a set of available **values** (codes). Look at a
specific variable’s values:

``` r
vars |> variable_values("Region")
```

## Step 4: Fetch data

Now you know which variables the table has and what values are
available. Pass your selections to
[`get_data()`](https://lchansson.github.io/pixieweb/reference/get_data.md):

- **ContentsCode** tells the API *what* to measure (population, deaths,
  etc.). `"*"` means “all measures in this table”.
- Variables you **omit** are *eliminated* — the API returns a
  pre-computed aggregate (e.g., omitting `Kon` gives totals for both
  sexes). Not all variables allow this; see
  [`vignette("introduction-to-pixieweb")`](https://lchansson.github.io/pixieweb/articles/introduction-to-pixieweb.md)
  for mandatory vs eliminable.

``` r
pop <- get_data(scb, "TAB638",
  Region = c("0180", "1480"),
  ContentsCode = "*",
  Tid = px_top(5)
)
pop
```

Selection helpers like
[`px_top()`](https://lchansson.github.io/pixieweb/reference/px_selections.md),
[`px_from()`](https://lchansson.github.io/pixieweb/reference/px_selections.md),
and
[`px_range()`](https://lchansson.github.io/pixieweb/reference/px_selections.md)
let you select values without knowing exact codes. Use them when you
want “the latest N periods” or “everything from 2020 onward” rather than
typing out specific year codes.

### Optional shortcut: `prepare_query()`

You can skip this section if you prefer the direct approach above.
[`prepare_query()`](https://lchansson.github.io/pixieweb/reference/prepare_query.md)
inspects the table and fills in sensible defaults — handy when you don’t
want to specify every variable:

``` r
q <- prepare_query(scb, "TAB638", Region = c("0180", "1480"))
```

It prints a summary of what was chosen and why. When you’re happy, pass
the query to
[`get_data()`](https://lchansson.github.io/pixieweb/reference/get_data.md):

``` r
pop <- get_data(scb, query = q)
```

Set `maximize_selection = TRUE` to automatically include as many
variables as the API’s cell limit allows:

``` r
q <- prepare_query(scb, "TAB638",
  Region = c("0180"),
  maximize_selection = TRUE
)
```

## Step 5: Work with the result

The result is a standard tibble. Use your favourite tidyverse tools:

``` r
library(ggplot2)

pop |>
  ggplot(aes(x = Tid, y = value, colour = Region_text)) +
  # One line per region
  geom_line(aes(group = Region_text)) +
  # Separate panel for each measure (Population, Deaths, etc.)
  facet_wrap(~ ContentsCode_text, scales = "free_y") +
  # Rotate x-axis labels to avoid overlap
  theme(axis.text.x = element_text(angle = 45, hjust = 1, vjust = 1)) +
  labs(
    title = "Population over time",
    caption = px_cite(pop)  # Auto-generated data citation
  )
```

Notice the `_text` suffix:
[`get_data()`](https://lchansson.github.io/pixieweb/reference/get_data.md)
returns both raw code columns (`Region = "0180"`) and human-readable
label columns (`Region_text = "Stockholm"`). Use `_text` columns for
display and plotting; use the raw codes for filtering and joining.

Other useful helpers:

- [`data_minimize()`](https://lchansson.github.io/pixieweb/reference/data_minimize.md)
  — remove columns where all values are identical
- [`data_legend()`](https://lchansson.github.io/pixieweb/reference/data_legend.md)
  — generate a caption string from variable metadata
- [`px_cite()`](https://lchansson.github.io/pixieweb/reference/px_cite.md)
  — create a citation for the downloaded data

## Next steps

- **Concepts & advanced features** —
  [`vignette("introduction-to-pixieweb")`](https://lchansson.github.io/pixieweb/articles/introduction-to-pixieweb.md)
  covers the data model, codelists, saved queries, and query
  composition.
- **Multiple countries** —
  [`vignette("multi-api")`](https://lchansson.github.io/pixieweb/articles/multi-api.md)
  shows how to compare data across national statistics agencies.
- **ggplot2 reference** — <https://ggplot2-book.org/> for more on
  visualisation.
