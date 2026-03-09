# Derive Reference Z-Scores from Bulk Expression and Phenotype

When you have bulk expression (samples × genes) and a phenotype (binary,
continuous, or survival), this function computes gene-level association
z-scores that can be used as a custom reference in
[`PhenoMap`](https://brooksbenard.github.io/PhenoMapR/reference/PhenoMap.md).

## Usage

``` r
derive_reference_from_bulk(
  bulk_expression,
  phenotype,
  sample_id_column = NULL,
  phenotype_column = NULL,
  phenotype_type = c("auto", "survival", "binary", "continuous"),
  survival_time = NULL,
  survival_event = NULL,
  gene_axis = NULL,
  normalize = TRUE,
  hugo_species = c("human", "mouse"),
  verbose = TRUE
)
```

## Arguments

- bulk_expression:

  Matrix or data.frame. Bulk expression with **samples as rows** and
  **genes as columns**. Can also be genes × samples; the function will
  detect and transpose so that rows = samples.

- phenotype:

  Data.frame with sample identifiers and phenotype column(s). Must align
  with `bulk_expression` by sample ID (see `sample_id_column`).

- sample_id_column:

  Character. Column name in `phenotype` that matches rownames (or
  colnames if transposed) of `bulk_expression`. If `NULL`, the first
  column of `phenotype` is used.

- phenotype_column:

  Character. Column name in `phenotype` for the outcome. For
  `phenotype_type = "survival"` this is ignored; use `survival_time` and
  `survival_event` instead.

- phenotype_type:

  One of `"auto"`, `"survival"`, `"binary"`, `"continuous"`. If
  `"auto"`, inferred from the phenotype column (numeric with \>2 unique
  → continuous; 2 unique → binary; or use survival if `survival_time`
  and `survival_event` are provided).

- survival_time:

  Character. Column name in `phenotype` for time-to-event (e.g. overall
  survival time). Required when `phenotype_type = "survival"`.

- survival_event:

  Character. Column name in `phenotype` for event indicator (0/1 or
  FALSE/TRUE). Required when `phenotype_type = "survival"`.

- gene_axis:

  Character. Either `"rows"` (genes are rows) or `"cols"` (genes are
  columns). If `NULL`, guessed by dimensions (if nrow \> ncol, assume
  samples × genes).

- normalize:

  Logical. If `TRUE`, run normalization when expression looks like
  counts (default `TRUE`). Set `FALSE` to skip.

- hugo_species:

  Character. Species for HUGO symbol cleaning: `"human"` or `"mouse"`
  (default `"human"`).

- verbose:

  Logical. Print progress messages (default `TRUE`).

## Value

A data.frame with genes as rownames and a single column of
phenotype-association z-scores, suitable for `reference` in
[`PhenoMap`](https://brooksbenard.github.io/PhenoMapR/reference/PhenoMap.md).

## Details

Steps: (1) clean gene names to approved HUGO symbols, (2) check if
expression is already normalized/scaled and normalize if needed, (3)
compute phenotype association z-scores per gene (Cox for survival,
logistic regression for binary, correlation for continuous).

## Examples

``` r
if (FALSE) { # \dontrun{
# Simulated bulk: 50 samples × 100 genes
set.seed(1)
bulk <- matrix(rnorm(50 * 100), 50, 100,
  dimnames = list(paste0("S", 1:50), paste0("G", 1:100)))
pheno <- data.frame(
  sample_id = paste0("S", 1:50),
  response = sample(c("R", "NR"), 50, replace = TRUE))

ref <- derive_reference_from_bulk(
  bulk_expression = bulk,
  phenotype = pheno,
  sample_id_column = "sample_id",
  phenotype_column = "response",
  phenotype_type = "binary")

# Use in scoring
scores <- PhenoMap(expression = my_single_cell_data, reference = ref)
} # }
```
