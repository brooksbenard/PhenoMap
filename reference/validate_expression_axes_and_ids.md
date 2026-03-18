# Validate expression matrix axes and gene ID format

Ensures genes are rows and samples/cells/spots are columns (heuristic:
orders of magnitude more genes than samples). If the matrix appears
transposed, it is transposed and a message is printed. Also checks for
ENSG-style rownames and warns the user to convert to HUGO symbols.

## Usage

``` r
validate_expression_axes_and_ids(mat, verbose = TRUE)
```

## Arguments

- mat:

  Matrix (or matrix-coercible object) with rownames and colnames.

- verbose:

  If TRUE, print a message when transposing.

## Value

The matrix, possibly transposed; rownames must be gene IDs, colnames
sample IDs.
