# Compute Score Vectors

Compute the weighted sum of expression with the reference meta-z vector:
score(cell) = sum over genes of `expression[gene, cell] * meta_z[gene]`.
Implemented via cross product for efficiency:
`crossprod(meta_z, expression)` yields one value per cell. Higher score
= worse prognosis (adverse).

## Usage

``` r
compute_scores(
  expression_data,
  prognostic_scores,
  pseudobulk = FALSE,
  verbose = TRUE
)
```
