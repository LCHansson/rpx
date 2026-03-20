# Get the persistent rpx cache directory

Returns the path to the user-level cache directory for rpx, creating it
if it does not exist. Uses
[`tools::R_user_dir()`](https://rdrr.io/r/tools/userdir.html) so the
cache survives across R sessions.

## Usage

``` r
rpx_cache_dir()
```

## Value

A single character string (directory path).

## Examples

``` r
rpx_cache_dir()
#> [1] "/home/runner/.cache/R/rpx"
```
