# Load RDS File with Fast Parallel Decompression

Loads RDS files using
[`fastSave::readRDS.pigz`](https://rdrr.io/pkg/fastSave/man/readRDS.pigz.html)
when available for faster parallel decompression. Installs fastSave from
GitHub if not present. Falls back to base `readRDS` if fastSave is
unavailable or fails.

## Usage

``` r
load_rds_fast(file, install_if_missing = TRUE)
```

## Arguments

- file:

  Path to the RDS file.

- install_if_missing:

  If TRUE (default), attempts to install fastSave via
  `devtools::install_github('barkasn/fastSave')` when not found.

## Value

The R object loaded from the RDS file.

## Examples

``` r
if (FALSE) { # \dontrun{
obj <- load_rds_fast("path/to/object.rds")
} # }
```
