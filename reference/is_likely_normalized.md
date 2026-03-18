# Check if expression matrix is likely already normalized (e.g. TISCH2, log-norm)

Used to avoid double-normalization when data is pre-normalized.
Heuristic: samples values and returns TRUE if most are non-integer or
range suggests log-scale (e.g. max moderate and not raw counts).

## Usage

``` r
is_likely_normalized(x, sample_cap = 5000L)
```

## Arguments

- x:

  Matrix or Matrix (genes x cells).

- sample_cap:

  Max number of values to sample (default 5000).

## Value

TRUE if data is likely already normalized; FALSE if likely raw counts.
