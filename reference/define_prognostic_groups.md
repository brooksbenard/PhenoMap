# Define Prognostic Groups (Top and Bottom Percentile)

For each score column (dataset), labels cells as adverse (top
percentile, highest scores), favorable (bottom percentile, lowest
scores), or middle.

## Usage

``` r
define_prognostic_groups(scores, percentile = 0.05, score_columns = NULL)
```

## Arguments

- scores:

  Data.frame of prognostic scores from `PhenoMap`. Rows = cells/samples,
  columns = score variables (e.g. weighted_sum_score_precog_BRCA).

- percentile:

  Fraction of cells in each tail (default 0.05 for top and bottom 5%).

- score_columns:

  Character vector of score column names to use. If NULL, all numeric
  columns in `scores` are used.

## Value

A data.frame with:

- `cell_id`: same as row names of `scores`

- For each score column: a `prognostic_group_<name>` column with values
  `"adverse"` (top percentile), `"favorable"` (bottom percentile), or
  `"middle"`

## Examples

``` r
if (FALSE) { # \dontrun{
scores <- PhenoMap(seurat_obj, reference = "precog", cancer_type = "BRCA")
groups <- define_prognostic_groups(scores, percentile = 0.05)
table(groups$prognostic_group_weighted_sum_score_precog_BRCA)
} # }
```
