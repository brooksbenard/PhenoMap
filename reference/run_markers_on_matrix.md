# Run marker detection on a matrix (no Seurat). Uses presto::wilcoxauc if available, else base Wilcoxon.

Run marker detection on a matrix (no Seurat). Uses presto::wilcoxauc if
available, else base Wilcoxon.

## Usage

``` r
run_markers_on_matrix(
  mat,
  group_vec,
  min.pct = 0.1,
  logfc.threshold = 0.25,
  pval_threshold = 0.05,
  max_cells_per_ident = 5000L,
  verbose = TRUE
)
```
