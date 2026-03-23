# Get the persistent pixieweb cache directory

Returns the path to the user-level cache directory for pixieweb,
creating it if it does not exist. Uses
[`tools::R_user_dir()`](https://rdrr.io/r/tools/userdir.html) so the
cache survives across R sessions.

## Usage

``` r
pixieweb_cache_dir()
```

## Value

A single character string (directory path).

## Examples

``` r
pixieweb_cache_dir()
#> [1] "/home/runner/.cache/R/pixieweb"
```
